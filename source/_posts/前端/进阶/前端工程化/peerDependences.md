---
title: 'peerDependences是干什么的？'
date: 2022-01-19 10:06:51
tags: 
    - 笔记
    - 基础
categories: 前端
---

[博客园](https://www.cnblogs.com/fitzlovecode/p/peerDependencies.html)

[知乎](https://zhuanlan.zhihu.com/p/460614360)

1. 首先声明它存在的目的是为了减少项目中的依赖
2. 比如项目依赖了a和b的1.0版本，同时a又依赖b的1.0版本，那么如果我们直接npmi的话他会把b的1.0版本安装两遍
3. 那这时候peerdependences就站出来了，他本质是并行依赖的含义，比如我们开发一个插件a，然后这个插件依赖于b的1.0之后的版本，那我们就可以在a的package.json中写b:>=1.0
4. 然后我们编写项目中已经有b了，他是1.5版本的，那就直接用
5. 因为peerdependences记录了这种同伴关系我们就可以利用同伴给他归类，最总减少代码量
