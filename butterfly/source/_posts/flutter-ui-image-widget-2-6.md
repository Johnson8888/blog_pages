---
title: 【Flutter 2-6】Flutter手把手教程UI布局和Widget——Image控件、NetworkImage、AssetImage
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-01-10 10:20:57
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter Image
  - Flutter NetworkImage
  - Flutter AssetImage
categories: Flutter
keywords: Flutter 容器，Flutter 控件，Flutter Container
description: Image是一个常用的控件，它可以帮助我们显示图片，图片的资源可以是来自网络、本地或者是内存。在移动端的开发中会大量的使用Image来展示一些图文，了解和掌握Image控件是非常有必要的。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)



Image是一个常用的控件，它可以帮助我们显示图片，图片的资源可以是来自网络、本地或者是内存。在移动端的开发中会大量使用Image来展示一些图文，了解和掌握Image控件是非常有必要的。

### AssetImage 和 Image.asset
`AssetImage`是Flutter提供的一个可以从本地读取图片资源的类，我们可以使用它来读取图片。同样Flutter还提供了`Image.asset`这个构造方法直接来帮助我们读取图片资源并返回一个Image对象。其实`Image.asset`是对`AssetImage`一层更高级的封装。
> 注意：要读取本地图片我们首先需要在`pubspec.yaml`文件里配置本地图片资源的路径，我们这里在`assets`这个字段下新增了`- images/image_demo.jpg`这个文件。后续将会有一篇专门的博客来讲解资源的管理。

**1. AssetImage**
``` dart
Image(
    image: AssetImage("images/image_demo.jpg"),
    width: 80,
    height: 80,
)
```

**2. Image.asset**
``` dart
Image.asset(
    "images/image_demo.jpg",
    width: 80,
    height: 80,
)
```
两个方法都是传入一个本地文件路径就可以了。

### NetworkImage 和 Image.network
`NetworkImage`是一个可以从网络下载图片的类，它本身是异步的。`Image.network`是对`NetworkImage`的封装，它需要传入一个URL地址就可以返回一个Image对象。这两个的设计跟`AssetImage`和`Image.asset`的设计基本一致。
**3. NetworkImage**
``` dart
Image(
    image: NetworkImage("http://www.fulade.me/img/avatar.jpg"),
    width: 80,
    height: 80,
)
```

**4. Image.network**
``` dart
Image.network(
    "http://www.fulade.me/img/avatar.jpg",
    width: 80,
    height: 80,
)
```

### Alignment
`alignment`是Image的一个很重要的参数，它可以帮助我们设置图片的位置。有以下几个枚举值
|  参数   | 描述  |
|  ----  | ----  |
| topCenter  | 居中靠上 |
| topRight  | 右上角 |
| centerLeft | 居中靠左 |
| center  |   居中 |
| centerRight | 居中靠右 |
| bottomLeft | 居右下角 |
| bottomCenter | 居中靠下 |
| bottomRight | 居右下角 |
### BoxFit
`fit`参数是很重要的布局参数，当我们的图片内容跟Image设置的大小不完全吻合的时候，`fit`的参数值`BoxFit`可以帮助我们做最优的调整和显示
**5. BoxFit.contain**
`fit`的默认值是`BoxFit.contain`。由下图我们不难看出，`BoxFit.contain`会等比例缩放，保持图片的原始的比例并且显示在Image内。
![2020_01_11_box_contain](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_11_box_contain.png)

**6. BoxFit.fill**
由图可见`BoxFit.fill`会充满整个容器，如果图片大小与容器不完全吻合，可能会出现拉伸。
![2020_01_11_box_fill](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_11_box_fill.png)

**7. BoxFit.cover**
`BoxFit.cover`会保持图片资源的大小，如果超过的部分会被裁掉不会显示。
![2020_01_11_box_cover](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_11_box_cover.jpg)

**8. BoxFit.fitWidth**
`BoxFit.fitWidth`会使宽度充满整个容器，高度会按比例缩放，图片不会被拉伸，超出容器的部分会被剪裁。
![2020_01_11_box_fillwidth](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_11_box_fillwidth.jpg)

**9. BoxFit.fitHeight**
`BoxFit.fitHeight`跟`BoxFit.fitWidth`相似，高度会充满整个容器，宽度会按比例缩放，图片不会被拉伸，超出容器的部分会被剪裁。
![2020_01_11_box_fitheight](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_11_box_fitheight.jpg)

**10. BoxFit.none**
none表示没有设置显示策略，以原始大小居中来显示。
![2020_01_11_box_none_2](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_11_box_none_2.jpg)


**11. BoxFit.scaleDown**
当图片资源大于容器的时候，效果相当于 `BoxFit.none`，
当组件比图片小时，效果相当于 `BoxFit.contain`。
![2020_01_11_box_scaleDown](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_01_11_box_scaleDown.jpg)


> 对于加载过的图片Flutter是会帮助我们做内存缓存，最大缓存数量是1000，最大缓存内存空间是100M。

想体验以上的示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`image_page.dart`查看，并且可以下载下来运行并体验。

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
