---
title: 【Flutter 3-5】Flutter进阶教程——在Flutter中使用Lottie动画
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-04-07 17:05:56
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_04_21_lottie_tag.png
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_04_21_lottie_tag.png
tags: 
  - Flutter lottie
  - Lottie 动画
categories: Flutter 
keywords: Flutter lottie、Lottie 动画
description: 在Flutter中使用Lottie动画
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

#### Lottie动画
在移动开发中总是需要展示一些动画特效，作为程序员的我们并不是很擅长用代码做动画，即便是有些动画可以实现，在跨平台的过程中也会因为API的差异性导致动画在各个平台中展示的有差异。
所以为了释放程序员的双手，不再陷入写动画调参数的苦恼，Airbnb开源了一款专门用于跨平台的动画解决方案：`Lottie`。  
`Lottie`可以解析使用Bodymovin导出为json的Adobe After Effects动画，并在移动端和Web端展示。这样我们就可以把做动画的工作交给专业做动画的同事来完成，我们只需要使用导入json文件即可，这样是不是大大减少了程序员的工作量，并且能够：实现专业的人做专业的事。

#### 导入Lottie框架
在Flutter中已经存在开源的[Lottie库](https://pub.dev/packages/lottie)，所以我们只需要在`pubspec.yaml`中的`dependencies`导入相关的依赖即可
``` yaml
dependencies:
  lottie: ^0.7.0              
```

#### 使用Lottie库 
在需要展示Lottie动画Widget导入头文件
``` dart
import 'package:lottie/lottie.dart';
```

#### 默认读取本地json文件
``` dart
    Lottie.asset("json/fun_do_like.json"),
```
![2021_04_21_lottie_nomail](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_04_21_lottie_nomail.gif)
只需要一句话即可展示Lottie动画，是不是很简单。
我们来看其他的属性

- repeat 是否重复执行。默认是true，如果是false，动画执行一遍就会停止
- reverse 是否倒序播放。默认是false，如果设置为true，动画会先正序播放一遍，然后再倒序播放一遍
- animate 是否允许播放动画。默认是true，如果设置为false，则不会播放动画

#### 从网络读取json文件
``` dart
Lottie.network("https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/lottie_test.json",),
```
同样我们可以设置获取到网络资源后的回调
``` dart
Lottie.network("https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/lottie_test.json",
    onLoaded: (LottieComposition composition) {
        print("onLoaded");
    },
),
```

好了，关于`Lottie`的使用就总结这些了。

想体验以上的示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`sqflite_page.dart`查看，并且可以下载下来运行并体验。
***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
