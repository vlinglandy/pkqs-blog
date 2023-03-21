---
title: 'vue2 和 vue3 的区别'
date: 2023-01-20 10:06:51
tags: 
    - vue
    - 基础
categories: 前端
---

## 没有全局事件总线EventBus

> 所以我用了mitt

## mitt的坑，误踩！

> 不能直接this.$bus.$emit("xxx",a,b)
>
> 只能传递一个对象this.\$bus.emit("xxx",{a:a,b:b})

## vite里图片不能用webpack里的require

> 所以用new url拼接图片

## 跨域差不多

# 在原型上定义方法区别

> 改成app.config.globalProperties

## 变量.sync改为v-model:变量

## 没有了@xxx.native这个属性

## 没有element，我引入了plus

## vite没有webpack的@，需要自己设置别名(已经设置好了，实在不行只能点点杠大法../../../../)

## ::deep要改成:deep（）

## 介绍

1. 用过低代码的都知道，很多低代码只能生成布局非常受限的网页，并且布局容器也只能分成有限份数
2. LowCode-Any-Layout，快速帮你构建出任意布局，自适应的网页

```
![An image](./image.png)
```

![](file://C:\Personal\Documents/IkMarkdown/.assets/vue2和vue3区别.md292771.0675869.png)

## 事件总线：mitt

## 路由管理：router

## 视频组件：videojs

## 插件配置：vue.use

## UI：Element-Plus

## 请求模块:axios

## 数据解析：koa-bodyparser

## 静态托管：koa-static

## 

AnyLayout

Any-layout

any-layout

Any-Layout

AnY-lAyOuT

## 掘金首页的内容

## 必应图片

<br/>https://lf-cdn-tos.bytescm.com/obj/static/xitu_extension/static/bing.efab636f.png

## logo链接

https://lf-cdn-tos.bytescm.com/obj/static/xitu_extension/static/brand.82c24770.svg

## 掘金图片

<br/>https://lf-cdn-tos.bytescm.com/obj/static/xitu_extension/static/gold.981a5510.svg

## CSDN图片

https://lf-cdn-tos.bytescm.com/obj/static/xitu_extension/static/csdn.9c2b2075.png

## 工具图标

https://lf-cdn-tos.bytescm.com/obj/static/xitu_extension/static/icon-ip-lookup-normal.25ef5c44.svg

## 背景颜色

rgb(30,128,255)

## 文字颜色

rgb(134,144,156)

## 白色按钮

rgb(232,243,255)

## 下面背景

rgb(244,245,245)
