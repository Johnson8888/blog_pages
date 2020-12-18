---
title: 【Flutter 1-17】Flutter手把手教程UI控件——【多图预警】按钮RaisedButton、FlatButton、OutlineButton、IconButton
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-16 20:38:22
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
    - Flutter 按钮
    - Flutter RaiseButton
    - FlatButton
    - OutlineButton
    - IconButton 
categories: Flutter 
keywords: Flutter 按钮,Flutter RaiseButton,FlatButton,OutlineButton,IconButton
description: 详解Flutter中的按钮事件和按钮样式，RaisedButton、FlatButton、OutlineButton,IconButton
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

Material 风格中常用的按钮有三种`RaiseButton`、`FlatButton`、`OutlineButton`。
这三种按钮都是继承了`MaterialButton`，而`MaterialButton`又继承自`StatelessWidget`。

RaiseButton：**带有阴影效果的按钮，默认带有灰色背景，点击下去会有点击效果和阴影。**
FlatButton: **扁平风格按钮，点击下去会有背景颜色。**
OutlineButton: **带有边框的按钮，且边框会在点击时改变颜色。**

### 1. RaisedButton
我们先来看`RaisedButton`的构造方法
``` dart
  const RaisedButton({
    Key key,
    /// 点击后的回调方法
    @required VoidCallback onPressed,
    /// 长按后的回调方法
    VoidCallback onLongPress,
    /// 高亮时候的回调方法
    ValueChanged<bool> onHighlightChanged,
    /// 鼠标指针的光标进入或悬停在此按钮(这个用于Web端或PC端)
    MouseCursor mouseCursor,
    /// 文本的主题，这个跟MaterialApp的属性theme有关
    ButtonTextTheme textTheme,
    /// 文本颜色
    Color textColor,
    /// 不可点击时的文本颜色
    Color disabledTextColor,
    /// 背景颜色
    Color color,
    /// 可点击时的背景颜色
    Color disabledColor,
    /// 获取焦点时的颜色(用于Web端或PC端)
    Color focusColor,
    /// 指鼠标悬停时的颜色(用于Web端或PC端)
    Color hoverColor,
    /// 高亮时的颜色
    Color highlightColor,
    /// 水波纹颜色，按下松开会有水波纹效果
    Color splashColor,
    /// 按钮主题颜色，默认浅色
    Brightness colorBrightness,
    /// 默认时的 阴影大小
    double elevation,
    /// 选中时的 阴影大小
    double focusElevation,
    /// 指鼠标悬停时的阴影大小
    double hoverElevation,
    /// 高亮时的阴影大小
    double highlightElevation,
    /// 不可选中时的阴影大小
    double disabledElevation,
    /// 内边距 跟布局有关
    EdgeInsetsGeometry padding,
    VisualDensity visualDensity,
    /// 设置按钮的形状
    ShapeBorder shape,
    /// 切边的样式
    Clip clipBehavior = Clip.none,
    FocusNode focusNode,
    bool autofocus = false,
    MaterialTapTargetSize materialTapTargetSize,
    /// 动画的时间
    Duration animationDuration,
    /// 子控件
    Widget child,
  }) 
```
**1.1 一个最简单的RaisedButton**
``` dart
RaisedButton(
    child: Text("RaisedButton"),
    onPressed: () {},
);
````
效果: 
![2020_12_17_rased_button_tap](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_17_rased_button_tap.gif)

**1.2 不可点击状态**
``` dart
RaisedButton(
    child: Text("不设置onPressed"),
    disabledColor: Colors.blue,
    disabledTextColor: Colors.red,
);
```
如果不设置`onPressed`参数，默认是不可点击的，当然我们依然可以设置不可点击时候的文字颜色和背景颜色。需要注意`onPressed`是`@required`参数，不建议不传此参数。
![2020_12_17_rased_button_no_onpressed](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_17_rased_button_no_onpressed.png)
**1.3 文本颜色**
``` dart
RaisedButton(
    child: Text("textColor红色"),
    textColor: Colors.red,
    onPressed: () {},
);
```
`textColor`可以设置文字的颜色。
![2020_12_17_rased_button_text_color](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_17_rased_button_text_color.png)

**1.4 设置形状**
``` dart
RaisedButton(
    onPressed: () {},
    child: Text("椭圆形"),
    shape: StadiumBorder(),
);
```
通过`shape`参数可以设置按钮的形状，常见的形状有`RoundedRectangleBorder`矩形、`CircleBorder`圆形、`StadiumBorder`椭圆形、`BeveledRectangleBorder`八边形。
![2020_12_17_rased_button_shape](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_17_rased_button_shape.png)

**1.5 背景颜色**
```dart
RaisedButton(
    child: Text("背景颜色"),
    color: Colors.red,
    onPressed: () {},
);
```
通过传入`color`可以设置按钮的背景颜色。
![2020_12_17_rased_button_back_color](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_17_rased_button_back_color.png)

**1.6 高亮颜色**
``` dart
RaisedButton(
    onPressed: () {},
    child: Text("高亮红色"),
    highlightColor: Colors.red,
);
```
传入`highlightColor`参数来设置选中时候的颜色。
![2020_12_17_rased_button_height_color](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_17_rased_button_height_color.gif)

**1.7 水波纹红色**
``` dart
RaisedButton(
    onPressed: () {},
    child: Text("水波纹红色"),
    splashColor: Colors.red,
);
```
`splashColor`可以帮助我们设置点击后的水波纹颜色。
![2020_12_17_rased_button_splash_color](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_17_rased_button_splash_color.gif)
**1.8 高亮回调**
```dart
RaisedButton(
    child: Text("高亮变化回调"),
    onPressed: () {},
    onHighlightChanged: (value) {
        print("高亮切换");
    },
);
```
`onHighlightChanged`可以接收一个回调方法，当按钮被按下并高亮的时候会回调该方法。
**1.9 长按回调**
``` dart
RaisedButton(
    child: Text("长按回调"),
    onPressed: () {},
    onLongPress: () {
        print("长按回调");
    },
);
```
`onLongPress`可以接收一个长按回调方法，当按钮被长按的时候会回调该方法。

**1.10 设置阴影的大小**
```dart
RaisedButton(
    child: Text("阴影设置20"),
    onPressed: () {},
    elevation: 20.0,
);
```
`elevation`参数可以设置阴影的大小，默认的阴影比较小，可以通过此参数设置更大的阴影大小。
![2020_12_17_rased_button_elevation](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_17_rased_button_elevation.png)

想体验以上代码运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`flat_button_page.dart`，可以下载下来运行并体验。

### 2. FlatButton
`FlatButton`的构造函数参数跟`RaisedButton`参数基本一致，设置方式也是一样的。
```dart
  const FlatButton({
    Key key,
    /// 点击后的回调
    @required VoidCallback onPressed,
    /// 长按后的回调
    VoidCallback onLongPress,
    /// 点击 高亮后的回调
    ValueChanged<bool> onHighlightChanged,
    /// 鼠标指针的光标进入或悬停在此按钮(这个用于Web端或PC端)
    MouseCursor mouseCursor,
    /// 文本的主题，这个跟MaterialApp的属性theme有关
    ButtonTextTheme textTheme,
    /// 文字颜色
    Color textColor,
    /// 不可点击时的文本颜色
    Color disabledTextColor,
    /// 背景颜色
    Color color,
    /// 不可点击时的背景颜色
    Color disabledColor,
    /// 获取焦点时的颜色(用于Web端或PC端)
    Color focusColor,
    /// 指鼠标悬停时的颜色(用于Web端或PC端)
    Color hoverColor,
    /// 高亮时的颜色
    Color highlightColor,
    /// 水波纹颜色，按下松开会有水波纹效果
    Color splashColor,
    /// 按钮主题颜色，默认浅色
    Brightness colorBrightness,
    /// 内边距 跟布局有关
    EdgeInsetsGeometry padding,
    VisualDensity visualDensity,
    /// 按钮的形状
    ShapeBorder shape,
    /// 切边的样式
    Clip clipBehavior = Clip.none,
    FocusNode focusNode,
    bool autofocus = false,
    MaterialTapTargetSize materialTapTargetSize,
    /// 子控件
    @required Widget child,
  })
