---
title: '10. sass学习'
date: 2022-01-19 10:06:51
tags: 
    - 笔记
    - 基础
categories: 前端
---

## 更换sass源

官网：[ruby](https://www.sass.hk/install/)

```ruby
gem update --system
gem -v
gem sources --add https://gems.ruby-china.com/ --remove h
gem sources -l

bundle config mirror.https://rubygems.org https://gems.ruby-china.com
```

![](file://C:\Personal\Documents\IkMarkdown\.assets\1月20日sass.md246098.1806178.png)

```ruby
gem install sass
gem install compass
```

## 常用命令

```scss

```

## 项目构建

1. 编译目录
2. 资源目录

# 使用方法

## 使用变量

```scss
$sass-style: red;
div{
    color:$sass-style;
}
```

## 规则

- 下划线等同于-
-

![](file://C:\Personal\Documents\IkMarkdown\.assets\1月20日sass.md248439.0169909.png)

![](file://C:\Personal\Documents\IkMarkdown\.assets\1月20日sass.md248502.0948059.png)

```scss
--style=nested//嵌套（默认）
--style=expanded//展开
--style=compact//紧凑
--style=compressed//压缩
```

![](file://C:\Personal\Documents\IkMarkdown\.assets\1月20日sass.md250085.4915727.png)

## &

> &相当于当前选择器从顶级选择器到当前选择器的夫选择器组

![](file://C:\Personal\Documents\IkMarkdown\.assets\1月20日sass.md252346.3523103.png)

## @mixin

![](file://C:\Personal\Documents\IkMarkdown\.assets\1月20日sass.md302.2332279.png)

## 运算

![](file://C:\Personal\Documents\IkMarkdown\.assets\1月20日sass.md2916.6256426.png)

![](file://C:\Personal\Documents\IkMarkdown\.assets\1月20日sass.md2920.8035762.png)

## map

```scss
$mapObj:(
    c1:red,
    c2:blue,
    c3:black
);

.string-test{
    color: map-keys($mapObj);
    color: map-values($mapObj);
    color: map-get($mapObj, c2 );
    color: map-has-key($mapObj, c3 );
}
```

![](file://C:\Personal\Documents\IkMarkdown\.assets\1月20日sass.md5073.4717357.png)

![](file://C:\Personal\Documents\IkMarkdown\.assets\1月20日sass.md6706.498681.png)

![](file://C:\Personal\Documents\IkMarkdown\.assets\1月20日sass.md8027.2859747.png)

![](file://C:\Personal\Documents\IkMarkdown\.assets\1月20日sass.md8097.629221.png)

## 逻辑控制

```scss
@echo $key,$item in $map{
    //.... 
}

@if 3<5{
    //....
}@else if 4>7{
    //...
}@else{
    //...
}

@for $i from 1 to 6{
//1,2,3,4,5，没有6
}
@for $i from 1 to 6{
//1,2,3,4,5,6，包括6
}
```

# 总结

```mindmap
- scss
  - 安装
    - ruby
    - 修改镜像
    - gem 安装sass，compress
  - 编译
    - 使用附加表达式
    - sass file1:file2 -w --style=expanded
  - 变量
    - $name
    - &:相当于父亲
  - 逻辑控制
    - @echo
    - @if $var in map
  - 运算
  - 附加
    - @include
    - @extend
  - map:$mapName:(k:v,k:v,k:v);
    - 方法
      - map-remove
      - map-keys
      - map-values
      - map-merge
```
