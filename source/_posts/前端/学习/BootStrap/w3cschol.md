---
title: 'w3cschol'
date: 2022-10-17 10:06:51
tags: 
categories: 前端
---

## 标题

```html
<span class="h1">你好</span>
<span class="h2">这是标题</span>
<span class="h3">这是标题</span>
<span class="h4">这是标题</span>
<span class="h5">这是标题</span>
<span class="h6">这是标题</span>
<h1>主标题<small>副标题</small></h1>
```

![](file://C:\Personal\Documents\IkMarkdown\.assets\w3cschol.md862.4771198.png)

## 页面主体

```html
Bootstrap 将页面主体设置默认为：

font-size:14px；

line-height:20px

<p>标签行高:10px

颜色:#333；
```

## 文本类

```html
<p>Bootstrap 框架</p>
<p class="lead">Bootstrap 框架</p>
<p>Bootstrap 框架</p>
<p class="text-left">Bootstrap 框架</p>
<p class="text-justify">Bootstrap 框架</p>
<p class="text-lowercase">小写hello WORLD</p>
<p class="text-uppercase">大写hello WORLD</p>
<p class="text-capitalize">首字母大写hello WORLD</p>
```

> 突出显示

> 注：
> text-left：向左对齐
> text-right：向右对齐
> text-center：居中对齐
> text-justify：两端对齐

## 略缩语

```html
<abbr title="World Wide Web">WWW</abbr>
<abbr title="World Wide Web" class="initialism">WWW</abbr>
```

## 引用文本

```html
<blockquote>
    <p>Bootstrap 框架 - W3Cschool </p>
</blockquote>
```

```html
<!--实现右对齐-->
<blockquote class="blockquote-reverse">
    <p>Bootstrap 框架 - W3Cschool </p>
</blockquote>
```

## 列表样式

![](https://www.w3cschool.cn/attachments/image/20190524/1558684098864274.png)

## 显示代码

> 用code或者pre

## 表格

![](file://C:\Personal\Documents\IkMarkdown\.assets\w3cschol.md1746.5527591.png)

```html
<table class="table  table-bordered">

    <thead>

    <tr>

        <th>产品</th>

        <th>付款日期</th>

        <th>状态</th>

    </tr>

    </thead>

    <tbody>

    <tr>

        <td>产品1</td>

        <td>23/05/2019</td>

        <td>待发货</td>

    </tr>

    <tr>

        <td>产品2</td>

        <td>13/05/2019</td>

        <td>发货中</td>

    </tr>

    </tbody>

</table>
```

## 表格状态类

![QQ图片20190525140350](https://www.w3cschool.cn/attachments/image/20190525/1558764249596906.png)

```html
<table class="table table-hover table-bordered">
    <caption>表格布局</caption>
    <thead>
    <tr>
        <th>产品</th>
        <th>付款日期</th>
        <th>状态</th>
    </tr>
    </thead>
    <tbody>
    <tr class="active">
        <td>产品1</td>
        <td>23/05/2019</td>
        <td>待发货</td>
    </tr>
    <tr class="success">
        <td>产品2</td>
        <td>13/05/2019</td>
        <td>发货中</td>
    </tr>
    <tr  class="warning">
        <td>产品3</td>
        <td>23/02/2019</td>
        <td>待确认</td>
    </tr>

    <tr  class="danger">
        <td>产品4</td>
        <td>23/05/2018</td>
        <td>已退货</td>
    </tr>
    </tbody>
</table>
```

## 按钮

```html
<a href="###" class="btn btn-default">Link</a>
<button class="btn btn-default">Button</button>
<input type="button" class="btn btn-default" value="input">
```

> btn-default 默认样式        btn-success 成功样式
> btn-warning 警告样式      btn-danger 危险样式
> btn-primary 首选项样式   btn-link 链接样式  btn-info 信息样式

```html
<button type="button" class="btn btn-default">默认按钮</button>

<button type="button" class="btn btn-primary">原始按钮</button>

<!-- 并不强调是一个按钮，看起来像一个链接，但同时保持按钮的行为 -->

<button type="button" class="btn btn-link">链接按钮</button>

<button type="button" class="btn btn-success">成功按钮</button>

<button type="button" class="btn btn-info">信息按钮</button>

<button type="button" class="btn btn-warning">警告按钮</button>

<button type="button" class="btn btn-danger">危险按钮</button>
```

## 尺寸大小

```html
<button class="btn btn-lg">Button</button>
<button class="btn">Button</button>
<button class="btn btn-sm">Button</button>
<button class="btn btn-xs">Button</button>
```

## 基本样式

```html
<body>

<!-- 标准的按钮 -->
<button type="button" class="btn btn-default btn-lg">大的默认按钮</button>
<button type="button" class="btn btn-default btn-lg active">大的激活的默认按钮</button>

<!-- 提供额外的视觉效果，标识一组按钮中的原始动作 -->
<button type="button" class="btn btn-primary btn-sm">小的原始按钮</button>
<!-- 表示一个成功的或积极的动作 -->
<button type="button" class="btn btn-success btn-xs">特小的成功按钮</button>
<!-- 信息警告消息的上下文按钮 -->
<button type="button" class="btn btn-info btn-lg btn-block">块级的信息按钮</button>
<!-- 表示应谨慎采取的动作 -->
<button type="button" class="btn btn-warning ">警告按钮</button>
<!-- 表示一个危险的或潜在的负面动作 -->
<button type="button" class="btn btn-danger disabled">禁用的危险按钮</button>
<!-- 并不强调是一个按钮，看起来像一个链接，但同时保持按钮的行为 -->
<button type="button" class="btn btn-link">链接按钮</button>
```

## 栅格系统

![](file://C:\Personal\Documents\IkMarkdown\.assets\w3cschol.md2723.7273675.png)

![12351521412412412421](https://www.w3cschool.cn/attachments/image/20190614/1560500254470961.png)
