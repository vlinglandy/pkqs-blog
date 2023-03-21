---
title: 'cjs规范'
date: 2022-01-19 10:06:51
tags: 
    - 笔记
    - 基础
categories: 前端
---

## 流程

1. 定义
2. 导出module.exports={}
3. 使用const m=require("./xxx.js");

```javascript
const sum=function(a,b){
    return a+b;
}
const sub=function(a,b){
    return a-b;
}
const mul=function(a,b){
    return a+b;
}
const div=function(a,b){
    return a/b;
}

module.exports={
    sum,
    sub,
    mul,
    div
};
```

```javascript
const m=require("./one.js");
console.log(m.sum(1,2));
console.log(m.sub(1,2));
console.log(m.mul(1,2));
console.log(m.div(1,2));
```

## es6版本

> 注意：node暂时不支持es6，所以要使用需要将其用babel编译成es5

**第一种方式**

```javascript
export function first(){
    console.log("第一个");
}

export function getList(){
    console.log("获取模块列表");
}
```

```javascript
import { first,getList } from "./es61";

first();
getList();
```

**第二种方式**

```javascript
export default {
    first(){
        console.log("第一个");
    },
  
    getList(){
        console.log("获取模块列表");
    }
}
```

```javascript
import user  from "./es62.js";
user.first();
user.getList();
```
