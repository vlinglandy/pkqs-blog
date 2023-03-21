---
title: '包管理器'
date: 2022-01-19 10:06:51
tags: 
    - 笔记
    - 基础
categories: 前端
---

## npm（node package manager）

![](file://C:\Personal\Documents\IkMarkdown\.assets\npm包管理器.md142027.4601679.png)

![](file://C:\Personal\Documents\IkMarkdown\.assets\npm包管理器.md142099.1894383.png)

## npm init -y

> 以默认的方式生成package.json

## 运行方式

```javascript
const mysql=require("mysql");
const redis=require("redis");
const client=redis.createClient();
client.on("error",function(error){
    console.log(error);
});
client.set("key","value",redis.print);
client.get("key",redis.print);
```

## npm使用总结

- 初始化方式 npm init 或者npm init -y默认生成package.json
- 运行方式node 文件名称
- 运行编译项目npm run 分支名称
- 下载方式npm install xxx
- 可以下载多个文件npm install xxxx xxxx xxxx
- 指定版本号npm install xxx@版本号
- package.json的作用：相当于maven，记录依赖的版本号，之后利用npm install可以重新下载node modules的文件
- 使用模块用require("mysql");

![](file://C:\Personal\Documents\IkMarkdown\.assets\npm包管理器.md52802.3586232.png)
