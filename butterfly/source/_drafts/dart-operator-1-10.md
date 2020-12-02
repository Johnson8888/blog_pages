---
title: dart-operator-1-10
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-29 22:08:38
cover: https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/page_conver_dart.jpg
thumbnail: https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/page_conver_dart.jpg
tags: 
    - Dart语言
    - Dart运算符
    - Flutter教程
categories: Flutter
keywords: Dart语言，Dart运算符，Flutter教程
description: 运算符是一种告诉编译器执行特定的数学或逻辑操作的符号。Dart 语言内置了丰富的运算符，并提供了以下类型的运算符：算术运算符、关系运算符、类型判断运算符、赋值运算符、逻辑运算符、按位和移位运算符、条件表达式、级联运算符、其他运算符。
photos:
fileName:
type:
---


### 运算符
运算符是一种告诉编译器执行特定的数学或逻辑操作的符号。Dart 语言内置了丰富的运算符，并提供了以下类型的运算符：算术运算符、关系运算符、类型判断运算符、赋值运算符、逻辑运算符、按位和移位运算符、条件表达式、级联运算符、其他运算符。

#### 算数运算符
|  算数运算符   | 描述  |
|  ----  | ----  |
| +  | 加 |
| -  | 减 |
| - 表达式  | 一元负, 也可以作为反转（反转表达式的符号） |
| *  | 乘 |
| /  | 除 |
| ~/  | 除并取整 |
| %  | 取模 |
示例：
``` Dart
assert(2 + 3 == 5);
assert(2 - 3 == -1);
assert(2 * 3 == 6);
assert(5 / 2 == 2.5); // 结果是一个浮点数
assert(5 ~/ 2 == 2); // 结果是一个整数
assert(5 % 2 == 1); // 取余

assert('5/2 = ${5 ~/ 2} r ${5 % 2}' == '5/2 = 2 r 1');
```
Dart 还支持自增自减运算符：

|  自增自减运算符   | 描述  |
|  ----  | ----  |
| ++ var  | var = var + 1 (表达式的值为 var + 1) |
| var ++  | var = var + 1 (表达式的值为 var) |
| -- var  | var = var – 1 (表达式的值为 var – 1) |
| var --  | var = var – 1 (表达式的值为 var) |
示例：
``` Dart
var a, b;

a = 0;
b = ++a; // 在 b 赋值前将 a 增加 1。
assert(a == b); // 1 == 1

a = 0;
b = a++; // 在 b 赋值后将 a 增加 1。
assert(a != b); // 1 != 0

a = 0;
b = --a; // 在 b 赋值前将 a 减少 1。
assert(a == b); // -1 == -1

a = 0;
b = a--; // 在 b 赋值后将 a 减少 1。
assert(a != b); // -1 != 0
```

#### 关系运算符
|  关系运算符   | 描述  |
|  ----  | ----  |
| ==  | 相等 |
|!=	|不等于|
|>	|大于|
|<	|小于|
|>=	|大于等于|
|<=|小于等于|
要判断两个对象 x 和 y 是否表示相同的事物使用 == 即可。（在极少数情况下，可能需要使用 identical() 函数来确定两个对象是否完全相同。）。下面是 == 运算符的一些规则：

假设有变量 x 和 y，且 x 和 y 至少有一个为 null，则当且仅当 x 和 y 均为 null 时 x == y 才会返回 true，否则只有一个为 null 则返回 false。

x.==(y) 将会返回值，这里不管有没有 y，即 y 是可选的。也就是说 == 其实是 x 中的一个方法，并且可以被重写。详情请查阅重写运算符。

下面的代码给出了每一种关系运算符的示例：

``` Dart
assert(2 == 2);
assert(2 != 3);
assert(3 > 2);
assert(2 < 3);
assert(3 >= 3);
assert(2 <= 3);
```
#### 类型判断运算符
`as`、`is`、`is!` 运算符是在运行时判断对象类型的运算符。
|  类型判断运算符   | 描述  |
|  ----  | ----  |
|as|类型转换（也用作指定类前缀)）|
|is	|如果对象是指定类型则返回 true|
|is! |如果对象是指定类型则返回 false|

当且仅当 obj 实现了 T 的接口，obj is T 才是 true。例如 obj is Object 总为 true，因为所有类都是 Object 的子类。

