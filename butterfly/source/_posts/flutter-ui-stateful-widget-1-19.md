---
title: 【Flutter 1-19】Flutter手把手教程UI布局和Widget——Statelesswidget与Statefulwidget
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-01-05 14:51:28
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter Statelesswidget
  - Flutter Statefulwidget
  - Flutter 控件
categories: Flutter
keywords: Flutter Statelesswidget，Flutter Statefulwidget，Flutter 控件
description: 在Flutter中一切皆为widget，其中Statelesswidget和Statefulwidget是Flutter比例很重要的两个widget。Statelesswidget是不需要改变状态的widget，Statefulwidget是允许改变状态的widget。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)


### Statelesswidget

如果一个Widget从初始化到使用再到销毁，整个过程中都不需要修改其UI的样式，例如纯展示页面，我们就用`Statelesswidget`。常见的`Statelesswidget`有：`Text`、`Icon`、`ImageIcon`、`Dialog`等。可以看到这些往往都是一些展示类的，不需要改变其状态的控件。
使用`Statelesswidget`更轻量，更节省内存资源。初始化`Statelesswidget`的时候不会附带一些动态更新UI的方法，这样也会提升我们软件的性能。
> 需要注意的是：
在iOS开发中，初始化一个`Label`并命名为`la`，改变它的文字内容，会调用`la.text = @"new text"`，我们可以理解为`Label`不是`Statelesswidget`的，因为它的`text`属性被改变了。那Flutter的`Text`为什么又是`Statelesswidget`的呢？因为Flutter中一切Widget都是 “配置文件”，当我们修改文本之后，Flutter会帮助我们重新初始化一个`Text`，而不是修改当前的`Text`对象，这是与原生开发不一样的地方。


### Statefulwidget
`Statefulwidget`是可变的Widget，在我们的开发中会大量使用`Statefulwidget`。它实现了一个`setState`方法，当我们调用这个方法的时候，该`Statefulwidget`会被重新渲染，注意是**重新被渲染**，而不是局部更新。
当我们调用`setState`时，Flutter在收到该消息后，会重新调用其`build`方法重新构建这个widget，从而达到更新UI的目的。

来看如下代码：

``` dart

class StatefulWidgetDemoPage extends StatefulWidget {
  @override
  _StatefulWidgetDemoPageState createState() => _StatefulWidgetDemoPageState();
}

class _StatefulWidgetDemoPageState extends State<StatefulWidgetDemoPage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      floatingActionButton: FloatingActionButton(
        onPressed: () {
          setState(() {});
        },
        child: Icon(Icons.add),
      ),
      appBar: AppBar(
        title: Text("StatefuleWidget Demo"),
        centerTitle: true,
        backgroundColor: Colors.blue,
      ),
      body: Column(
        children: [
          Container(
            width: 100,
            height: 100,
            margin: EdgeInsets.all(10),
            /// 颜色一个随机值
            color: _randomColor(),
          ),
        ],
      ),
    );
  }

  /// 获取一个随机的颜色值
  _randomColor() {
    return Color.fromARGB(255, Random().nextInt(255), Random().nextInt(255),
        Random().nextInt(255));
  }
}
```
我们定义了一个生成随机颜色的方法`_randomColor()`，它会返回一个`Color`对象，然后我们又定义了一个`Container`，`Container`的初始化参数`color`的值是`_randomColor()`的返回值。然后我们在`FloatingActionButton`的`onPressed`的方法中调用一下`setState`方法，这个时候Flutter会重新绘制`StatefulWidgetDemoPage`，所以每次点击按钮，我们可以看到`Container`的颜色都是不一样的。

### 一切都是Widget
在Flutter中我们看到的UI元素都是由`Widget`**生成的**，包括手势，在Flutter中也是`Widget`。`Widget`并不是我们看到的UI元素，我们实际看到的UI元素叫`Element`，`Widget`是`Element`的配置数据。
我们写了大量的`Widget`经Flutter处理渲染生成了`Element`来展示在手机屏幕上。所以当我们调用`setState`方法的时候，我们只是更新了**配置数据**，Flutter依照更新后的配置数据来生成新的`Element`来达到渲染UI的目的。

> 注意
一个 `Widget`可以对应多个`Elememt`对象，这等同与一个配置文件可以生成多个实例对象一样。

想体验以上的示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`statefulwidget_page.dart`查看，并且可以下载下来运行并体验。

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
