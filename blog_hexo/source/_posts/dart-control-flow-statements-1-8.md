---
title: 【Flutter 1-8】Flutter教程Dart语言——控制语句
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-08 20:03:59
cover: https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/page_conver_control_flow_statements.jpg
thumbnail: https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/page_conver_control_flow_statements.jpg
categories: Flutter
keywords: dar语言，dart语言变量，flutterdart语言，dart语言基础
tags:
  - Flutter
description:
photos:
fileName:
type:
---
作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)
##### **控制语句**
Dart语言的控制语句跟其他常见语言的控制语句是一样的，基本如下：
- **if 和 else**
- **for 循环**
- **while 和 do-while 循环**
- **break 和 continue**
- **switch 和 case**
- **assert**

<!--more-->
<!-- [文章首发地址](http://fulade.me/dart-control-flow-statements-1-8.html) -->
##### **If 和 Else**
Dart 支持 `if - else` 语句，其中 `else` 是可选的，比如下面的例子。
```Dart 
int i = 0;
if (i == 0) {
  print("value 0");
} else if (i == 1) {
  print("value 1");
} else {
  print("other value");
}
```

如果要遍历的对象实现了 `Iterable` 接口，则可以使用 `forEach()` 方法，如果不需要使用到索引，则使用 `forEach` 方法是一个非常好的选择：
>`Iterable`接口实现了很多方法，比如说 `forEach()、any()、where()`等，这些方法可以大大精简我们的代码，减少代码量。  

``` Dart
var callbacks = [];
for (var i = 0; i < 2; i++) {
  callbacks.add(() => print(i));
}
callbacks.forEach((c) => c());
```
像 `List` 和 `Set` 等，我们同样可以使用 `for-in` 形式的 迭代：
``` Dart 
var collection = [1, 2, 3];
for (var x in collection) {
  print(x); // 1 2 3
}
```

##### **While 和 Do-While**
while 循环会在执行循环体前先判断条件：
``` Dart
var i = 0;
while (i < 10) {
  i++;
  print("i = " + i.toString());
}
```
`do-while` 循环则会先执行一遍循环体 再 判断条件：
``` Dart
var i = 0;
do {
  i++;
  print("i = " + i.toString());
} while (i < 10);

```

##### **Break 和 Continue**
使用 `break` 可以中断循环：
``` Dart
for (int i = 0; i < 10; i++) {
  if (i > 5) {
    print("break now");
    break;
  }
  print("i = " + i.toString());
}
```
使用 `continue` 可以跳过本次循环直接进入下一次循环：
``` Dart
  for (int i = 0; i < 10; ++i) {
    if (i < 5) {
      continue;
    }
    print("i = " + i.toString());
  }
```
由于 List实现了 Iterable 接口，则可以简单地使用下述写法：
``` Dart:
[0,1, 2, 3, 4, 5, 6, 7, 8, 9].where((i) => i > 5).forEach((i) {
  print("i = " + i.toString());
});
```
##### **Switch 和 Case**
Switch 语句在 Dart 中使用 `==` 来比较整数、字符串或编译时常量，比较的两个对象必须是同一个类型且不能是子类并且没有重写 `==` 操作符。 枚举类型非常适合在 Switch 语句中使用。
每一个 `case` 语句都必须有一个 `break` 语句，也可以通过 `continue、throw` 或者 `return` 来结束 `case` 语句。
当没有 `case` 语句匹配时，可以使用 `default` 子句来匹配这种情况：
``` Dart
  var command = 'OPEN';
  switch (command) {
    case 'CLOSED':
      print('CLOSED');
      break;
    case 'PENDING':
      print('PENDING');
      break;
    case 'APPROVED':
      print('APPROVED');
      break;
    case 'DENIED':
      print('DENIED');
      break;
    case 'OPEN':
      print('OPEN');
      break;
    default:
      print('UNKNOW');
  }
```

但是，`Dart` 支持空的 `case` 语句，如下：
```Dart
var command = 'CLOSED';
switch (command) {
  case 'CLOSED': // case 语句为空时的 fall-through 形式。
  case 'NOW_CLOSED':
    // case 条件值为 CLOSED 和 NOW_CLOSED 时均会执行该语句。
    print(command);
    break;
}
```

##### **断言**
在开发过程中，可以在条件表达式为 `false` 时使用 **assert**， 来中断代码的执行，提示出错误。你可以在本文中找到大量使用 `assert` 的例子。下面是相关示例：
``` Dart
// 确保变量值不为 null (Make sure the variable has a non-null value)
assert(text != null);

// 确保变量值小于 100。
assert(number < 100);

// 确保这是一个 https 地址。
assert(urlString.startsWith('https'));
assert 的第二个参数可以为其添加一个字符串消息。

assert(urlString.startsWith('https'),'URL ($urlString) should start with "https".');
```
`assert` 的第一个参数可以是值为布尔值的任何表达式。如果表达式的值为`true`，则断言成功，继续执行。如果表达式的值为`false`，则断言失败，抛出一个 `AssertionError` 异常。

**注意：**
在生产环境代码中，断言会被忽略，与此同时传入 `assert` 的参数不被判断。

本文所有代码都已上传到[Github](https://github.com/Johnson8888/learn_flutter)
***  
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)