```
**2.1 一个最简单的FlatButton**
``` dart
FlatButton(
    child: Text("FlatButton"),
    onPressed: () {},
);
```
![2020_12_17_flat_button_normal](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_17_flat_button_normal.gif)
我们可以看到相对比于`RaisedButton`，`FlatButton`默认扁平化风格的。

**2.2 设置形状**
``` dart
FlatButton(
    onPressed: () {},   
    child: Text("椭圆形"),
    shape: StadiumBorder(),
);
```
通过传入`shape`参数可设置`FlatButton`的形状。需要注意的是：设置好的形状，只有当点击下去的时候才可以看到效果。
![2020_12_17_flat_button_shape](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_17_flat_button_shape.gif)
其他的 **不可点击状态、文本颜色、背景颜色、高亮颜色、水波纹红色、高亮回调、长按回调**等状态的设置代码跟`RaisedButton`的设置方式一样。    

想体验`FlatButton`的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`flat_button_page.dart`，可以下载下来运行并体验。

### 3. OutlineButton
我们来看`OutlineButton`的构造函数
``` dart
const OutlineButton({
    Key key,
    /// 点击后的回调
    @required VoidCallback onPressed,
    /// 长按后的回调
    VoidCallback onLongPress,
    /// 鼠标指针的光标进入或悬停在此按钮(这个用于Web端或PC端)
    MouseCursor mouseCursor,
    /// 文本的主题，这个跟MaterialApp的属性theme有关
    ButtonTextTheme textTheme,
    /// 文字颜色
    Color textColor,
    /// 不可点击时的文本颜色
    Color disabledTextColor,
    /// 背景颜色
    Color color,
    /// 获取焦点时的颜色(用于Web端或PC端)
    Color focusColor,
    /// 指鼠标悬停时的颜色(用于Web端或PC端)
    Color hoverColor,
    /// 高亮时的颜色
    Color highlightColor,
    /// 水波纹颜色，按下松开会有水波纹效果
    Color splashColor,
     /// 高亮时的阴影大小
    double highlightElevation,
    /// 边框的延时
    this.borderSide,
    /// 不可用时 边框的颜色
    this.disabledBorderColor,
    /// 选中时边框的样色
    this.highlightedBorderColor,
    /// 内边距 跟布局有关
    EdgeInsetsGeometry padding,
    VisualDensity visualDensity,
    /// 按钮的形状
    ShapeBorder shape,
    /// 切边的样式
    Clip clipBehavior = Clip.none,
    FocusNode focusNode,
    bool autofocus = false,
    /// 子控件
    Widget child,
  })
