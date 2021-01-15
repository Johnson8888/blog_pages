---
title: 【Flutter 2-7】Flutter手把手教程UI布局和Widget——垂直布局控件Column
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-01-12 16:30:21
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter Column
  - Flutter 布局控件
  - Flutter Row
categories: Flutter
keywords: Flutter Column，Flutter Row，Flutter 布局控件  
description: Column 是在Flutter中常见的布局控件，它负责垂直方向布局。Row负责水平方向布局，二者都是继承于`Flex`，类似于`iOS`里面的`UIScrollView`，但是又有很多不同。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)


### Column
`Column`是在Flutter中常见的布局控件，它负责垂直方向布局。Row负责水平方向布局，二者都是继承于`Flex`，类似于`iOS`里面的`UIScrollView`，但是又有很多不同。
先来看一下`Column`的构造函数
``` dart
Column({
    /// key
    Key key,
    /// Column的对其方式 默认是 MainAxisAlignment.start
    MainAxisAlignment mainAxisAlignment = MainAxisAlignment.start,
    /// 表示Column在垂直方向占用的大小，默认是 max，表示尽可能的充满垂直方向空间。如果这是 min表示尽量小的占用垂直方向空间
    MainAxisSize mainAxisSize = MainAxisSize.max,
    /// 横轴对其方式 默认是 居中对齐
    CrossAxisAlignment crossAxisAlignment = CrossAxisAlignment.center,
    /// 子控件的布局顺序，不同国家书写习惯的不同(中文、英语从左往右书写，阿拉伯文从右往左书写)，这个参数可以帮助我们调整布局显示顺序
    TextDirection textDirection,
    /// 表示垂直方向的对其方向 
    VerticalDirection verticalDirection = VerticalDirection.down,
    /// 基线对齐方式 在Row里面会有使用
    TextBaseline textBaseline,
    /// 子控件
    List<Widget> children = const <Widget>[],
}) 
```

### mainAxisAlignment
`mainAxisAlignment`接收一个`MainAxisAlignment`类型的枚举，`MainAxisAlignment`共有六个枚举值，如下：
|  枚举值   | 描述  |
|  ----  | ----  |
| start  | 与 开始的位置对齐 |
| end  | 与 结束的位置对齐 |
| center | 居中对齐 |
| spaceBetween  |  把剩余的空间拆分成n-1份(n是子控件的个数) 每一份都插入到子控件之间  |
| spaceEvenly | 把剩余的空间拆分成n+1份(n是子控件的个数) 然后均匀分布 |
| spaceAround | 把剩余空间拆分成 2n 份(n是子控件的个数) 每个子控件上下各放一份 |
看描述比较晦涩，我们直接来看效果：

**MainAxisAlignment.start**
居顶部
![2020_01_12_column_mainaxisalignment_start_1](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_mainaxisalignment_start_1.png)

**MainAxisAlignment.center**
居中间
![2020_01_12_column_mainaxisalignment_center](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_mainaxisalignment_center.png)

**MainAxisAlignment.end**
居底部
![2020_01_12_column_mainaxisalignment_end](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_mainaxisalignment_end.png)



**MainAxisAlignment.spaceBetween**
把剩余的空间拆分成n-1份(n是子控件的个数)，这里也就是3分，每一份都插入到子控件之间。看绿色数字就是每一份的编号
![2020_01_12_column_mainaxisalignment_specebtween](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_mainaxisalignment_specebtween.png)

**MainAxisAlignment.spaceEvenly**

把剩余的空间拆分成n+1份(n是子控件的个数)，这里也就是5分， 然后均匀分布。
![2020_01_12_column_mainaxisalignment_speceevenly](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_mainaxisalignment_speceevenly.png)


**MainAxisAlignment.spaceAround**
把剩余空间拆分成 2n 份(n是子控件的个数)，这里也就是8分，每个子控件上下各放一份
![2020_01_12_column_mainaxisalignment_specearound](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_mainaxisalignment_specearound.png)


### crossAxisAlignment
`crossAxisAlignment`接收一个`CrossAxisAlignment`枚举值，有以下5中枚举

|  枚举值   | 描述  |
|  ----  | ----  |
| start  | 与 开始的位置对齐 |
| end  | 与 结束的位置对齐 |
| center | 居中对齐 |
| stretch  |  水平方向扩充与Column相同大小  |
| baseline | 无效 |

**CrossAxisAlignment.start**
居左侧
![2020_01_12_column_crossaxisalignment_start](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_crossaxisalignment_start.png)

**CrossAxisAlignment.center**
居中
![2020_01_12_column_crossaxisalignment_center](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_crossaxisalignment_center.png)
**CrossAxisAlignment.end**
居右侧
![2020_01_12_column_crossaxisalignment_end](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_crossaxisalignment_end.png)


**CrossAxisAlignment.stretch**
子控件的宽度拉伸到与`Column`相同大小
![2020_01_12_column_crossaxisalignment_stretch](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_crossaxisalignment_stretch.png)

### textDirection
`textDirection`参数接收一个`TextDirection`类型的枚举类型，它有两个不同的枚举值，如下
|  枚举值   | 描述  |
|  ----  | ----  |
| rtl  | 书写习惯是从右边开始  子控件默认从右边对齐 |
| ltr  | 书写习惯是从左边开始  子控件默认从左边对齐 |
`crossAxisAlignment`参数会受到`textDirection`参数值影响。
如下：  

- 当 `textDirection`的参数值为`ltr`时，`crossAxisAlignment`参数为`CrossAxisAlignment.start`这个时候子控件居左对齐。
![2020_01_12_column_ltr_start](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_ltr_start.png)


- 当 `textDirection`的参数值为`ltr`时，`crossAxisAlignment`参数为`CrossAxisAlignment.end`这个时候子控件居右对齐。

![2020_01_12_column_ltr_end](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_ltr_end.png)



- 当 `textDirection`的参数值为`rtl`时，`crossAxisAlignment`参数为`CrossAxisAlignment.start`这个时候子控件居右对齐。

![2020_01_12_column_rtl_start](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_rtl_start.png)

- 当 `textDirection`的参数值为`rtl`时，`crossAxisAlignment`参数为`CrossAxisAlignment.end`这个时候子控件居做对齐。

![2020_01_12_column_rtl_end](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_12_column_rtl_end.png)

总的来说`textDirection`会控制书写习惯来改变布局。这个其实是在做国际化的时候用到的比较多。在下一节即将讲解的`Row`也相同的会收到影响。

>在上面的描述中有`开始的位置`和`结束的位置`，为什么不直接写`左边`或`右边`，其实也是受`textDirection`的影响，`开始的位置`就是书写开始的位置，`结束的位置`就是写结束的位置。

想体验以上的`Column`的示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`column_page.dart`查看，并且可以下载下来运行并体验。


***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)







