---
title: Flutter 2-12】Flutter手把手教程UI布局和Widget——网格列表GridView
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-01-16 16:59:45
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter Column
  - Flutter 布局控件
  - Flutter Row
  - Flutter Flexible
  - Flutter GridView
  - Flutter ListView
categories: Flutter
keywords: Flutter Column，Flutter Row，Flutter 布局控件， Flutter GridView Warp，ListView 
description: GridView 是在一个好用的网格布局控件，它的很多属性跟前面提到的ListView是一样的，重复的属性这里就不在赘述了。我们重点看几个初始化方法`GridView.count`、`SliverGridDelegateWithFixedCrossAxisCount`、`SliverGridDelegateWithMaxCrossAxisExtent`的使用。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### GridView
`GridView` 是在一个好用的网格布局控件，它的很多属性跟前面提到的ListView是一样的，重复的属性这里就不在赘述了。我们重点看几个初始化方法`GridView.count`、`SliverGridDelegateWithFixedCrossAxisCount`、`SliverGridDelegateWithMaxCrossAxisExtent`的使用。

### GridView.count
我们先来看`GridView.count`的构造函数
``` dart
GridView.count({
    /// key 
    Key key,
    /// 布局方向
    Axis scrollDirection = Axis.vertical,
    /// 是否 倒序显示
    bool reverse = false,
    /// ScrollController用于控制滚动位置和监听滚动事件
    ScrollController controller,
    /// 是否使用默认的controller
    bool primary,
    /// 滚动效果  可以通过此参数 设置 GridView 不可滚动
    ScrollPhysics physics,
    /// 是否根据子控件的总长度来设置 GridView 的长度，默认值为false
    bool shrinkWrap = false,
    ///  padding
    EdgeInsetsGeometry padding,
    /// 交叉轴 子控件的个数
    @required int crossAxisCount,
    /// 主轴方向的间距
    double mainAxisSpacing = 0.0,
    /// 交叉轴方向子元素的间距
    double crossAxisSpacing = 0.0,
    /// 子控件的宽高比例
    double childAspectRatio = 1.0,
    // 在 关闭屏幕时 是否释放子控件
    bool addAutomaticKeepAlives = true,
    /// 是否 避免列表项重绘
    bool addRepaintBoundaries = true,
    /// 该属性表示是否把子控件包装在IndexedSemantics里，用来提供无障碍语义
    bool addSemanticIndexes = true,
    // 预加载子控件的个数
    double cacheExtent,
    /// 子控件的数组
    List<Widget> children = const <Widget>[],
    /// 子控件的数量
    int semanticChildCount,
    DragStartBehavior dragStartBehavior = DragStartBehavior.start,
    ScrollViewKeyboardDismissBehavior keyboardDismissBehavior = ScrollViewKeyboardDismissBehavior.manual,
})
```
这里要说的是有两个比较重要的参数`crossAxisSpacing`和`childAspectRatio`，这个两个参数是用来定义子控件大小的  

比如我们设置 `crossAxisSpacing = 2`,那么每一行就会显示`2`个控件，而且控件的高度由`childAspectRatio`来确定，`childAspectRatio`表示的宽高的比，假如我们设置为`2 / 3`，那么高就是宽的1.5倍，这样我们就可以定义子控件的大小了，并且按照 `GridView`设置好的方向来排列和布局子控件。
``` dart
GridView.count(
    crossAxisCount: 3,
    childAspectRatio: 2 / 3,
    children: List.generate(
        50,
        (index) {
        return Card(
            child: Container(
            color: Colors.green,
                child: Center(
                    child: Text("$index"),
                ),
            ),
        );
        },
    ),
)
```
效果图如下：   
![2021_01_16_gridview_count](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_16_gridview_count.png)


#### SliverGridDelegateWithFixedCrossAxisCount
除了`GridView.count()`这种构造方法，我们很多时候常用一个构造方法是`GridView.builder(gridDelegate: itemBuilder:)`，它接收一个`delegate`对象，并且跟`ListView`一样接收一个`itemBuilder`方法。
`SliverGridDelegateWithFixedCrossAxisCount`的构造方法如下：  

``` dart
SliverGridDelegateWithFixedCrossAxisCount({
  @required this.crossAxisCount,
  this.mainAxisSpacing = 0.0,
  this.crossAxisSpacing = 0.0,
  this.childAspectRatio = 1.0,
})
```
可以看得出来它是把`GridView.count()`的几个参数封装了一下，具体的用法和效果跟`GridView.count()`一样，这里就不赘述了。

`SliverGridDelegateWithFixedCrossAxisCount`在很多情况下都能满足我们的布局需求，但是有一个不足，因为它设置的每一行的数量是一个定值，当我们把屏幕旋转，此时原来的高度会变为现在的宽度，效果就会如下：
![2021_01_16_gridview_la](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_16_gridview_la.jpg)

所以我们可以使用以下参数来解决这个问题  

#### SliverGridDelegateWithMaxCrossAxisExtent
我们可以在`GridView.builder(gridDelegate: itemBuilder:)`方法内传入另外一个参数`SliverGridDelegateWithMaxCrossAxisExtent`

构造方法如下：
``` dart
const SliverGridDelegateWithMaxCrossAxisExtent({
    @required this.maxCrossAxisExtent,
    this.mainAxisSpacing = 0.0,
    this.crossAxisSpacing = 0.0,
    this.childAspectRatio = 1.0,
}) 
```