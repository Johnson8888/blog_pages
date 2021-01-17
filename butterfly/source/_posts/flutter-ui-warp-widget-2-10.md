---
title: 【Flutter 2-10】Flutter手把手教程UI布局和Widget——流式布局Wrap
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-01-15 11:55:17
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter Column
  - Flutter 布局控件
  - Flutter Row
  - Flutter Flexible
  - Flutter Wrap
categories: Flutter
keywords: Flutter Column，Flutter Row，Flutter 布局控件， Flutter Flexible，Flutter Wrap
description: 在Flutter中Wrap是流式布局控件，Row和Column在布局上是很好用，但是有一个缺点，如果当子控件数量过多导致Row或Column装载不下的时候，就会出现UI页面上的错误。Wrap可以完美的避免这些问题，当控件过多一行显示不全的时候，Wrap可以换行显示。当然`Wrap`跟`Row`和`Column`有着很多相似的地方。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### Wrap 
在`Flutter`中`Wrap`是流式布局控件，`Row`和`Column`在布局上是很好用，但是有一个缺点，如果当子控件数量过多导致`Row`或`Column`装载不下的时候，就会出现UI页面上的错误。`Wrap`可以完美的避免这个问题，当控件过多一行显示不全的时候，`Wrap`可以换行显示。  

当然`Wrap`跟`Row`和`Column`有着很多相似的地方。
我们先来看`Wrap`的构造函数：
``` dart
Wrap({
    // Key
    Key key,
    // 子控件显示方向， 有垂直方向 水平方向两个值
    this.direction = Axis.horizontal,
    /// 子控件的 布局方式  跟Column的 mainAxisalignment类似 
    this.alignment = WrapAlignment.start,
    /// 子控件 主轴方向间距
    this.spacing = 0.0,
    /// 子控件 交叉方向的 布局方式
    this.runAlignment = WrapAlignment.start,
    /// 子控件 交叉方向间距
    this.runSpacing = 0.0,
    /// 交叉轴的对齐方式 与 Column 的crossAxisAlignment 一样
    this.crossAxisAlignment = WrapCrossAlignment.start,
    /// 书写方向 与 Column的 textDirection 一样
    this.textDirection,
    /// Wrap交叉轴方向上子控件的布局方向
    this.verticalDirection = VerticalDirection.down,
    /// 裁剪方式
    this.clipBehavior = Clip.hardEdge,
    /// 子控件
    List<Widget> children = const <Widget>[],
}) 
```
下面我们就来看看这些参数 
#### direction
`direction`有两个参数值`Axis.horizontal`和`Axis.vertical`，很明显它管理着`Wrap`的是水平布局还是垂直布局。
`Axis.horizontal`表示子控件按水平方向布局，`Axis.vertical`表示子控件按垂直方向布局显示。


**Axis.horizontal** 
效果如下：

![20202_01_15_wrap_horizontal](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/20202_01_15_wrap_horizontal.png)


**Axis.vertical**
效果如下：
![20202_01_15_wrap_vertical](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/20202_01_15_wrap_vertical.png)

#### alignment
`alignment`接收一个`WrapAlignment`类型的枚举，`WrapAlignment`共有六个枚举值，如下：
> `WrapAlignment`的枚举值与效果与 `Column` 的 `mainAxisAlignment`效果一样，想了解的可以看之前的[文章](https://juejin.cn/post/6916870555060666376)  

  
|  枚举值   | 描述  |
|  ----  | ----  |
| start  | 与 开始的位置对齐 |
| end  | 与 结束的位置对齐 |
| center | 居中对齐 |
| spaceBetween  |  把剩余的空间拆分成n-1份(n是子控件的个数) 每一份都插入到子控件之间  |
| spaceEvenly | 把剩余的空间拆分成n+1份(n是子控件的个数) 然后均匀分布 |
| spaceAround | 把剩余空间拆分成 2n 份(n是子控件的个数) 每个子控件上下各放一份 |  

**WrapAlignment.start**  
![20202_01_15_wrap_alignment_start](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/20202_01_15_wrap_alignment_start.jpg)

**WrapAlignment.center**  
![20202_01_15_wrap_alignment_center](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/20202_01_15_wrap_alignment_center.jpg)

**WrapAlignment.end**  
![20202_01_15_wrap_alignment_end](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/20202_01_15_wrap_alignment_end.jpg)


**WrapAlignment.spaceBetween**  
![20202_01_15_wrap_alignment_between](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/20202_01_15_wrap_alignment_between.jpg)  

**WrapAlignment.spaceEvenly**  
![20202_01_15_wrap_alignment_spaceEvenly](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/20202_01_15_wrap_alignment_spaceEvenly.jpg)  

**WrapAlignment.spaceAround**  
![20202_01_15_wrap_alignment_spaceAround](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/20202_01_15_wrap_alignment_spaceAround.jpg)  


### runAlignment
`runAlignment`接收一个`WrapAlignment`类型的枚举，`WrapAlignment`共有六个枚举值（跟`alignment`的枚举值是一样的），`runAlignment`控制是的是`Wrap`布局交叉方向的对齐方式。  
如果`Wrap`的是水平方向布局，`runAlignment`控制的就是`Wrap`垂直方向的对齐方式。


### verticalDirection
`verticalDirection`有两个值`VerticalDirection.down`和`VerticalDirection.up`，表示从哪个方向开始布局。  
**VerticalDirection.down**  
![2021_01_15_wrap_down](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_15_wrap_down.jpg)

**VerticalDirection.up**  
![2021_01_15_wrap_up](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_15_wrap_up.jpg)  

> 注意 当设置为`VerticalDirection.up`的时候，第一个控件也就是`Number 0`是从最低端最左侧开始的。  

### spacing 和 runSpacing  

`spacing`表示子控件主轴方向间距，`runSpacing`子控件在交叉方向间距。  
在一个水平方向布局的`Wrap`为中，`spacing`表示的就是水平方向子控件之间的间距，`runSpacing`表示的就是子控件在垂直方向上的间距。

**space**  
`space`等于`10`的样子  
![2021_01_15_wrap_space_10](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_15_wrap_space_10.jpg)

`space`等于`40`的样子  
![2021_01_15_wrap_space_40](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_15_wrap_space_40.jpg)
**runSpacing**  
`runSpacing`等于`10`的样子  
![2021_01_15_wrap_runSpace_10](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_15_wrap_runSpace_10.jpg)

`runSpacing`等于`40`的样子  
![2021_01_15_wrap_runSpace_40](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_01_15_wrap_runSpace_40.jpg)


想体验以上示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`wrap_page.dart`查看，并且可以下载下来运行并体验。

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
