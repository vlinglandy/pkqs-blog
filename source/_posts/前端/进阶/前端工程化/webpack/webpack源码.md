---
title: 'webpack源码分析'
date: 2022-01-19 10:06:51
tags: 
   - 源码
   - webpack
categories: 前端
---

## 前情提要

## `__webpack_require__.d`

传入导出对象和文件中定义的导出对象，判断定义的对象是否全部导出，如果没有则在导出对象上定义好获取方式，define

## `__webpack_require__.o`

传入对象和key，判断key是否定义在对象上，own

## `__webpack_require__.r`

给传入的对象定义为esmodule，report

## `__webpack_exports__`

初始化每个模块的对象

## `__WEBPACK_DEFAULT_EXPORT__`

每个模块默认导出函数

## `__webpack_modules__`

一个数组，索引是模块id，值是每个模块的执行函数

module是新创建的模块，里面有一个exports属性

`module, module.exports, __webpack_require__`与`__unused_webpack_module, __webpack_exports__, __webpack_require__`相对应

## `__webpack_require__`

传入模块id，返回模块导出对象

## 打包后的bundle.js究竟做了什么？

1. 首先声明严格模式
2. 定义好`__webpack_modules__`对象，key是一个id为模块id，值是一个函数，

   1. 这个函数首先用`__webpack_require__.r`方法给传入的对象添加一个esmodule的属性，值为true，也就是标记该模块是esmodule
   2. ```javascript
      __webpack_require__.d(__webpack_exports__, {
        "default": () => (__WEBPACK_DEFAULT_EXPORT__)
      });
      ```
   3. 然后用以上方法给__webpack_exports__定义了一个default属性，值是一个函数，返回 __WEBPACK_DEFAULT_EXPORT__
   4. 之后定义 __WEBPACK_DEFAULT_EXPORT__ 函数为模块导出的具体内容

```javascript
/******/ (() => { // webpackBootstrap
/******/ 	"use strict";
/******/ 	var __webpack_modules__ = ([
/* 0 */,
/* 1 */
/***/ ((__unused_webpack_module, __webpack_exports__, __webpack_require__) => {

__webpack_require__.r(__webpack_exports__);
/* harmony export */ __webpack_require__.d(__webpack_exports__, {
/* harmony export */   "default": () => (__WEBPACK_DEFAULT_EXPORT__)
/* harmony export */ });
/* harmony default export */ const __WEBPACK_DEFAULT_EXPORT__ = (() => {
    let node = document.createElement('div')
    node.innerText = 'hello webpack'
    document.getElementById('app').append(node)
});

/***/ })
/******/ 	]);
/************************************************************************/
/******/ 	// The module cache
/******/ 	var __webpack_module_cache__ = {};
/******/ 
/******/ 	// The require function
/******/ 	function __webpack_require__(moduleId) {
/******/ 		// Check if module is in cache
/******/ 		var cachedModule = __webpack_module_cache__[moduleId];
/******/ 		if (cachedModule !== undefined) {
/******/ 			return cachedModule.exports;
/******/ 		}
/******/ 		// Create a new module (and put it into the cache)
/******/ 		var module = __webpack_module_cache__[moduleId] = {
/******/ 			// no module.id needed
/******/ 			// no module.loaded needed
/******/ 			exports: {}
/******/ 		};
/******/ 
/******/ 		// Execute the module function
/******/ 		__webpack_modules__[moduleId](module, module.exports, __webpack_require__);
/******/ 
/******/ 		// Return the exports of the module
/******/ 		return module.exports;
/******/ 	}
/******/ 
/************************************************************************/
/******/ 	/* webpack/runtime/define property getters */
/******/ 	(() => {
/******/ 		// define getter functions for harmony exports
/******/ 		__webpack_require__.d = (exports, definition) => {
/******/ 			for(var key in definition) {
/******/ 				if(__webpack_require__.o(definition, key) && !__webpack_require__.o(exports, key)) {
/******/ 					Object.defineProperty(exports, key, { enumerable: true, get: definition[key] });
/******/ 				}
/******/ 			}
/******/ 		};
/******/ 	})();
/******/ 
/******/ 	/* webpack/runtime/hasOwnProperty shorthand */
/******/ 	(() => {
/******/ 		__webpack_require__.o = (obj, prop) => (Object.prototype.hasOwnProperty.call(obj, prop))
/******/ 	})();
/******/ 
/******/ 	/* webpack/runtime/make namespace object */
/******/ 	(() => {
/******/ 		// define __esModule on exports
/******/ 		__webpack_require__.r = (exports) => {
/******/ 			if(typeof Symbol !== 'undefined' && Symbol.toStringTag) {
/******/ 				Object.defineProperty(exports, Symbol.toStringTag, { value: 'Module' });
/******/ 			}
/******/ 			Object.defineProperty(exports, '__esModule', { value: true });
/******/ 		};
/******/ 	})();
/******/ 
/************************************************************************/
var __webpack_exports__ = {};
// This entry need to be wrapped in an IIFE because it need to be isolated against other modules in the chunk.
(() => {
__webpack_require__.r(__webpack_exports__);
/* harmony import */ var _process_js__WEBPACK_IMPORTED_MODULE_0__ = __webpack_require__(1);


(0,_process_js__WEBPACK_IMPORTED_MODULE_0__["default"])()

})();

/******/ })()
;
```

## 总结

1. 首先定义好了`__webpack_modules__ `，key是模块id，属性是一个函数，这个函数会给传入的对象添加好所有属于该模块id的依赖
2. 之后`__webpack_require__`会根据模块id返回该模块对应的module.exports对象，如果缓存里有就直接拿，没有就创建一个包含exports属性的对象返回给module变量，同时将该对象传入`__webpack_modules__ `进而给这个对象添加好模块的所有方法
3. 运行时根据webpack定义好的依赖树进行执行，用到什么就require(id)进来

![](file://C:\Personal\Documents/IkMarkdown/.assets/webpack源码.md619427.862813.png)

![](file://C:\Personal\Documents/IkMarkdown/.assets/webpack源码.md630655.7572731.png)



![](file://C:\Personal\Documents/IkMarkdown/.assets/webpack源码.md630753.2392985.png)

合并模块

![](file://C:\Personal\Documents/IkMarkdown/.assets/webpack源码.md630941.8944969.png)
