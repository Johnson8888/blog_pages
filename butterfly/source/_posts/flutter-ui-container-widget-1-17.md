---
title: 【Flutter 1-16】Flutter手把手教程UI布局和Widget——容器控件Container
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-28 11:58:21
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter Container
  - Flutter 容器
  - Flutter 控件
categories: Flutter
keywords: Flutter 容器，Flutter 控件，Flutter Container
description: Container是一个相对复杂一些的控件，它有很多属性，初始化的时候传入多个参数来满足我们更多的UI需求。这是一个在布局中非常重要的控件。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)


### Container
我们先来看一下Container初始化的参数：
``` dart
  Container({
    Key key,
    // 位置 居左、居右、居中
    this.alignment, 
    // EdgeInsets Container的内边距
    this.padding,
    // 背景颜色  
    this.color,
    // 背景装饰器
    this.decoration,
    // 前景装饰器
    this.foregroundDecoration,
    // 宽度
    double width,
    // 告诉
    double height,
    // 约束
    BoxConstraints constraints,
    // EdgeInsets Container的外边距
    this.margin,
    // 旋转
    this.transform,
    // 子控件
    this.child,
    // 裁剪Widget的模式 
    this.clipBehavior = Clip.none,
  }) 
```

**注意：**

- `Container` 的`color`属性与属性 `decoration`的`color`存在冲突，如果两个`color`都做了设置，默认会以`decoration`的`color`为准。
- 如果我们没有给`Container`设置`width`和`height`，`Container`会跟`child`的大小一样；假如我们没有设置`child`的时候，它的尺寸会极大化，尽可能的充满它的`父Widget`。


**1. 最简单的Container**
``` dart
Container(
    child: Text("Fulade"),
    color: Colors.red,
)
```
Container接收一个`child`参数，我们可以传入`Text`作为`child`参数,然后传入是一个颜色。    
![2020_12_28_container_normal](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_28_container_normal.png)

**2. Padding**
``` dart
Container(
    child: Text("Pading 10"),
    padding: EdgeInsets.all(10),
    color: Colors.blue,
)
```  
`Padding`是内边距，我们在这里设置了`padding: EdgeInsets.all(10)`，也就是说`Text`距离`Container`的四条边的边距都是10。  
![2020_12_28_container_padding](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_28_container_padding.png)

**3. Margin**
``` dart
Container(
    child: Text("Margin 10"),
    margin: EdgeInsets.all(10),
    color: Colors.green,
)
```
`Margin`是外边距，我们在这里设置了`margin: EdgeInsets.all(10)`，`Container`在原有大小的基础上，又被**包围**了一层宽度为10的矩形。
需要注意，绿色外围的白色区域也是属于`Container`的一部分。
![2020_12_28_container_margin](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_28_container_margin.png)  

**4. transform**
``` dart
Container(
    padding: EdgeInsets.symmetric(horizontal: 15),
    margin: EdgeInsets.all(10),
    child: Text("transform"),
    transform: Matrix4.rotationZ(0.1),
    color: Colors.red,
)
```
`transform`可以帮助我们做旋转，`Matrix4`给我们提供了很多的变换样式。
![2020_12_28_container_transform](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_28_container_transform.png)


**5. decoration**
`decoration`可以帮助我们实现更多的效果。例如形状、圆角、边界、边界颜色等。
``` dart
Container(
    child: Text("Decoration"),
    padding: EdgeInsets.symmetric(horizontal: 15),
    margin: EdgeInsets.all(10),
    decoration: BoxDecoration(
        color: Colors.red,
        shape: BoxShape.rectangle,
        borderRadius: BorderRadius.all(Radius.circular(5)),
    ),
)
```
![2020_12_28_container_decoration](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_28_container_decoration.png)
这里就是设置了一个圆角的示例，同样我们对`BoxDecoration`的`color`属性设置颜色，对整个`Container`的也是有效的。

**6. 显示 Image**
``` dart
Container(
    height: 40,
    width: 100,
    margin: EdgeInsets.all(10),
    decoration: BoxDecoration(
        image: DecorationImage(
                image: AssetImage("images/flutter_icon_100.png"),
                fit: BoxFit.contain,
            ),
    ),
)
```
`BoxDecoration`可以传入一个`Image`对象，这样就灵活了很多，`Image`可以来自本地也可以来自网络。
![2020_12_28_container_image](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_28_container_image.png)


**7. Border**
``` dart
Container(
    child: Text('BoxDecoration with border'),
    padding: EdgeInsets.symmetric(horizontal: 15),
    margin: EdgeInsets.all(5),
    decoration: BoxDecoration(
        borderRadius: BorderRadius.circula(12),
        border: Border.all(
            color: Colors.red,
            width: 3,
        ),
    ),
)
```
使用`border`可以帮助我们做边界效果，还可以设置圆角`borderRadius`，也可以设置`border`的宽度，颜色等。
![2020_12_28_container_border](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_28_container_border.png)

**8. 渐变色**

``` dart
Container(
    padding: EdgeInsets.symmetric(horizontal: 20),
    margin: EdgeInsets.all(20), //容器外填充
    decoration: BoxDecoration(
        gradient: RadialGradient(
            colors: [Colors.blue, Colors.black, Colors.red],
            center: Alignment.center,
            radius: 5
        ),
    ),
    child: Text(
        //卡片文字
        "RadialGradient",
        style: TextStyle(color: Colors.white),
    ),
)
```
`BoxDecoration`的属性`gradient`可以接收一个颜色的数组，`Alignment.center`是渐变色开始的位置，可以从`左上角`、`右上角`、`中间`等位置开始颜色变化。

![2020_12_28_container_radialGradient](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_28_container_radialGradient.png)


想体验以上的`Container`的示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`container_page.dart`查看，并且可以下载下来运行并体验。

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
