---
title: 【Flutter 2-11】Flutter手把手教程UI布局和Widget——列表ListView
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

先来看一下构造函数：
```dart
ListView({
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
    /// 滚动效果  可以通过此参数 设置 ListView 不可滚动
    ScrollPhysics physics,
    /// 是否根据子控件的总长度来设置ListView的长度，默认值为false
    bool shrinkWrap = false,
    ///  padding
    EdgeInsetsGeometry padding,
    /// 子控件高度
    this.itemExtent,
    // 在 关闭屏幕时 是否释放子控件
    bool addAutomaticKeepAlives = true,
    /// 是否 避免列表项重绘
    bool addRepaintBoundaries = true,
    /// 该属性表示是否把子控件包装在IndexedSemantics里，用来提供无障碍语义
    bool addSemanticIndexes = true,
    // 预加载子控件的个数
    double cacheExtent,
    /// 子控件数组
    List<Widget> children = const <Widget>[],
    /// 子控件的个数
    int semanticChildCount,
    DragStartBehavior dragStartBehavior = DragStartBehavior.start,
    ScrollViewKeyboardDismissBehavior keyboardDismissBehavior = ScrollViewKeyboardDismissBehavior.manual,
})
```


#### builder 
`Flutter`给我们提供了四种构造`ListView`的方法，有`ListView()`、`ListView.builder()`、`ListView.separated()`、`ListView.custom()`、

|  构造函数   | 描述  |
|  ----  | ----  |
| ListView()  | 静态构造方法 初始化之前需要确定数据源的大小 |
| ListView.builder()  | 动态构造方法  可动态传入数据 |
| ListView.separated() | 动态构造方法  可动态传入数据 可动态定制分割线的样式 |
| ListView.custom()  |  动态构造方法 需要传入`SliverChildDelegate`来做动态生成 |

**静态构造方法和动态构造方法**
`ListView()`是初始化的时候需要确定数据源的大小，一旦初始化成功后不能再次动态的插入数据。
`ListView.builder()`、`ListView.separated()`、`ListView.custom()`可以动态的插入数据，且能够更小的节省内存空间。
我们来看以下代码：  
``` dart
Flexible(
    child: ListView(
        children: List.generate(
            10,
            (index) {
                print("without builder index = $index");
                return Container(
                height: 60,
                child: Card(
                        color: Colors.blue,
                        child: Center(child: Text("$index")),
                    ),
                );
            },
        ),
    ),
),
Flexible(
    child: ListView.builder(
        itemCount: 10,
        itemExtent: 60,
        itemBuilder: (BuildContext contenxt, int index) {
            print("builder index = $index");
            return Container(
                height: 60,
                child: Card(
                color: Colors.red,
                child: Center(child: Text("$index")),
                ),
            );
        },
    ),
),
```
同样是需要初始化10个子控件，我们分别在`List.generate`方法和`itemBuilder`方法中做了打印操作
输出如下：
``` dart
flutter: without builder index = 0
flutter: without builder index = 1
flutter: without builder index = 2
flutter: without builder index = 3
flutter: without builder index = 4
flutter: without builder index = 5
flutter: without builder index = 6
flutter: without builder index = 7
flutter: without builder index = 8
flutter: without builder index = 9
flutter: builder index = 0
flutter: builder index = 1
flutter: builder index = 2
flutter: builder index = 3
flutter: builder index = 4
flutter: builder index = 5
flutter: builder index = 6
flutter: builder index = 7
```
由输出的log可见，`builder`方法只初始化了7个子控件，`ListView()`方法完整的初始化了10个子控件。  
`builder`方法是**在需要使用的时候**才会初始化，当页面滚动到第9个子控件的时候，这个时候才会初始化第9个子控件。  
这样做的优势是：当我们的列表数据量很大的时候(比如说有成百上千个数据)，我们只初始化几个来满足页面的显示需求，其他的控件在需要的时候，再做初始化这样就大大的帮助我们节省内存空间。

#### scrollDirection
`ListView`同时具备了水平布局和垂直布局的能力，我们只需要给`scrollDirection`设置不同的参数即可。
`scrollDirection`接收的参数值有两个`Axis.vertical`和`Axis.horizontal`  
  
**Axis.vertical**  
效果如下  
![2021_01_16_listview_horizontal](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_16_listview_horizontal.jpg)

**Axis.horizontal**  
效果如下  
![2021_01_16_listview_vertical](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_16_listview_vertical.jpg)




#### reverse
参数`reverse`可以控制列表是按正序显示还是倒序显示。

**reverse = true**
表示倒序显示
![2021_01_16_listview_reverse_true](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_16_listview_reverse_true.png)

**reverse = false**
表示正序显示
![2021_01_16_listview_reverse_false](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_16_listview_reverse_false.png)

#### physics
某些情况下我们并不想要`ListView`可以滚动，只要把`physics`设置为`NeverScrollableScrollPhysics`即可。
`physics`还有其他两个比较重要的值：
`ClampingScrollPhysics`：在Android设备上有微光效果。
`BouncingScrollPhysics`：在iOS设备上有弹性效果。


#### separated
在`ListView.separated()`构造函数中，我们可以传入一个自定义的`Divider`来作作为分隔的样式
这里我们来看一下`Divider`都有哪些参数：
``` dart

const Divider({
    /// key
    Key key,
    // 高度
    this.height,
    /// 颜色的 高度
    this.thickness,
    /// 开头处的缩进
    this.indent,
    /// 结束处的缩进 
    this.endIndent,
    /// 颜色
    this.color,
})
```

**height = 0**  
![2021_01_16_listview_height_0](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_16_listview_height_0.jpg)

**height = 10**  
![2021_01_16_listview_height_10](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_16_listview_height_10.jpg)

**thinkness = 10**  
![2021_01_16_listview_thinkness_10](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_16_listview_thinkness_10.jpg)

**indent = 100**  
![2021_01_16_listview_indent_100](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_16_listview_indent_100.jpg)

**end = 100**  
![2021_01_16_listview_end_100](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_16_listview_end_100.jpg)



想体验以上示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`listview_page.dart`查看，并且可以下载下来运行并体验。

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
