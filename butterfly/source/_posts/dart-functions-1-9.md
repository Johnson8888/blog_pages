---
title: 【Flutter 1-9】Flutter教程Dart语言——函数和匿名函数
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-08 22:28:10
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_functions.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_functions.jpeg
tags: 
    - Flutter
categories: Flutter
keywords: Flutter函数，Flutter函数变量，dart函数，dart方法
description: Dart 同样也是一种面向对象的语音。所以即便函数也是一个对象。类型为 `Function`，这意味着函数可做作为变量，也也可以作为函数的参数。
photos:
fileName:
type:
---
作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)
#### **函数**
>Dart 同样也是一种面向对象的语音。所以即便函数也是一个对象。类型为 `Function`，这意味着函数可做作为变量，也也可以作为函数的参数。
<!--more-->
下面是定义一个函数的例子：
```Dart
isEmpty(List aList) {
  return aList.length == 0;
}
```
为了规范其实我们需要在函数的头部声明一下返回值类型，当然如果不声明也可以运行，
```Dart
bool isEmpty(List aList) {
  return aList.length == 0;
}
```
如果函数体内只包含一个表达式，你可以使用简写语法：
```Dart
bool isEmpty(List aList) => aList == 0;
```
 `=>` 表达的 是 `{ return 表达式; }` 的简写，有时`=>`也称之为**胖箭头语法**。



#### **参数**
函数可以有两种形式的参数：**必选参数** 和 **可选参数**。必选参数定义在参数列表前面，可选参数一定是定义在必要参数后面。

##### **可选的命名参数**
当你调用函数时，可以使用 参数名: 参数值 的形式来指定命名参数。例如：
```Dart
enableFlags(bold: true, hidden: false);
```
已命名的参数是可选参数了，除非他们被特别标记为 `required`。

定义函数时，使用 `{param1, param2, …}` 来指定命名参数：
```Dart
/// 设置 [bold] 和 [hidden] 标识……
void enableFlags({bool bold, bool hidden}) {...}
```
虽然命名参数是可选参数的一种类型，但是你仍然可以使用 `@required` 注解来标识一个命名参数是必须的参数，此时调用者则必须为该参数提供一个值。例如：
```Dart
const Scrollbar({Key key, @required Widget child})
```
如果调用者想要通过 `Scrollbar` 的构造函数构造一个 `Scrollbar` 对象而不提供 child 参数，则会导致编译错误。

##### **可选参数**
使用 `[]` 将一系列参数包裹起来作为可选参数：
```Dart
strings(String s1, String s2, [String s3]) {
  var result = '$s1 and $s2';
  if (s3 != null) {
    result = '$result and $s3';
  }
  print(result);
}
```
下面是不使用可选参数调用上述函数的示例：
```Dart
strings("s1", "s2");
s1 and s2
```
下面是使用可选参数调用上述函数的示例：
```Dart
strings("s1", "s2", "s3");
s1 and s2 and s3
```
##### **默认参数值**
我们可以用 `=` 为函数的命名参数和可选参数定义默认值，默认值必须为编译时常量，没有指定默认值的情况下默认值为 `null`。

下面是设置可选参数默认值示例：

```Dart
/// 设置 [bold] 和 [hidden] 标识……
void enableFlags({bool bold = false, bool hidden = false}) {...}

// bold 的值将为 true；而 hidden 将为 false。
enableFlags(bold: true);
```


下一个示例 默认值：
```Dart
strings(String s1, String s2, [String s3 = 'this is s3', String s4]) {
  var result = '$s1 and $s2';
  if (s3 != null) {
    result = '$result and $s3';
  }
  if (s4 != null) {
    result = '$result and $s4';
  }
  print(result);
}

strings("s1", "s2");
s1 and s2 and this is s3
```

##### **main() 函数**
每个 `Dart` 程序都必须有一个 `main()` 顶级函数作为程序的入口，`main()` 函数返回值为 `void`。

下面是一个 Flutter 应用的 `main()` 函数示例：
```Dart
void main() {
  runApp(MyApp());
}
```

##### **函数作为参数**
可以将函数作为参数传递给另一个函数。例如：

```Dart
void printElement(int element) {
  print(element);
}
// 将 printElement 函数作为参数传递。
var list = [1, 2, 3];
list.forEach(printElement);
```

你也可以将函数赋值给一个变量，比如：
```Dart
var loudify = (msg) => '!!! ${msg.toUpperCase()} !!!';
var result = loudify('hello');
print(result);
```

#### **匿名函数**
>大多数方法都是有名字的，比如 `main()` 或 `printElement()`。你可以创建一个没有名字的方法，称之为 **匿名函数**，其实匿名函数很常见，也有不同的叫法，在C++里面叫Lambda表达式，在Objective-C叫Block闭包。你可以将匿名方法赋值给一个变量然后使用它。

匿名方法看起来与命名函数h类似，在括号之间可以定义参数，参数之间用逗号分割。

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


如果函数体内只有一行语句，你可以使用胖箭头缩写法。下面代码的运行结果，与上面代码的运行结果是一致的。
```Dart
list.forEach(
    (item) => print('${list.indexOf(item)}: $item'));
```
#### **变量作用域**
变量的作用域在写代码的时候就确定了，大括号内定义的变量只能在大括号内访问，与 Java 类似。

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

返回值
所有的函数都有返回值。没有显示返回语句的函数最后一行默认为执行 `return null`;。
``` Dart
foo() {}

assert(foo() == null);
```

本文所有代码都已上传到[Github](https://github.com/Johnson8888/learn_flutter)
***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)

