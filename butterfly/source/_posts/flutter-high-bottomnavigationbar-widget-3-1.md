---
title: 【Flutter 3-1】Flutter进阶教程——底部导航栏BottomNavigationBar使用
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-01-29 15:08:27
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter BottomNavigationBar
  - Flutter 进阶教程
  - Flutter 项目
  - Flutter 底部导航栏
categories: Flutter
keywords: Flutter BottomNavigationBar Row，Flutter 进阶教程， Flutter 项目，底部导航栏
description: BottomNavigationBar 和 BottomNavigationBarItem 配合来共同展示Flutter里面的底部状态栏，底部状态栏是在移动端很重要的控件。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)


### BottomNavigationBar
`BottomNavigationBar` 和 `BottomNavigationBarItem` 配合来共同展示Flutter里面的底部状态栏，底部状态栏是在移动端很重要的控件。

先看一下 `BottomNavigationBar`构造方法
``` dart

BottomNavigationBar({
    // key
    Key key,
    /// BottomNavigationBarItem 数组
    @required this.items,
    /// 点击事件方法
    this.onTap,
    /// 当前选中的 元素下标
    this.currentIndex = 0,
    ///  底部导航栏的Z坐标
    this.elevation,
    /// 默认是 BottomNavigationBarType.shifting 一般我们使用 BottomNavigationBarType.fixed
    this.type,
    /// 选中项目颜色的值
    Color fixedColor,
    /// 背景颜色
    this.backgroundColor,
    /// BottomNavigationBarItem图标的大小
    this.iconSize = 24.0,
    /// 选中时图标和文字的颜色
    Color selectedItemColor,
    /// 未选中时图标和文字的颜色
    this.unselectedItemColor,
    // 选中时的子Item的样式
    this.selectedIconTheme,
    /// 未选中时的子Item的样式
    this.unselectedIconTheme,
    // 选中时字体大小
    this.selectedFontSize = 14.0,
    /// 未选中时的字体大小
    this.unselectedFontSize = 12.0,
    /// 选中的时候的字体样式
    this.selectedLabelStyle,
    /// 未选中时的字体样式
    this.unselectedLabelStyle,
    /// 是否为未选择的BottomNavigationBarItem显示标签
    this.showSelectedLabels = true,
    //// 是否为选定的BottomNavigationBarItem显示标签
    this.showUnselectedLabels,
    /// pc端或web端使用
    this.mouseCursor,
})
```

我们来做一个点击底部状态栏按钮切换颜色的Demo

``` dart 
class _BottomNavigationBarDemoPageState
    extends State<BottomNavigationBarDemoPage> {
  int selectedIndex = 0;
  List<Container> containerList = [
    Container(
      color: Colors.red,
    ),
    Container(
      color: Colors.blue,
    ),
    Container(
      color: Colors.yellow,
    ),
    Container(
      color: Colors.green,
    )
  ];
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        centerTitle: true,
        title: Text("BottomNavigationBarDemo"),
        backgroundColor: Colors.blue,
      ),
      body: containerList[selectedIndex],
      bottomNavigationBar: BottomNavigationBar(
        /// 这个很重要
        type: BottomNavigationBarType.fixed,
        currentIndex: selectedIndex,
        onTap: (index) {
          setState(() {
            selectedIndex = index;
          });
        },
        items: <BottomNavigationBarItem>[
          BottomNavigationBarItem(
            title: Text('F1'),
            icon: Icon(Icons.home),
          ),
          BottomNavigationBarItem(
            title: Text('F2'),
            icon: Icon(Icons.book),
          ),
          BottomNavigationBarItem(
            title: Text('F3'),
            icon: Icon(Icons.school),
          ),
          BottomNavigationBarItem(
            title: Text('F4'),
            icon: Icon(Icons.perm_identity),
          ),
        ],
      ),
    );
  }
}
```
- `Scaffold`接收一个`BottomNavigationBar`作为`bottomNavigationBar`的参数，然后`BottomNavigationBar`接收一个`items`的数组，这个数组里面传入了4个`BottomNavigationBarItem`对象分别命名为`F1`、`F2`、`F3`、`F4`

- `type`参数传入的是`BottomNavigationBarType.fixed`，默认是`BottomNavigationBarType.shifting`，默认的效果是 只有在选中`BottomNavigationBarItem`时才会显示文字。设置成`BottomNavigationBarType.fixed`非选中状态下也会显示文字和图标

- `onTap`实现的是一个方法，参数是被点击的当前`BottomNavigationBarItem`的下标，在这里被点击后调用`setState`来刷新页面的颜色

效果如下：

![2020_01_29_bottom_navigation_bar](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_29_bottom_navigation_bar.gif)


日常开发中以上效果基本能满足大多数需求
如果想要自定义下面Icon的样式，可以使用 [BottomAppBar](https://material.io/components/app-bars-bottom/android#anatomy-and-key-properties)

这里也介绍两个不错的库
- tab_bar_animation 

  链接: https://github.com/tunitowen/tab_bar_animation
  效果如下：
![2020_01_29_bottom_th2](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_29_bottom_th2.gif)
- simpleanimations 
  链接: https://github.com/TechieBlossom/simpleanimations
  效果如下：
![2020_01_29_bottom_th1](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_29_bottom_th1.gif)


想体验以上的示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`bottom_navigation_page.dart`查看，并且可以下载下来运行并体验。

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)