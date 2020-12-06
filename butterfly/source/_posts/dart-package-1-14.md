---
title: 【Flutter 1-14】Flutter手把手教程Dart语言——Dart语言引用、import、package使用
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-06 13:55:57
cover: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Dart语言
  - Dart import
  - Flutter教程
  - Dart 包管理
categories: Flutter
keywords: Dart语言，Dart import，Flutter教程，Dart包管理
description: import 关键字可以帮助你创建一个模块化和可共享的代码库，代码库不仅只是提供 API 而且还起到了封装的作用：以下划线（_）开头的成员仅在代码库中可见。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)
### 库
`import` 关键字可以帮助你创建一个模块化和可共享的代码库，代码库不仅只是提供 API 而且还起到了封装的作用：以下划线（_）开头的成员仅在代码库中可见。
#### 使用库
使用`import`来指定命名空间以便其它库可以访问。比如你可以导入代码库 `dart:html`来使用`Dart Web`中相关 API：
``` dart
import 'dart:html';
```
`import`的唯一参数是用于指定代码库的`URI`，对于`Dart`内置的库，使用 `dart:xxxxxx`的形式。而对于其它的库，你可以使用一个文件系统路径或者以 `package:xxxxxx` 的形式。`package:xxxxxx` 指定的库通过包管理器（比如 pub 工具）来提供：
``` dart
import 'package:test/test.dart';
```
#### 指定库前缀
如果你导入的两个代码库有冲突的标识符，你可以为其中一个指定前缀。比如如果 `library1`和`library2` 都有`Element` 类，那么可以这么处理：
``` dart
import 'package:lib1/lib1.dart';
import 'package:lib2/lib2.dart' as lib2;
// 使用 lib1 的 Element 类。
Element element1 = Element();
// 使用 lib2 的 Element 类。
lib2.Element element2 = lib2.Element();
```
#### 导入库的一部分
如果你只想使用代码库中的一部分，你可以有选择地导入代码库。例如：
``` dart
// 只导入 lib1 中的 foo。(Import only foo).
import 'package:lib1/lib1.dart' show foo;
// 导入 lib2 中除了 foo 外的所有。
import 'package:lib2/lib2.dart' hide foo;
```
#### 延迟加载库
**延迟加载**（也常称为懒加载）允许应用在需要时再去加载代码库，下面是可能使用到延迟加载的场景：

- 为了减少应用的初始化时间。

- 处理 A/B 测试，比如测试各种算法的不同实现。

- 加载很少会使用到的功能，比如可选的屏幕和对话框。

使用`deferred as`关键字来标识需要延时加载的代码库：
``` dart
import 'package:greetings/hello.dart' deferred as hello;
```

当实际需要使用到库中API时先调用`loadLibrary`函数加载库：
``` dart
Future greet() async {
  await hello.loadLibrary();
  hello.printGreeting();
}
``` 

在前面的代码，使用 await 关键字暂停代码执行直到库加载完成。更多关于 async 和 await 的信息请参考异步支持。
`loadLibrary` 函数可以调用多次也没关系，代码库只会被加载一次。
当你使用延迟加载的时候需要牢记以下几点：
- 延迟加载的代码库中的常量需要在代码库被加载的时候才会导入，未加载时是不会导入的。
- 导入文件的时候无法使用延迟加载库中的类型。如果你需要使用类型，则考虑吧接口类型转移到另一个库中然后让两个库都分别导入这个接口库。
- `Dart`会隐式地将`loadLibrary`方法导入到使用了`deferred as`命名空间 的类中。`loadLibrary`函数返回的是一个`Future`。

![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)