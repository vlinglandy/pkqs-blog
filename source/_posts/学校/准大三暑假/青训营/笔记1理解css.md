---
title: '理解css'
date: 2023-01-20 10:06:51
tags: 
    - css
    - 基础
categories: 前端
---

[ppt地址](https://bytedance.feishu.cn/file/boxcnnXEvzh3hhRKNQGLoU1mjoh)

## css是什么？

> 级联样式表

## css的结构

- 选择器：选择器用来选中页面中要调整样式的元素，可以是标签，类，id，属性等
- 属性：用来指定要增加的样式属性
- 属性值：用来给属性值进行相应设置

## css引入方式

- 外部链接`<link ref="stylesheet" href="/aaa/bbb"></link>`
- 内联`<style></style>`
- 内部`<p style="aa=bb;"></p>`

## css工作方式

1. 加载html
2. 解析html
3. 加载css同时创建dom树
4. 解析css，将样式添加到dom树
5. 展示页面

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md218647.173366.png)

## css选择器种类

- id选择器
- 类选择器
- 后代选择器
- 属性选择器

## 组合

- 直接组合 ab
- 后代组合a b
- 父子组合a>b
- 兄弟组合a~b
- 相邻选择器a+b

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md219079.011119.png)

## 选择器特异度关联到选择器权重

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md219402.1933185.png)

## 继承

继承的含义就是一些元素会自动继承父元素的属性值，除非显示指定一个值

- 显示继承：通过给全局样式*添加样式，给html添加样式等，让其后代所有元素都附上该属性

## 初始值

- 每个css都有初始值，可以是none，可以是transparent
- 可以用initial显示指定为初始值

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md219886.4612302.png)

## css求值过程

1. 在解析好dom树和样式规则的前提下
2. 第一步：筛选，进行样式规则筛选，选择器匹配，属性有效，符合当前media
3. 第二步：多对一，首先一个属性值可能有多个声明值，根据选择器权重，权重高的在前，如果权重相似，那么后加载的css为最后的到的值
4. 第三步：处理空值，如果没有设置相应属性的选择器的值，那么就赋值为继承值或初始值，最后保证得到的属性值一定不为空
5. 第四步：规则化，将em，和百分数，小数转换为px整数值，最后得到实际应用值

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md220217.8306201.png)

![](https://assets.codepen.io/59477/value.svg)

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md220639.8503365.png)

## 布局

> 根据元素，容器，兄弟结点算出每个元素的位置空间

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md221547.2095768.png)

## width和height计算结果

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md221664.9078061.png)

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md221692.2893996.png)

## 常规流

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md222125.9937966.png)

## 行级排版

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md222239.9160676.png)

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md222262.8181075.png)

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md222275.4463433.png)

## positon定位

![](file://C:\Personal\Documents/IkMarkdown/.assets/笔记1理解css.md222443.5535013.png)
