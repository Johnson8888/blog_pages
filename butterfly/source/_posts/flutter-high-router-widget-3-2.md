---
title: 【Flutter 3-1】Flutter进阶教程——路由Router和导航Navigator以及传值
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-01-31 20:42:02
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter Router
  - Flutter Navigator
  - Flutter 导航栏
  - Flutter Router传值
categories: Flutter
keywords: Flutter Router，Flutter Navigator， Flutter 导航栏，Router传值
description: 在移动开发中，我们管页面之间的跳转叫做路由。在iOS中只的就是ViewController之间的跳转，在Android中就是Activity之间的跳转。路由是在移动端开发中非常重要的概念，它负责管理着各个页面之间的跳转还有传值工作，是必不可缺少的控件。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### 路由
在移动开发中，我们管页面之间的跳转叫做路由。在iOS中只的就是ViewController之间的跳转，在Android中就是Activity之间的跳转。路由是在移动端开发中非常重要的概念，它负责管理着各个页面之间的跳转还有传值工作，是必不可缺少的控件。

### 路由Map
为了方便我们管理跳转页面，`Flutter`为我们 提供了路由Map。
对于路由Map的管理是在`main.dart`文件里面`MaterialApp`的参数`routes`，`routes`参数接受一个Map，Map里面就是我们项目的路由Map，你可以打开我的项目看到`routes`参数如下：
``` dart
routes: {
  "/": (context) => MainPage(),
  "TextDemoPage": (context) => TextDemoPage(),
  "RaisedButtonDemoPage": (context) => RaisedButtonDemoPage(),
  "FlatButtonDemoPage": (context) => FlatButtonDemoPage(),
  "OutlineButtonDemoePage": (context) => OutlineButtonDemoePage(),
  "IconButtonDemoPage": (context) => IconButtonDemoPage(),
  "ContainerDemoPage": (context) => ContainerDemoPage(),
  "StatefulWidgetDemoPage": (context) => StatefulWidgetDemoPage(),
  "TextFieldDemoPage": (context) => TextFieldDemoPage(),
  "ImageDemoPage": (context) => ImageDemoPage(),
  "ColumnDemoPage": (context) => ColumnDemoPage(),
  "RowDemoPage": (context) => RowDemoPage(),
  "FlexibleDemoPage": (context) => FlexibleDemoPage(),
  "WrapDemoPage": (context) => WrapDemoPage(),
  "ListViewDemoPage": (context) => ListViewDemoPage(),
  "GridViewDemoPage": (context) => GridViewDemoPage(),
  "BottomNavigationBarDemoPage": (context) =>
      BottomNavigationBarDemoPage(),
  "RouterDemoPage": (context) => RouterDemoPage(),
  "RouterDemoPage2": (context) => RouterDemoPage2(),
},
```
其中`key`为`/`对应的`Value`是整个Flutter项目的入口页面，这里需要另外一个很重要的参数`initialRoute`来配合使用
我们给`initialRoute`参数传值如下：
``` dart 
    initialRoute: "/",
```
这里的表示的就是Flutter项目的入口页面对于的`key`是`/`，那么就会找到在`routes`中`/`对应的页面，这里也就是`MainPage()`

> 需要注意的是：
默认我们新创建的Flutter项目中`MaterialApp`是带有`home`这个参数，它也表示也是入口页面。如果我们想要要使用路由Map的方式来管理路由，一定需要把`home`参数删除掉。

###  Navigator.pushNamed
在我们声明好路由Map之后，我们就可以传入前面的`key`的值来实现页面的跳转工作，这个时候我们需要借助的API就是`Navigator.pushNamed`
``` dart
 @optionalTypeArgs
  static Future<T> pushNamed<T extends Object>(
    BuildContext context,    /// context
    String routeName, {     /// 路由Map中 key 的值
    Object arguments,        /// 参数
   }) {
    return Navigator.of(context).pushNamed<T>(routeName, arguments: arguments);
  }
```
只需要传入路由Map中`key`的值就可以实现跳转。

> 由于我们是跨平台开发，Flutter帮助我们实现了跳转时候的动画，在iOS中动画是从右侧划入到左侧，返回的时候同样是由左侧划出到右侧。在Android则是由下方弹出显示到上方，返回的时候是由上方退出到下方弹出。

