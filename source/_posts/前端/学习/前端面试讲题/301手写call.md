---
title: 'title'
date: 2022-08-15 10:06:51
tags: 手写
categories: js
---

## 手写call函数

```javascript
Function.prototype.myCall = function (context,...args) {
    var context = context || window;
    context.fn=this;
    var res=(args!=null&&args!=undefined)?context.fn(...args):context.fn();
    delete context.fn;
    return res;
}
function test(){
    console.log(this);
}
test.myCall({name:'lili'});
```

## 手写apply函数

```javascript
Function.prototype.myBind=function(obj,...args){
    obj=obj||windows;
    fn=this;
    return function(params){
        fn.apply(obj,params);
    }
}
```
