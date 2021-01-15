---
title: 【Flutter 2-9】Flutter手把手教程UI布局和Widget——弹性布局控件Flexible
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-01-14 11:28:29
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter Column
  - Flutter 布局控件
  - Flutter Row
  - Flutter Flexible
categories: Flutter
keywords: Flutter Column，Flutter Row，Flutter 布局控件， Flutter Flexible 
description: Flexible可以帮助Row、Column、Flex的子控件充满父控件，它的用法很灵活，也具有权重的属性。跟Flexible相类似的控件还有Expanded。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### Flexible
Flexible可以帮助Row、Column、Flex的子控件充满父控件，它的用法很灵活，也具有权重的属性。跟Flexible相类似的控件还有Expanded。
先来看`Flexible`的构造函数
``` dart
const Flexible({
    /// key
    Key key,
    // 默认 flex 的值为 1
    this.flex = 1,
    /// 默认 fit参数为 FlexFit.loose 表示子控件可以以最小的大小来布局
    this.fit = FlexFit.loose,
    @required Widget child,
}) 
```

#### 按比例布局  
`Flexible`的参数`flex`是表示比例的值。  
假如我们在`Column`内部有三个子控件，每个控件的`flex`值都设置为`1`
那么这三个子控件的高度都是`Column`高度(Row的情况下就是宽度)的三分之一，也就是三个子控件均分了`Column`的高度(Row的情况下就是宽度)  
``` dart
Column(
    crossAxisAlignment: CrossAxisAlignment.center,
    children: [
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 1,
        ),
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 1,
        ),
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 1,
        ),
    ],
)
```
如下图：  
![2020_01_14_flexible_1_1_1](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_14_flexible_1_1_1.png)

然后我们把`flex`的值分别设置为`1`、`2`、`3`，那么这个三个控件的高度分别是五分之一、五分之二、五分之三的高度  
``` dart
Column(
    crossAxisAlignment: CrossAxisAlignment.center,
    children: [
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 1,
        ),
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 2,
        ),
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 3,
        ),
    ],
)
```
效果如下图：
![2020_01_14_flexible_1_2_3](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_14_flexible_1_2_3.png)


#### FlexFit.loose 和 FlexFit.tight
|  枚举值   | 描述  |
|  ----  | ----  |
| loose  | loose表示允许以最小的高度(Row下是宽度)布局 可以忽略flex的值 |
| tight  | 必须以设置的最大的flex值来显示 |
``` dart
Column(
    crossAxisAlignment: CrossAxisAlignment.center,
    children: [
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 1,
        ),
        Flexible(
            child: Image.asset(
            "images/image_demo.jpg",
            height: 80,
            ),
            fit: FlexFit.loose,
            flex: 2,
        ),
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 2,
        ),
    ],
)
```
我们给第二个控件设置的`flex`值为2，给`Image`设置的高度为`80`，给`fit`的值设置为`FlexFit.loose`，这个时候优先起到作用的是`FlexFit.loose`，`flex`的值会被忽略，所以这里的`Image`会以高度为`80`的大小来显示。
效果如下图：  
![2020_01_14_flexible_loose](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_14_flexible_loose.png)

``` dart
Column(
    crossAxisAlignment: CrossAxisAlignment.center,
    children: [
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 1,
        ),
        Flexible(
            child: Image.asset(
            "images/image_demo.jpg",
            height: 80,
            ),
            fit: FlexFit.tight,
            flex: 2,
        ),
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 2,
        ),
    ],
)
```

我们把`FlexFit.loose`改为`FlexFit.tight`，此时就会忽略当前设置的高度`80`，直接使用比例来显示。
效果如下图：  
![2020_01_14_flexible_tight](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_14_flexible_tight.png)


#### 优先布局
如果我们将`flex`的值设置为0，此时`Flexible`并不是被分配0的高度，而是`flex`值为0的`Flexible`会优先布局且会尽量大的占用`Column`的高度
``` dart
Column(
    children: [
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 1,
        ),
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 2,
        ),
        Flexible(
            child: Image.asset("images/image_demo.jpg"),
            flex: 0,
        ),
    ],
)
```
![2020_01_14_flexible_flex_00](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_14_flexible_flex_00.png)
可以看到第三个`Flexible`是高度最大的，因为它优先占用最高的高度。

#### 填充剩余的空间
很多情况下在`Column`内不止是有`Flexible`控件，还有像`Container`这种控件。在二者都存在的情况下，`Container`会优先布局并占用自己需要的高度，剩余的高度由`Flexible`控件来填充满。如果有多个`Flexible`控件，它们会按自己设置的`flex`值来均分剩余的高度。
``` dart
Column(
    children: [
        Container(
            child: Image.asset("images/image_demo.jpg"),
            width: 100,
            height: 100,
        ),
        Container(
            child: Image.asset("images/image_demo.jpg"),
            width: 100,
            height: 100,
        ),
        Flexible(
            child: Container(
                decoration: BoxDecoration(color: Colors.green),
                width: 300,
            ),
        ),
    ],
)
```
效果如下：  
![2020_01_14_flexible_flex_space_full](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_14_flexible_flex_space_full.png)

想体验以上示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`flexible_page.dart`查看，并且可以下载下来运行并体验。