仅当你确定这个对象是该类型的时候，你才可以使用 as 操作符可以把对象转换为特定的类型。例如：
``` Dart
(emp as Person).firstName = 'Bob';
```
如果你不确定这个对象类型是不是 T，请在转型前使用 is T 检查类型。
``` Dart
if (emp is Person) {
  // 类型检查
  emp.firstName = 'Bob';
}
```
你可以使用 `as` 运算符进行缩写：
``` Dart
(emp as Person).firstName = 'Bob';
``
#### 赋值运算符
可以使用 = 来赋值，同时也可以使用 ??= 来为值为 null 的变量赋值。
``` Dart
// 将 value 赋值给 a (Assign value to a)
a = value;
// 当且仅当 b 为 null 时才赋值
b ??= value;
```
像 += 这样的赋值运算符将算数运算符和赋值运算符组合在了一起。
|         |      |       |       |       |       |  
|  ----  | ----  | ----  | ----  | ----  | ----  |
|=	|–=	|/=|%=|	>>=|	^=|
|+=	|*=| ~/=|<<=	|&=|	=|
下面的例子展示了如何使用赋值以及复合赋值运算符：
``` Dart
a += b  	//就 等同于 a = a + b
var a = 2; // 使用 = 赋值 (Assign using =)
a *= 3; // 赋值并做乘法运算 Assign and multiply: a = a * 3
assert(a == 6);
```

#### 逻辑运算符
|  类型判断运算符   | 描述  |
|  ----  | ----  |
|!表达式|对表达式结果取反（即将 true 变为 false，false 变为 true）|
| &#124;&#124;	|逻辑或|
|&& |逻辑与|
下面是使用逻辑表达式的示例：
``` Dart
if (!done && (col == 0 || col == 3)) {
  // ...Do something...
}
```
#### 按位和移位运算符

|  按位和移位运算符   | 描述  |
|  ----  | ----  |
|&	|按位与| 
|&#124;	|按位或|
|^	|按位异或|
|~ 表达式|	按位取反（即将 “0” 变为 “1”，“1” 变为 “0”）|
|<<	|位左移|
|>>	|位右移|
下面是使用按位和移位运算符的示例：
```Dart
final value = 0x22;
final bitmask = 0x0f;
assert((value & bitmask) == 0x02); // 按位与 (AND)
assert((value & ~bitmask) == 0x20); // 取反后按位与 (AND NOT)
assert((value | bitmask) == 0x2f); // 按位或 (OR)
assert((value ^ bitmask) == 0x2d); // 按位异或 (XOR)
assert((value << 4) == 0x220); // 位左移 (Shift left)
assert((value >> 4) == 0x02); // 位右移 (Shift right)
```
#### 条件表达式

`条件 ? 表达式 1 : 表达式 2` ：如果条件为 true，执行表达式 1并返回执行结果，否则执行表达式 2 并返回执行结果。
`表达式 1 ?? 表达式 2`：如果表达式 1 为非 null 则返回其值，否则执行表达式 2 并返回其值。
如果赋值是根据布尔表达式则考虑使用 ?:  
``` Dart
var visibility = isPublic ? 'public' : 'private';
```
如果赋值是根据判定是否为 null 则考虑使用 ??
``` Dart
String playerName(String name) => name ?? 'Guest';
```
上述示例还可以写成至少下面两种不同的形式，只是不够简洁：
``` Dart
// 相对使用 ?: 运算符来说稍微长了点。(Slightly longer version uses ?: operator).
String playerName(String name) => name != null ? name : 'Guest';

// 如果使用 if-else 则更长。
String playerName(String name) {
  if (name != null) {
    return name;
  } else {
    return 'Guest';
  }
}
```

#### 级联运算符（..）
级联运算符（..）可以让你在同一个对象上连续调用多个对象的变量或方法。
比如下面的代码：

``` dart
querySelector('#confirm') // 获取对象 (Get an object).
  ..text = 'Confirm' // 使用对象的成员 (Use its members).
  ..classes.add('important')
  ..onClick.listen((e) => window.alert('Confirmed!'));
```
第一个方法 `querySelector` 返回了一个 `Selector` 对象，后面的级联操作符都是调用这个 `Selector` 对象的成员并忽略每个操作的返回值。

上面的代码相当于：
``` dart
var button = querySelector('#confirm');
button.text = 'Confirm';
button.classes.add('important');
button.onClick.listen((e) => window.alert('Confirmed!'));
```
级联运算符可以嵌套，例如：
``` dart
final addressBook = (AddressBookBuilder()
      ..name = 'jenny'
      ..email = 'jenny@example.com'
      ..phone = (PhoneNumberBuilder()
            ..number = '415-555-0100'
            ..label = 'home')
          .build())
    .build();
```
在返回对象的函数中谨慎使用级联操作符。例如，下面的代码是错误的：
``` dart
var sb = StringBuffer();
sb.write('foo')
  ..write('bar'); // 出错：void 对象中没有方法 write (Error: method 'write' isn't defined for 'void').
```
上述代码中的 `sb.write()` 方法返回的是 void，返回值为 void 的方法则不能使用级联运算符。

#### 其他运算符
大多数其它的运算符，已经在其它的示例中使用过：
| 运算符   | 名字  |  描述 |
| ---   | ---  |  --- |
|()	|使用方法	|代表调用一个方法|
|[]	|访问 List	|访问 List 中特定位置的元素|
|.	|访问成员|	成员访问符|
|?.	|条件访问成员|	与上述成员访问符类似，但是左边的操作对象不能为 null，例如 foo?.bar，如果 foo 为 null 则返回 null ，否则返回 bar|

更多关于 ., ?. 和 .. 运算符介绍，请参考下一篇[类]().

![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
