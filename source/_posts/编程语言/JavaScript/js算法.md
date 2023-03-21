---
title: '手写'
date: 2022-11-20 10:06:51
tags: 基础
categories: js
---

# js之join方法实现

```javascript
var arr=[1,2,3];
var newArr=arr.join('=');
Array.prototype.newJoin=function (){
  var s="";
  for(let i=0;i<this.length;i++){
    if(this[i]===null||this[i]===undefined){
      this[i]="";
    }
    if(arguments!==undefined&&i!=this.length-1){
      s+=this[i]+arguments;
    }else{
      s+=this[i];
    }
  }
  return s;
}
```

# js之find方法实现

```javascript
var arr=[1,2,3,4,5,6];
arr.find(function(){
  return arr>=arguments[0];
});
Array.prototype.newFind=function (func){
  if(typeof func!=="function"){
    throw new Error(`${func}不是一个函数`);
  }
  if(this===null||this===undefined){
    return this;
  }
  for(let i=0;i<this.length;i++){
    if(func(this[i],i,this)){
      return this[i];
    }
  }
  return undefined;
}
```

# js之push方法实现

```javascript
<script>
  var arr=[1,2,3,4,5,6];
  var newArr=arr.push(3,2,1);
  console.log(newArr);
  Array.prototype.newPush=function (){
    var lenThis=this.length;
    var legArgu=arguments.length;
    lenThis===0?return arguments:;
    lenArgu===0?return this:;
    for(let i=0;i<lenArgu;i++){
      this[lenThis+i]=arguments[i];
    }
  }
</script>
```

## js插入

```javascript
arrays.splice(pos,num,...arr);
arrays.splice(3,0,...arr);
```
