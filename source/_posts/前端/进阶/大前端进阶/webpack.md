---
title: 'webpack基本使用'
date: 2023-01-19 10:06:51
tags: 
    - 笔记
    - 基础
categories: 前端
---

## 安装

```
npm install -g webpack webpack-cli
```

## 使用过程

- 首先新建一个node项目
- 然后写好要打包的文件
- 之后定义webpack.config.js的配置文件,导入path模块，定义规则，module.exports={entry:"src/main.js",output:{path:path.resolve(__dirname,"./dist"),filename:"bundle.js"}}
- 执行webpack

```javascript
exports.info=function(str){
    console.log(str);
};
```

```javascript
exports.add=function(a,b){
    console.log(a,b);
};
```

```javascript
const util=require("./util.js");
const common=require("./common.js");
common.info("你好");
util.add(1,2);
```

```javascript
const path = require("path");

module.exports={
    entry:"./src/main.js",
    output:{
        path:path.resolve(__dirname,"./dist"),
        filename:"bundle.js"
    }
}
```

## 打包css

- 安装类加载器npm install --save-dev style-loader css-loader
- 在webpack配置文件中新建module
- 在打包入口文件中添加css文件(require)

```javascript
module:{
    rules:[{
        test:/\.css$/,
        use:["style-loader","css-loader"]
    }]
}
```
