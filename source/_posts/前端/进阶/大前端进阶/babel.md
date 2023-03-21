---
title: '基本使用'
date: 2022-01-19 10:06:51
tags: 
    - 笔记
    - 基础
    - babel
categories: 前端
---

## 使用过程

1. 首先定义一个node的项目nom init -y
2. 然后新建一个src目录，写上js文件
3. 配置.babelrc文件：{"presets":["es2015"],"plugins":[]}
4. 安装解码器：cnpm install --save-dev babel-preset-es2015
5. 生成编译文件babel src -d dist
