---
title: '8. documentElement具体解析'
date: 2022-01-19 10:06:51
tags: 
    - 笔记
    - 基础
categories: 前端
---

## document.documentElement.clientX

> 获取浏览器的可视宽度

```javascript
//添加事件监听器绑定点击事件,onclick不可用于事件捕获
element.addEventListener(
    "click",
    function(){
        console.log("haha");
    },
    false//是否捕获
);

//e.stopPropagation();//阻止时间捕获
```

## 事件冒泡与事件委托

## 对象解构可用于赋值，传参，转换

```javascript
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ul>
var ul=...;
var li=ul.````;
ul.addEventListener("click",function(e){
    if(e.target.tagName=="LI"){console.log(e.target.innerHtml);}
});//添加事件委托
```

```javascript
var axian={
    name:"pig",
    age:20
};
```
