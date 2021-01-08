---
title: 【Flutter 1-20】Flutter手把手教程UI布局和Widget——TextField使用、搭配InputDecoration和FocusedNode使用
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-01-07 15:09:54
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_07_material_textfiled.png
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_07_material_textfiled.png
tags:
    - Flutter TextField
    - Flutter 输入框
    - Flutter 输入控件
    - Flutter 控件
categories: Flutter
keywords: Flutter TextField，Flutter 输入框，Flutter 输入控件，Flutter 控件
description: TextField是一个常用的控件，是有状态的Statefulwidget，它是由多个控件组合成的控件，使用起来并不复杂，但是变化情况比较多，多看源码，避免踩坑。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### TextField 

TextField是一个常用的控件，同时它也是一个组合控件，由多个控件组合而成。
这是来自Material官方网站的的图片
![2021_01_07_material_textfield](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_07_material_textfiled.png)
TextField是由7个控件组成，其中有些控件默认不显示，我们也可以对各个控件单独设置想要的样式以此来完成不同的UI展示。
下面我们就来列举几种常见的样式：

**1. 简单的TextField**
``` dart
TextField(
    decoration: InputDecoration(
        labelText: "最基本的的TextField",
    ),
)
```
`TextField`接收一个`InputDecoration`作为参数，`InputDecoration`可以的参数`labelText`帮助我们定义placeholder。`labelText`模式会灰色的，选中之后会变为蓝色，并且`TextField`底部会有一条蓝色线条。

