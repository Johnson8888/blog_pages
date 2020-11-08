---
title: Flutter教程Dart语言——控制语句
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
##### **控制语句**
Dart语言的控制语句跟其他常见语言的控制语句是一样的，基本如下：
- **if 和 else**
- **for 循环**
- **while 和 do-while 循环**
- **break 和 continue**
- **switch 和 case**
- **assert**

<!--more-->
[文章首发地址](http://fulade.me/dart-control-flow-statements-1-8.html)
##### **If 和 Else**
Dart 支持 if - else 语句，其中 else 是可选的，比如下面的例子。
```Dart 
if (isRaining()) {
  you.bringRainCoat();
} else if (isSnowing()) {
  you.wearJacket();
} else {
  car.putTopDown();
}
```
与 JavaScript 不同的是，Dart 的 if 语句中的条件必须是一个布尔值，不能是其它类型。
##### **For循环**
For 循环
你可以使用标准的 for 循环进行迭代。例如：
``` Dart
var message = StringBuffer('Dart is fun');
for (var i = 0; i < 5; i++) {
  message.write('!');
}
```
在 Dart 语言中，for 循环中的闭包会自动捕获循环的 索引值 以避免 JavaScript 中一些常见的陷阱。假设有如下代码：
``` Dart
var callbacks = [];
for (var i = 0; i < 2; i++) {
  callbacks.add(() => print(i));
}
callbacks.forEach((c) => c());
```
上述代码执行后会输出 0 和 1，但是如果在 JavaScript 中执行同样的代码则会输出两个 2。

如果要遍历的对象实现了 Iterable 接口，则可以使用 forEach() 方法，如果不需要使用到索引，则使用 forEach 方法是一个非常好的选择：
``` Dart
candidates.forEach((candidate) => candidate.interview());
```
像 List 和 Set 等实现了 Iterable 接口的类还支持 for-in 形式的 迭代：
``` Dart 
var collection = [1, 2, 3];
for (var x in collection) {
  print(x); // 1 2 3
}
```

##### **While 和 Do-While**
while 循环会在执行循环体前先判断条件：
``` Dart
while (!isDone()) {
  doSomething();
}
```
do-while 循环则会先执行一遍循环体 再 判断条件：
``` Dart
do {
  printLine();
} while (!atEndOfPage());

```

##### **Break 和 Continue**
使用 `break` 可以中断循环：
``` Dart
while (true) {
  if (shutDownRequested()) break;
  processIncomingRequests();
}
```
使用 `continue` 可以跳过本次循环直接进入下一次循环：
``` Dart
for (int i = 0; i < candidates.length; i++) {
  var candidate = candidates[i];
  if (candidate.yearsExperience < 5) {
    continue;
  }
  candidate.interview();
}
```
上述代码中的 candidates 如果像 `List` 或 `Set` 一样实现了 `Iterable` 接口则可以简单地使用下述写法：
``` Dart:
candidates
    .where((c) => c.yearsExperience >= 5)
    .forEach((c) => c.interview());
```
##### **Switch 和 Case**
Switch 语句在 Dart 中使用 == 来比较整数、字符串或编译时常量，比较的两个对象必须是同一个类型且不能是子类并且没有重写 == 操作符。 枚举类型非常适合在 Switch 语句中使用。

每一个非空的 `case` 子句都必须有一个 `break` 语句，也可以通过 `continue、throw` 或者 `return` 来结束非空 `case` 语句。
当没有 `case` 语句匹配时，可以使用 `default` 子句来匹配这种情况：
``` Dart
var command = 'OPEN';
switch (command) {
  case 'CLOSED':
    executeClosed();
    break;
  case 'PENDING':
    executePending();
    break;
  case 'APPROVED':
    executeApproved();
    break;
  case 'DENIED':
    executeDenied();
    break;
  case 'OPEN':
    executeOpen();
    break;
  default:
    executeUnknown();
}
```
下面的例子忽略了 `case` 子句的 `break` 语句，因此会产生错误：
``` Dart
var command = 'OPEN';
switch (command) {
  case 'OPEN':
    executeOpen();
    // 错误: 没有 break

  case 'CLOSED':
    executeClosed();
    break;
}
```
但是，`Dart` 支持空的 `case` 语句，允许其以 `fall-through` 的形式执行。
```Dart
var command = 'CLOSED';
switch (command) {
  case 'CLOSED': // case 语句为空时的 fall-through 形式。
  case 'NOW_CLOSED':
    // case 条件值为 CLOSED 和 NOW_CLOSED 时均会执行该语句。
    executeNowClosed();
    break;
}
```
在非空 `case` 语句中想要实现 `fall-through` 的形式，可以使用 `continue` 语句配合 lable 的方式实现:
``` Dart
var command = 'CLOSED';
switch (command) {
  case 'CLOSED':
    executeClosed();
    continue nowClosed;
  // 继续执行标签为 nowClosed 的 case 子句。

  nowClosed:
  case 'NOW_CLOSED':
    // case 条件值为 CLOSED 和 NOW_CLOSED 时均会执行该语句。
    executeNowClosed();
    break;
}
```
每个 `case` 子句都可以有局部变量且仅在该 `case` 语句内可见。

##### **断言**
在开发过程中，可以在条件表达式为 `false` 时使用 **- assert**; 来打断代码的执行。你可以在本文中找到大量使用 `assert` 的例子。下面是相关示例：
``` Dart
// 确保变量值不为 null (Make sure the variable has a non-null value)
assert(text != null);

// 确保变量值小于 100。
assert(number < 100);

// 确保这是一个 https 地址。
assert(urlString.startsWith('https'));
assert 的第二个参数可以为其添加一个字符串消息。

assert(urlString.startsWith('https'),
    'URL ($urlString) should start with "https".');
```
`assert` 的第一个参数可以是值为布尔值的任何表达式。如果表达式的值为`true`，则断言成功，继续执行。如果表达式的值为 false，则断言失败，抛出一个 `AssertionError` 异常。

如何判断 `assert` 是否生效？`assert` 是否生效依赖开发工具和使用的框架：

- Flutter 在调试模式时生效。

- 一些开发工具比如 dartdevc 通常情况下是默认生效的。

- 其他一些工具，比如 dart 以及 dart2js 通过在运行 Dart 程序时添加命令行参数 --enable-asserts 使 assert 生效。

在生产环境代码中，断言会被忽略，与此同时传入 `assert` 的参数不被判断。


***  
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)