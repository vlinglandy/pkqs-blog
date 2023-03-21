---
title: 'vue源码初探'
date: 2023-01-19 10:06:51
tags: 
    - 笔记
    - 基础
categories: 前端
---

## vue创建与运行流程

1. 每个vue文件都会编译成render函数，放在自身对象上，子组件会放在components对象中

   ```json
   {
       "name": "App",
       "components": {
           "HelloWorld": {
               "name": "HelloWorld",
               "__hmrId": "/src/components/HelloWorld.vue",
               "__file": "C:\\Personal\\Desktop\\study\\interview\\vue\\exercse1\\src\\components\\HelloWorld.vue"
           }
       },
       "__hmrId": "/src/App.vue",
       "__file": "C:\\Personal\\Desktop\\study\\interview\\vue\\exercse1\\src\\App.vue"
   }
   ```
2. 创建app实例时传入上述对象，首先init初始化好工具函数，之后将组件实例放到component中

## 从mini-vue看源码怎么实现的vue

**源码运行流程以及ref的创建**

1. 首先引入打包好的文件
2. 打包文件中调用了将template方法传入一个将template转换成ast语法树的函数，并调用运行时dom返回render函数

   ```js
   function compileToFunction(template, options = {}) {
     const { code } = baseCompile(template, options);

     // 调用 compile 得到的代码在给封装到函数内，
     // 这里会依赖 runtimeDom 的一些函数，所以在这里通过参数的形式注入进去
     const render = new Function("Vue", code)(runtimeDom);

     return render;
   }
   ```
3. 并且将该函数保存到compile中
4. 引入好打包文件之后引入项目组件app.js，这里app.js中每个组件已经转换为对象的形式，包含名称，render函数，和setup函数
5. 我们看一下这个创建响应式count数据的流程

   ```js
   const count = ref(0);
   ```

   1. 调用createRef方法传入value0
   2. 调用RefImpl的接口，传入value返回一个ref对象

      1. refimpl对象包含rawvalue，value，dep和__v_isRef为true的变量
      2. 首先将传入的value变量为rawvalue变量赋值
      3. 用convert函数转换该变量，如果该变量是一个对象就调用reactive函数，否则直接返回变量到value中
      4. 调用createDep方法给dep变量赋值，传入空对象，该函数返回一个new Set的集合对象
      5. 创建完refImpl对象了，将该变量返回给count，结束
   3. RefImpl中提供了get value和setvalue的方法

      1. get val中有`trackRefValue`函数，该函数接受前面传过来的this
      2. 如果shouldTrack并且activeeffect被定义则调用 ，trackeffects，并传入之前的this.dep的集合变量
      3. 该函数会将`activeEffect`添加到dep集合中
   4. setvalue的流程

      1. 该函数接受一个新值，如果该值和自己的ths.rawvalue不一样的话就调用convert方法传入新值并赋值给value，同时直接将新值赋值geinewvalue
      2. 之后调用`triggerRefValue`方法，传入该变量的this，该函数会将this.dep变量传给`triggerEffects`的函数，`triggerEffects`会遍历传入的dep集合，如果这个集合中含有`scheduler`属性就调用该迭代变量的scheduler函数中，否则就调用run函数
         ```js
         function triggerEffects(dep) {
             for (const effect of dep) {
                 if (effect.scheduler) {
                     effect.scheduler();
                 }
                 else {
                     effect.run();
                 }
             }
         }
         ```
   5. ref对象创建完毕，接下来我们可以用count.value获取到该值了，同时该值的getter与setter已经被我们截获，每次调用set值之后就会去dep中调用相应的订阅函数
   6. 总体来讲就是我们创建一个count变量，为这个变量设置get和set方法，每次set之后我们还要记得给依赖该函数的变量进行重新计算赋值，dep就是谁依赖我了，谁用到我了，而不是我依赖谁了，谁用到我了，我修改之后要跟他说一声，该说的我都放到dep集合中了，每次set之后我都通知dep集合中的每一个对象，让他尽快改，相当于也调用他的set方法
6. 将app中的组件返回，最终的结构是

   ```js
   {
     name: "App",
     setup() {},

     render() {
       return h("div", { tId: 1 }, [h("p", {}, "主页"), h(HelloWorld)]);
     },
   };
   ```
