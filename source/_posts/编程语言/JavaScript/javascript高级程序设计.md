---
title: '高级程序设计笔记'
date: 2022-11-20 10:06:51
tags: 基础
categories: js
---

## 4.1原始值与引用值

```javascript
let obj1=new Object();
let obj2=obj1;
obj1.name="axian";
console.log(obj2.name);//"axian"
```

## 4.2形式参数如果拷贝的是值那么就会复制一份，如果是引用，那么就拷贝地址，传递指针

> undefined保存在undefined类型里
>
> null保存到object类型里
>
> 2保存在number里
>
> true保存在boolean里
>
> “zxczx”保存在字符串里

## 4.3垃圾回收问题

> 垃圾回收问题基本内容就是周期性的确认某个变量不会被使用，然后及时释放这个变量所占的内存
>
> 但是垃圾回收是一个近似且不完美的方案，因为判断某块内存是否还有用属于“不可判定问题”，意味靠算法是解决不了的

## 解决垃圾回收问题的方法：标记清理和引用计数。

> 标记清理：在垃圾回收机制运行时，首先会将内存中所有的变量都进行标记，然后会将上下文的变量和所有上下文引用的变量的标记都进行清理，接下来标记的变量就是要删除的变量了

> 引用计数：就是对每个值都记录被引用的次数，如果一个变量被创建并初始化一个引用值时，那么这个值的引用就是1，如果还有别的变量用到这个值，那么引用数+1，如果引用这个值的变量被覆盖，那个引用数-1，当这个引用值为0时，就说明没办法引用这个值了，说明可以清理这个变量的内存了

## 6.2 Array

**创建数组的几种方式**

```javascript
let a1=new Array();
let a2=new Array(10);//创建一个有是个元素的数组，内容都是undefined
let a3=Array();//与第一种相同
let a4=new Array(1,2,3,4);//形成一个内容为1,2,3,4的数组
let a5=new Array("a","b","c");
```

**Array.from()和Array.of()方法**

```javascript
let m=new Map().set(1,2).set(2,3);
let a1=Array.from(m);//[[1,2],[2,3]]

let s=new Set().add(1).add(2);
let a2=Array.from(s);//[1,2]

let a3=Array.from("asdasdasd");//相当于split

let a4=Array.from([1,2,3,4],x=>x**2);

//of替代了.call.apply(null,arguments);
//相当于new Array(1,2,3,4);
let a5=Array.of(1,2,3,4);
```

**Array的其他操作**

> 对象解构和数组遍历

```javascript
let aa=[1,2,3,4];
let res=Array.from(aa.entries());
for(var [index,val] of res){
    console.log(index,val);
}
```

> 修改数组的length来进行插入删除

```javascript
var cc=[1,2,3];
cc.length=1;
cc[cc.length]=cc.length;
```

## 数组操作

**concat（拼接新数组）**

**slice（切片）**

> 相当于字符串的substring，只不过操作对象是数组

**splice（粘接，可用于删除，插入，修改）**

## Set,Map

```javascript
let s=new Set([1,2,3]);

let m=new Map([
    [1,2],
    [2,3]
]);
```
