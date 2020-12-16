---
title: 【Flutter 1-15】Flutter手把手教程UI布局和Widget——文本和样式 Text Widget，
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-15 20:09:03
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter 文本
  - Flutter 文本样式
  - Flutter Text
  - Flutter Text Widget 
categories: Flutter
keywords: Flutter 文本，Flutter文本样式，Flutter Text，Flutter Text Widget
description: Text是我们日常开发中最常见的控件了，几乎所有的文字显示我们都会用到Text控件。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### Text 
我们先来看Text的构造函数都有哪些参数：
``` dart
const Text( 
    this.data, { 
    //data 就是我们需要展示的文字 是字符串类型，这个是必传字段，其他的都是可选
    Key key,    
    //widget的标识
    this.style, 
    //文本样式，类型是TextStyle
    this.strutStyle, 
    //用来设置最小行高的参数
    this.textAlign, 
    //文本的对齐方式，类型是TextAlign
    this.textDirection, 
    // 文字方向，类型是TextDirection
    this.locale, 
    //选择用户语言和格式的标识符，类型是Locale，主要用于国际化
    this.softWrap, 
    //bool 类型 ，false标识文本只有一行，水平方向无限
    this.overflow, 
    //超出显示区域后的展示方式，类型是TextOverflow
    this.textScaleFactor,
    //double类型 表示文本相对于当前字体的缩放系数，默认为1.0
    this.maxLines,
    // int 类型，显示的最大行数
    this.semanticsLabel, 
    //String 类型，给文本加上一个语义标签
    this.textWidthBasis,
    //一行或多行文本宽度的不同方式，类型是TextWidthBasis
  }) 
```
`Text`我们重点介绍下面几个参数:`data`、`style`、`textAlign`、`maxLines`、`overflow`。
**1. 最简单的示例**
``` dart
  Text("Fulade");
```
**2. 放大和缩小**
``` dart
Text("文字放大1.5倍",textScaleFactor: 1.5);
```
`textScaleFactor`是缩放参数，默认是`1.0`，设置小于1的参数是缩小，设置大约1的参数是放大。
**3. 居中、居左和居右**
``` dart
Text(
  "居右显示" * 10,
  textAlign: TextAlign.right,
);
```
`textAlign`是位置参数，常见的枚举值有`TextAlign.right`、`TextAlign.left`和`TextAlign.center`。
**4. 单行显示**
``` dart
Text(
  "最多一行显示超过部分显示..." * 10,
  maxLines: 1,
  overflow: TextOverflow.ellipsis,
);
```
`maxLines`表示文字需要几行来显示，如果超过了要显示的行数，文字会被切断。使用`overflow`来设置切断文字的样式，`overflow`有以下几个枚举值：
``` dart
enum TextOverflow {
  clip,      //直接裁剪。
  fade,      // 渐变淡出
  ellipsis,  // 以省略号的方式
  visible,   // 依然显示，此时将会溢出父组件
}
```
如果我们不设置`maxLines`，文字默认会换行，以全部都展示的方式来显示。  

以上四种样式效果如下：
![2020_11_16_text](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_16_text.png)

### TextStyle
如果想要设置更复杂的文字样式，我们需要传入`Text`的`style`参数，`style`参数接收一个 `TextStyle`的对象，`TextStyle`可以帮助我们做很多事情。

**5. 粗体**
``` dart
Text(
  "粗体",
  style: TextStyle(fontWeight: FontWeight.bold),
)
```
`fontWeight`用来设置粗体。`FontWeight.bold`默认是`w700`。
**6. 颜色**
``` dart
Text(
  "红色",
  style: TextStyle(color: Colors.red),
)
```
`color`参数用来设置颜色。
**7. 字号**
``` dart
Text(
  "字号20",
  style: TextStyle(fontSize: 20),
)
```
`fontSize`用来设置字号。
**8. 斜体**
``` dart
Text(
  "斜体",
  style: TextStyle(fontStyle: FontStyle.italic),
)
```
`fontStyle`可以用来设置斜体，`FontStyle.italic`表示斜体，默认是`FontStyle.normal`。

