---
title: Flutter教程Dart语言——匿名函数
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-09 19:58:16
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_functions.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_functions.jpeg
categories: Flutter
keywords: Flutter函数，Flutter函数变量，dart函数，dart方法，dart匿名函数
tags:
  - Flutter
description:
photos:
fileName:
type:
---


#### **匿名函数**
>大多数方法都是有名字的，比如 main() 或 printElement()。你可以创建一个没有名字的方法，称之为 匿名函数，或 Lambda表达式 或 Closure闭包。你可以将匿名方法赋值给一个变量然后使用它，比如将该变量添加到集合或从中删除。

匿名方法看起来与命名方法类似，在括号之间可以定义参数，参数之间用逗号分割。
<!--more-->
后面大括号中的内容则为函数体：
```Dart
([[类型] 参数[, …]]) {
  函数体;
};
```
下面代码定义了只有一个参数 `item` 且没有参数类型的匿名方法。`List` 中的每个元素都会调用这个函数，打印元素位置和值的字符串：
```Dart
var list = ['apples', 'bananas', 'oranges'];
list.forEach((item) {
  print('${list.indexOf(item)}: $item');
});
```


如果函数体内只有一行语句，你可以使用胖箭头缩写法。粘贴下面代码到 `DartPad` 中并点击运行按钮，验证两个函数是否一致。
```Dart
list.forEach(
    (item) => print('${list.indexOf(item)}: $item'));
```
#### **词法作用域**
Dart 是词法有作用域语言，变量的作用域在写代码的时候就确定了，大括号内定义的变量只能在大括号内访问，与 Java 类似。

下面是一个嵌套函数中变量在多个作用域中的示例：

``` Dart
bool topLevel = true;

void main() {
  var insideMain = true;

  void myFunction() {
    var insideFunction = true;

    void nestedFunction() {
      var insideNestedFunction = true;

      assert(topLevel);
      assert(insideMain);
      assert(insideFunction);
      assert(insideNestedFunction);
    }
  }
}
```
注意 `nestedFunction()` 函数可以访问包括顶层变量在内的所有的变量。

#### **词法闭包**
**闭包** 即一个函数对象，即使函数对象的调用在它原始作用域之外，依然能够访问在它词法作用域内的变量。

函数可以封闭定义到它作用域内的变量。接下来的示例中，函数 `makeAdder()` 捕获了变量 addBy。无论函数在什么时候返回，它都可以使用捕获的 `addBy` 变量。
``` Dart
/// 返回一个将 [addBy] 添加到该函数参数的函数。
/// Returns a function that adds [addBy] to the
/// function's argument.
Function makeAdder(int addBy) {
  return (int i) => addBy + i;
}

void main() {
  // 生成加 2 的函数。
  var add2 = makeAdder(2);

  // 生成加 4 的函数。
  var add4 = makeAdder(4);

  assert(add2(3) == 5);
  assert(add4(3) == 7);
}
```
#### **测试函数是否相等**
下面是顶级函数，静态方法和示例方法相等性的测试示例：
``` Dart
void foo() {} // 定义顶层函数 (A top-level function)

class A {
  static void bar() {} // 定义静态方法
  void baz() {} // 定义实例方法
}

void main() {
  var x;

  // 比较顶层函数是否相等。
  x = foo;
  assert(foo == x);

  // 比较静态方法是否相等。
  x = A.bar;
  assert(A.bar == x);

  // 比较实例方法是否相等。
  var v = A(); // A 的实例 #1
  var w = A(); // A 的实例 #2
  var y = w;
  x = w.baz;

  // 这两个闭包引用了相同的实例对象，因此它们相等。
  assert(y.baz == x);

  // 这两个闭包引用了不同的实例对象，因此它们不相等。
  assert(v.baz != w.baz);
}
```
返回值
所有的函数都有返回值。没有显示返回语句的函数最后一行默认为执行 `return null`;。
``` Dart
foo() {}

assert(foo() == null);
```
