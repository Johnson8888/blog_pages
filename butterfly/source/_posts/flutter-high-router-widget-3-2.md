---
title: 【Flutter 3-2】Flutter进阶教程——路由Router和导航Navigator以及传值
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
在移动开发中，我们管页面之间的跳转叫做路由。在iOS中指的就是ViewController之间的跳转，在Android中就是Activity之间的跳转。路由是在移动端开发中非常重要的概念，它负责管理着各个页面之间的跳转还有传值工作，是必不可缺少的控件。

### 路由Map
为了方便我们管理跳转页面，`Flutter`为我们 提供了路由Map。
路由Map由在`main.dart`文件里面`MaterialApp`的参数`routes`管理，`routes`参数接收一个Map，Map里面就是我们项目的路由Map，你可以打开[我的项目](https://github.com/Johnson8888/learn_flutter)看到`routes`参数如下：
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
这里表示的是Flutter项目的入口页面对应的`key`是`/`，那么就会找到在`routes`中`/`对应的页面，也就是`MainPage()`

> 需要注意的是：
默认我们新创建的Flutter项目中`MaterialApp`是带有`home`这个参数的，它也表示也是入口页面。如果我们想要要使用路由Map的方式来管理路由，一定需要把`home`参数删除掉。

###  Navigator.pushNamed
在我们声明好路由Map之后，我们就可以传入前面的`key`的值来实现页面的跳转工作，这个时候我们需要借助的API是`Navigator.pushNamed`
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
代码如下：
``` dart
Navigator.pushNamed(context, "RouterDemoPage2");
```
> 由于我们是跨平台开发，Flutter帮助我们实现了跳转时候的转场动画，在iOS中动画是从右侧滑入到左侧，返回的时候同样是由左侧滑出到右侧。在Android则是由下方弹出显示到上方，返回的时候是由上方退出到下方弹出。

### 跳转传值
很多时候我们希望跳转的时候可以传值过去，这个时候我们可以通过自定义`MaterialPageRoute`来实现传值。
``` dart
MaterialPageRoute({
    /// builder 方法
    @required this.builder,
    /// 配置信息
    RouteSettings settings,
    ///  默认情况下，当入栈一个新路由时，原来的路由仍然会被保存在内存中，如果想在路由没用的时候释放其所占用的所有资源，可以设置maintainState为false。
    this.maintainState = true,
    ///  表示新页面是否是全屏展示，在iOS中，如果fullscreenDialog为true，新页面将会从屏幕底部滑入
    bool fullscreenDialog = false,
})
```
我们只需要在构建新的页面的时候传入我们想要传递的参数即可
``` dart
Navigator.of(context).push(MaterialPageRoute(builder: (context) {
  return RouterDemoPage3(passText: "Fulade");
}));
```

### 返回传值
传递返回值我们使用`Navigator`的`pop`方法即可
``` dart
Navigator.pop(context, "pop value");
```
`pop`方法接收一个参数为返回的携带的参数，如果我们有多个参数，可以把它封装为`List`或`Map`即可。

返回值我们需要在`push`方法后面使用`then`来接收
```dart
Navigator.of(context)
    .push(MaterialPageRoute(builder: (context) {
  return RouterDemoPage3(passText: "Fulade");
})).then((value) {
  setState(() {
    title = value;
  });
});
```
> `then`函数 涉及到了Dart语音中很重要的概念 await 和future，后面有机会我们再来详细的说。


想体验以上的示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`router_page.dart`查看，并且可以下载下来运行并体验。


***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