```
**3.1 简单的 OutlineButton**
``` dart
OutlineButton(
    onPressed: () {},
    child: Text("OutlineButton"),
);
```
它的边框默认是灰色的，点击选中的时候会变为蓝色。
![2020_12_17_outline_button_normal](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_17_outline_button_normal.gif)
**3.2 Border的样式**
``` dart
OutlineButton(
    child: Text("Border颜色"),
    borderSide: BorderSide(color: Colors.red, width: 2),
    highlightColor: Colors.yellow,
    highlightedBorderColor: Colors.green,
    onPressed: () {},
);
```
`borderSide`可以接收一个`BorderSide`的对象，该对象可以设置颜色和宽度，同样我们也可以通过设置`highlightColor`和`highlightedBorderColor`来设置选中的背景颜色和选中的边框颜色。

![2020_12_17_outline_button_border](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_17_outline_button_border.gif)

其他的 **不可点击状态、文本颜色、高亮颜色、水波纹红色、高亮回调、长按回调**等状态的设置代码跟`RaisedButton`的设置方式一样。    


想体验`FlatButton`的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`outline_button_page.dart`，可以下载下来运行并体验。

### 4. IconButton
**4.1 简单的IconButton**
```dart
IconButton(
    icon: Icon(Icons.local_taxi),
    onPressed: () {},
);
```


`IconButton`可以接收一个`Icon`类的的参数，Flutter自带了很多`Icon`详情可见[这里](https://material.io/resources/icons/?style=baseline)
**4.1 带有选中提示的IconButton**
```dart
IconButton(
    icon: Icon(Icons.local_cafe),
    tooltip: "Cafe Button",
    color: Colors.red,
    onPressed: () {},
);
```
通过设置`tooltip`属性，可以设置按钮按下的弹出提示文字。我们这里设置了`Cafe Button`的文字。
![2020_12_18_icon_button_tool](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_18_icon_button_tool.gif)

**4.2 自定义图片的IconButton**
```dart
IconButton(
    icon: Image.asset("images/flutter_icon_100.png"),
    onPressed: () {},
);
```
我们同样可以提供一个`Image`类型的`Icon`，这样就满足我们设置不同的图片按钮。
如下图：
![2020_12_18_icon_button_image](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_18_icon_button_image.png)


想体验`IconButton`的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`icon_button_page.dart`，可以下载下来运行并体验。


以上就是Material风格的按钮以及详解，如果你想了解Cupertino风格按钮，可以点击[这里](https://api.flutter.dev/flutter/cupertino/cupertino-library.html)。
我们日常开发中大多数情况下都会使用Material风格的样式。


***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)