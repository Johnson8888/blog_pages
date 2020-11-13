---
title: 【Flutter 1-7】Flutter教程Dart语言——变量
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-08 12:14:19
cover: https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/page_conver_variable.png
thumbnail: https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/page_conver_variable.png
categories: Flutter
keywords: dar语言，dart语言变量，flutterdart语言，dart语言基础
tags:
  - Flutter
description:
photos:
fileName:
type:
---

> 2011年10月10日的GOTO大会上，谷歌的两位工程师发布了“Dart”；Dart是一种全新的编程语言，旨在帮助开发者构建Web应用程序。Dart 1.0于2013年11月14日发布。我们日常开发Flutter使用的就是Dart语言，所以我们有必要了解一下Dart语言的使用方法。
<!--more-->
[文章首发地址](http://fulade.me/dart-variable-1-7.html)
#### **类型安全的语言**
Dart 语言是类型安全的语言，但是由于其支持类型推断，因此大多数变量不需要显式地指定类型：
例如
``` Dart
/// 初始化一个字符串
var name = 'Fulade';
/// Int类型
var year = 1995;
/// 浮点数类型
var antennaDiameter = 3.7;
/// 数组
var list = ['Java', 'Python', 'C++', 'C'];
/// 字典类型
var image = {
  'tags': ['土星'],
  'url': '//path/to/saturn.jpg'
};
```
#### **变量**
下面的示例代码将创建一个变量并将其初始化：
``` Dart
var name = 'Fulade';
```
**变量仅存储对象的引用。**
这里名为 name 的变量存储了一个 `String` 类型对象的引用，`'Fulade'` 则是该对象的值。
`name` 变量的类型被推断为 `String`，但是你可以为其指定类型。
如果一个对象的引用不局限于单一的类型，可以将其指定为 `Object` 或 `dynamic` 类型。
``` Dart
dynamic name = 'Bob';
```
除此之外你也可以指定类型：
``` Dart
String name = 'Bob';
```
#### **默认值**
在 Dart 中，未初始化的变量拥有一个默认的初始化值：`null`。即便数字也是如此，因为在 Dart 中一切皆为对象，数字也不例外。
``` Dart 
int lineCount;
if(lineCount == null) {
    print("line is null");
}
```
##### **Final 和 Const**
如果你不想更改一个变量，可以使用关键字 `final` 或者 `const` 修饰变量，这两个关键字可以替代 `var` 关键字或者加在一个具体的类型前。一个 `final` 变量只可以被赋值一次；一个 `const` 变量是一个编译时常量（`const` 变量同时也是 `final`）。被`final`修饰的变量在第一次使用的时候被初始化。
下面的示例中我们创建并设置两个 `final` 变量：
``` Dart
final name = 'Bob'; // Without a type annotation
final String nickname = 'Bobby';
```
你不能修改一个 `final` 变量的值：
``` Dart
name = 'Alice'; // Error: a final variable can only be set once.
```
使用关键字 `const` 修饰变量表示该变量为 **编译时常量**。如果使用 `const` 修饰类中的变量，则必须加上 `static` 关键字，即 `static const`（注意：顺序不能颠倒。在声明 `const` 变量时可以直接为其赋值，也可以使用其它的 `const` 变量为其赋值：
```Dart
const bar = 1000000; // 直接赋值 [Unit of pressure (dynes/cm2)]
const double atm = 1.01325 * bar; // 利用其它 const 变量赋值 (Standard atmosphere)
```
`const` 关键字不仅仅可以用来定义常量，还可以用来创建常量值，该常量值可以赋予给任何变量。你也可以将构造函数声明为 `const` 的，这种类型的构造函数创建的对象是不可改变的。
``` Dart 
var foo = const [];
final bar = const [];
const baz = []; // 相当于 `const []` (Equivalent to `const []`)
```
如果使用初始化表达式为常量赋值可以省略掉关键字 `const`，比如上面的常量 `baz` 的赋值就省略掉了 `const`没有使用 `final` 或 `const` 修饰的变量的值是可以被更改的，即使这些变量之前引用过 `const` 的值。
``` Dart
foo = [1, 2, 3]; // foo 的值之前为 const [] (Was const [])
```
常量的值不可以被修改：
``` Dart 
baz = [42]; // 报错：常量不可以被赋值。(Error: Constant variables can't be assigned a value.)
```
***  
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)