**9. 背景颜色**
``` dart
Text(
  "背景颜色红色",
  style: TextStyle(
      background: Paint()..color = Colors.red,
      color: Colors.blue),
)
```
`background`用来设置背景颜色，它接收一个`Paint`对象作为参数，`Paint`对象可以设置`color`属性。
**10. 删除线**
``` dart
Text(
  "删除线",
  style: TextStyle(
      decoration: TextDecoration.lineThrough,
      decorationColor: Colors.red),
)
```
`decorationColor`参数是设置删除线的颜色，`TextDecoration.lineThrough`是删除线的样式。
**11. 下划线**
``` dart
Text(
  "下划线",
  style: TextStyle(
    decoration: TextDecoration.underline,
  ),
);
```
下划线的设置跟**删除线**的设置基本一样，只是枚举值不同，下划线使用的是`TextDecoration.underline`枚举。

以上几种样式展示效果如下：
![2020_11_16_text_span](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_16_text_span.png)
### RichText 和 TextSpan
Flutter支持在一行文字里面显示不同颜色的文字，这里我们需要用到`RichText`和 `TextSpan`。

**12. 多彩文字**
``` dart
RichText(
  text: TextSpan(
    textAlign: TextAlign.center,
    text: "多彩文字：",
    style: TextStyle(color: Colors.black),
    children: <TextSpan>[
      TextSpan(
          text: "红色、", style: TextStyle(color: Colors.red)),
      TextSpan(
          text: "蓝色、", style: TextStyle(color: Colors.blue)),
      TextSpan(
          text: "绿色 ", style: TextStyle(color: Colors.green)),
    ],
  ),
);
```
`TextSpan`的参数`children`，可以是一个`TextSpan`对象的数组，这就比较有意思。每一个`TextSpan`都可以设置颜色和字体，这样我们就可以组合成一个多彩的文字结构。同样`RichText`也有`textAlign`参数，它是整个文字的位置参数。


**13. 给文字添加点击事件**
``` dart
RichText(
  text: TextSpan(
    text: "添加了手势的文字: ",
    style: TextStyle(color: Colors.black),
    children: <TextSpan>[
      TextSpan(
        text: "点击会输出Log",
        style: TextStyle(color: Colors.blue),
        recognizer: TapGestureRecognizer()
          ..onTap = () {
            tapCount++;
            print("taped taped " + tapCount.toString());
          },
      ),
    ],
  ),
);
```
`TextSpan`可以给相应的文字添加手势，这样就可以满足我们点击某个文字触发事件的需求，这在日常开发中非常有效。我们就不需要搞一些"文字+按钮+文字+..."的这种组合了。  
`TextSpan`的参数`recognizer`可以接收一个手势参数，当然这里的手势不仅有**点击手势**，还有滑动手势等等(具体的手势功能我们后面会讲到)。多种手势更是满足了我们更多的交互需求。  

多彩文字和点击时间如下图：
![2020_11_16_text_tap](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_16_text_tap.png)

想体验点击事件效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目里`flutter_app`->`lib`->`routes`->`text_page.dart`运行查看。

### DefaultTextStyle
`DefaultTextStyle`是一个特殊的TextStyle。在`DefaultTextStyle`下面的所有子元素的文本样式都继承了`DefaultTextStyle`设置的文本样式。因此，我们只需要定义一个`DefaultTextStyle`，其下的所有文本样式都是该定义好的`DefaultTextStyle`的样式。这样就极大的方便我们来写一些统一的样式，而不需要每次都要写繁琐的设置样式的代码。

``` dart
DefaultTextStyle(
  // 设置文本默认样式
  style: TextStyle(
    color: Colors.red,
    fontSize: 20.0,
  ),
  textAlign: TextAlign.start,
  child: Column(
    crossAxisAlignment: CrossAxisAlignment.start,
    children: <Widget>[
      Text("DefaultTextStyle "),
      Text("DefaultTextStyle"),
      Text(
        "改变了的DefaultTextStyle",
        style: TextStyle(
            inherit: false, // 设置不再继承默认样式
            color: Colors.blue),
      ),
    ],
  ),
);
```
首先我们声明了一个`DefaultTextStyle`的样式，它是红色的，字号是20。
注意:这里有一个`Text`的`inherit`设置了`false`，只有设置了`false`才允许不继承`DefaultTextStyle`的样式。而其他的两个`Text`对象，默认使用了`DefaultTextStyle`的样式。  

效果如下：

![2020_11_16_default_text](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_16_default_text.png)


---
以上所有的代码都在[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目里`flutter_app`->`lib`->`routes`->`text_page.dart`里面，你可以下载下来运行并体验。

运行效果图如下：  

![2020_11_16_screen](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_16_screen.png)

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)