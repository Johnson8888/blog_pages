---
title: dart-functions-1-9
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-08 22:28:10
cover:
thumbnail:
tags:
keywords:
description:
photos:
fileName:
type:
---


#### **函数**
>Dart 是一种真正面向对象的语言，所以即便函数也是对象并且类型为 `Function`，这意味着函数可以被赋值给变量或者作为其它函数的参数。你也可以像调用函数一样调用 `Dart` 类的实例。

下面是定义一个函数的例子：
```Dart
bool isNoble(int atomicNumber) {
  return _nobleGases[atomicNumber] != null;
}
```
虽然高效 `Dart` 指南建议在公开的 API 上定义返回类型，不过即便不定义，该函数也依然有效：
```Dart
isNoble(atomicNumber) {
  return _nobleGases[atomicNumber] != null;
}
```
如果函数体内只包含一个表达式，你可以使用简写语法：
```Dart
bool isNoble(int atomicNumber) => _nobleGases[atomicNumber] != null;
```
语法 `=>` 表达式 是 `{ return 表达式; }` 的简写， `=>` 有时也称之为胖箭头语法。



#### **参数**
函数可以有两种形式的参数：**必要参数** 和 **可选参数**。必要参数定义在参数列表前面，可选参数则定义在必要参数后面。可选参数可以是 **命名的** 或 **位置的**。

##### **已命名的参**数
已命名的参数是可选参数了，除非他们被特别标记为 `required`。

当你调用函数时，可以使用 参数名: 参数值 的形式来指定命名参数。例如：
```Dart
enableFlags(bold: true, hidden: false);
```
定义函数时，使用 `{param1, param2, …}` 来指定命名参数：
```Dart
/// 设置 [bold] 和 [hidden] 标识……
/// Sets the [bold] and [hidden] flags...
void enableFlags({bool bold, bool hidden}) {...}
```
虽然命名参数是可选参数的一种类型，但是你仍然可以使用 `@required` 注解来标识一个命名参数是必须的参数，此时调用者则必须为该参数提供一个值。例如：
```Dart
const Scrollbar({Key key, @required Widget child})
```
如果调用者想要通过 `Scrollbar` 的构造函数构造一个 `Scrollbar` 对象而不提供 child 参数，则会导致编译错误。

`@required` 注解定义在 `meta package` 中，可以直接导入 `package:meta/meta.dart` 包使用。

##### **可选的位置参数**
使用 `[]` 将一系列参数包裹起来作为位置参数：
```Dart
String say(String from, String msg, [String device]) {
  var result = '$from says $msg';
  if (device != null) {
    result = '$result with a $device';
  }
  return result;
}
```
下面是不使用可选参数调用上述函数的示例：
```Dart
assert(say('Bob', 'Howdy') == 'Bob says Howdy');
```
下面是使用可选参数调用上述函数的示例：
```Dart
assert(say('Bob', 'Howdy', 'smoke signal') ==
    'Bob says Howdy with a smoke signal');
```
##### **默认参数值**
可以用 = 为函数的命名和位置参数定义默认值，默认值必须为编译时常量，没有指定默认值的情况下默认值为 null。

下面是设置可选参数默认值示例：

```Dart
/// 设置 [bold] 和 [hidden] 标识……
/// Sets the [bold] and [hidden] flags ...
void enableFlags({bool bold = false, bool hidden = false}) {...}

// bold 的值将为 true；而 hidden 将为 false。
enableFlags(bold: true);
```


下一个示例将向你展示如何为位置参数设置默认值：
```Dart
String say(String from, String msg,
    [String device = 'carrier pigeon', String mood]) {
  var result = '$from says $msg';
  if (device != null) {
    result = '$result with a $device';
  }
  if (mood != null) {
    result = '$result (in a $mood mood)';
  }
  return result;
}

assert(say('Bob', 'Howdy') ==
    'Bob says Howdy with a carrier pigeon');
```
`List` 或`Map` 同样也可以作为默认值。下面的示例定义了一个名为 `doStuff()` 的函数，并为其名为 `list` 和 `gifts` 的参数指定了一个 `List` 类型的值和 `Map` 类型的值。
```Dart
void doStuff(
    {List<int> list = const [1, 2, 3],
    Map<String, String> gifts = const {
      'first': 'paper',
      'second': 'cotton',
      'third': 'leather'
    }}) {
  print('list:  $list');
  print('gifts: $gifts');
}
```
##### **main() 函数**
每个 `Dart` 程序都必须有一个 `main()` 顶级函数作为程序的入口，`main()` 函数返回值为 `void` 并且有一个 `List<String>` 类型的可选参数。

下面是一个 Web 应用的 `main()` 函数示例：
```Dart
void main() {
  querySelector('#sample_text_id')
    ..text = 'Click me!'
    ..onClick.listen(reverseText);
}
```
 **上述代码中的 .. 语法称之为 级联调用。使用级联访问可以在一个对象上执行多个操作。

下面是使用命令行访问带参数的 main() 函数示例：
```Dart
// 使用命令 dart args.dart 1 test 运行该应用
// Run the app like this: dart args.dart 1 test
void main(List<String> arguments) {
  print(arguments);

  assert(arguments.length == 2);
  assert(int.parse(arguments[0]) == 1);
  assert(arguments[1] == 'test');
}
```
你可以通过使用 参数库 来定义和解析命令行参数。

##### **函数作为一级对象**
可以将函数作为参数传递给另一个函数。例如：

```Dart
void printElement(int element) {
  print(element);
}

var list = [1, 2, 3];

// 将 printElement 函数作为参数传递。
list.forEach(printElement);
```
你也可以将函数赋值给一个变量，比如：
```Dart
var loudify = (msg) => '!!! ${msg.toUpperCase()} !!!';
assert(loudify('hello') == '!!! HELLO !!!');
```

**下一节我们来学习匿名函数**