7. h函数会返回虚拟dom，如果传入的是对象则调用render方法，放到children中，否则就会根据tag，props，children创建虚拟dom
8. 导入app.js完毕，现在获取到了所需的虚拟dom，将其传入createapp函数中

   1. create函数将传入的app放到...args中，调用ensurerenderer函数返回的createapp函数
   2. ensurerenderer返回renderer对象，如果该对象为空则返回createrenderer函数创建的对象，createrenderer会传入创建元素，文本，文字，插入，删除等所有dom操作方法放到options中解构使用

      ```js
      function ensureRenderer() {
        // 如果 renderer 有值的话，那么以后都不会初始化了
        return (
          renderer ||
          (renderer = createRenderer({
            createElement,
            createText,
            setText,
            setElementText,
            patchProp,
            insert,
            remove,
          }))
        );
      }
      ```
   3. createrenderer函数构建流程

      1. 首先定义render函数，传入vnode，和container容器
         render会调用patch传入null，vnode和container
   4. 返回包含render和createapp函数的对象，createapp相当于createappapi函数，传入了render函数

      1. createappapi会返回createapp函数
      2. createapp函数接收rootcomponent对象，定义好app对象

         ```js
         export function createAppAPI(render) {
           return function createApp(rootComponent) {
             const app = {
               _component: rootComponent,
               mount(rootContainer) {
                 console.log("基于根组件创建 vnode");
                 const vnode = createVNode(rootComponent);
                 console.log("调用 render，基于 vnode 进行开箱");
                 render(vnode, rootContainer);
               },
             };

             return app;
           };
         }
         ```
      3. app对象中的component包含render返回的虚拟dom
      4. 同时含有mount方法接受rootcontainer的id选择器，用之前创建的createvnode方法传入返回虚拟vnode
      5. 接下来调用render函数传入vnode和容器
      6. 最终返回app对象
   5. 调动mount方法，生成dom，createvnode的实现

      ```js
      export const createVNode = function (
        type: any,
        props?: any,
        children?: string | Array<any>
      ) {
        // 注意 type 有可能是 string 也有可能是对象
        // 如果是对象的话，那么就是用户设置的 options
        // type 为 string 的时候
        // createVNode("div")
        // type 为组件对象的时候
        // createVNode(App)
        const vnode = {
          el: null,
          component: null,
          key: props?.key,
          type,
          props: props || {},
          children,
          shapeFlag: getShapeFlag(type),
        };

        // 基于 children 再次设置 shapeFlag
        if (Array.isArray(children)) {
          vnode.shapeFlag |= ShapeFlags.ARRAY_CHILDREN;
        } else if (typeof children === "string") {
          vnode.shapeFlag |= ShapeFlags.TEXT_CHILDREN;
        }

        normalizeChildren(vnode, children);

        return vnode;
      };
      ```
   6. vnode包含el元素和component组件和key，type和props参数和children子节点数组
   7. 如果children是数组则将vnode的shapeflag或一个ShapeFlags.ARRAY_CHILDREN变量
   8. 之后调用normalizeChildren函数传入vnode和children

      ```js
      export function normalizeChildren(vnode, children) {
        if (typeof children === "object") {
          // 暂时主要是为了标识出 slots_children 这个类型来
          // 暂时我们只有 element 类型和 component 类型的组件
          // 所以我们这里除了 element ，那么只要是 component 的话，那么children 肯定就是 slots 了
          if (vnode.shapeFlag & ShapeFlags.ELEMENT) {
            // 如果是 element 类型的话，那么 children 肯定不是 slots
          } else {
            // 这里就必然是 component 了,
            vnode.shapeFlag |= ShapeFlags.SLOTS_CHILDREN;
          }
        }
      }
      ```
   9. 调用render函数传入vnode和rootcontainer

      1. render会根据接收到的vnode和container进行path
      2. patch会根据不同的类型做不同的处理，首先获取到变量中的type

         ```js
           function patch(
             n1,
             n2,
             container = null,
             anchor = null,
             parentComponent = null
           ) {
             // 基于 n2 的类型来判断
             // 因为 n2 是新的 vnode
             const { type, shapeFlag } = n2;
             switch (type) {
               case Text:
                 processText(n1, n2, container);
                 break;
               // 其中还有几个类型比如： static fragment comment
               case Fragment:
                 processFragment(n1, n2, container);
                 break;
               default:
                 // 这里就基于 shapeFlag 来处理
                 if (shapeFlag & ShapeFlags.ELEMENT) {
                   console.log("处理 element");
                   processElement(n1, n2, container, anchor, parentComponent);
                 } else if (shapeFlag & ShapeFlags.STATEFUL_COMPONENT) {
                   console.log("处理 component");
                   processComponent(n1, n2, container, parentComponent);
                 }
             }
           }
         ```
      3. ```js
           function processComponent(n1, n2, container, parentComponent) {
             // 如果 n1 没有值的话，那么就是 mount
             if (!n1) {
               // 初始化 component
               mountComponent(n2, container, parentComponent);
             } else {
               updateComponent(n1, n2, container);
             }
           }
         ```
      4.
