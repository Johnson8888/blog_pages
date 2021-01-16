---
title: Flutter 2-10】Flutter手把手教程UI布局和Widget——列表ListView
author: 弗拉德
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-01-16 12:08:06
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter Column
  - Flutter 布局控件
  - Flutter Row
  - Flutter Flexible
  - Flutter Warp
  - Flutter ListView
categories: Flutter
keywords: Flutter Column，Flutter Row，Flutter 布局控件， Flutter Flexible，Flutter Warp，ListView 
description: ListView是在移动端非常常见的控件，在大多数的展示场景中都离不开ListView。在Flutter中对ListView的封装也非常好，简单几行代码就可以满足我们布局一个滚动列表的需求。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### ListView
`ListView`是在移动端非常常见的控件，在大多数的展示场景中都离不开`ListView`。在`Flutter`中对`ListView`的封装也非常好，简单几行代码就可以满足我们布局一个滚动列表的需求。

#### builder 
`Flutter`给我们提供了四种构造`ListView`的方法，有`ListView()`、`ListView.builder()`、`ListView.separated()`、`ListView.custom()`、

|  构造函数   | 描述  |
|  ----  | ----  |
| ListView()  | 静态构造方法 初始化之前需要确定数据源的大小 |
| ListView.builder()  | 动态构造方法  可动态传入数据 |
| ListView.separated() | 动态构造方法  可动态传入数据 可动态定制分割线的样式 |
| ListView.custom()  |  动态构造方法 需要传入SliverChildDelegate来做动态生成 |

**静态构造方法和动态构造方法**




想体验以上示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`listview_page.dart`查看，并且可以下载下来运行并体验。
