---
title: 【Flutter 1-12】Flutter手把手教程Dart语言——什么是泛型和泛型的使用场景
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
cover: 'https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/page_conver_dart.jpg'
thumbnail: 'https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/page_conver_dart.jpg'
toc: true
comments: true
tags:
  - Dart语言
  - Dart运算符
  - Flutter教程
  - Dart类
  - Dart Class
categories: Flutter
keywords: Dart语言，Dart运算符，Flutter教程，Dart Class，Dart类
description: >-
  如果你查看数组的API文档，你会发现数组List的实际类型为List<E>。<…>
  符号表示数组是一个泛型（或参数化类型）通常使用一个字母来代表类型参数，比如E、T、S、K 和 V 等等。
date: 2020-12-05 19:34:28
photos:
fileName:
type:
---

作者 | 弗拉德  
来源 | 弗拉德（公众号：fulade_me)


## 泛型
如果你查看数组的API文档，你会发现数组`List`的实际类型为`List<E>`。`<>` 符号表示数组是一个泛型（或参数化类型）通常使用一个字母来代表类型参数，比如E、T、S、K 和 V 等等。

#### 为什么使用泛型？
泛型常用于需要要求类型安全的情况，但是它对代码运行也有好处：
- 适当地指定泛型可以更好地帮助代码生成。
- 使用泛型可以减少代码重复。

比如你想声明一个只能包含`String`类型的数组，你可以将该数组声明为`List<String>`，这表示只能包含字符串类型的数组。这样的话就可以很容易避免因为在该数组放入非`String`类变量而导致的诸多问题，同时编译器以及其他阅读代码的人都可以很容易地发现并定位问题：
``` Dart
var names = List<String>();
names.addAll(['Seth', 'Kathy', 'Lars']);
names.add(42); // 这样写就会报错
``` 
另一个使用泛型的原因是可以减少重复代码。泛型可以让你在多个不同类型实现之间共享同一个接口声明，比如下面的例子中声明了一个类用于缓存对象的接口：
``` dart
/// 定义一个 抽象类
abstract class ObjectCache {
  Object getByKey(String key);
  void setByKey(String key, Object value);
}
```
不久后你可能又会想专门为`String`类对象做一个缓存，于是又有了专门为`String`做缓存的类：
``` dart
/// 另外一个抽象类
abstract class StringCache {
  String getByKey(String key);
  void setByKey(String key, String value);
}
```
如果过段时间你又想为数字类型也创建一个类，那么就会有很多诸如此类的代码。
这时候可以考虑使用泛型来声明一个类，让不同类型的缓存实现该类做出不同的具体实现即可：
``` dart
abstract class Cache<T> {
  T getByKey(String key);
  void setByKey(String key, T value);
}
```
在上述代码中，`T`是一个替代类型。其相当于类型占位符，在开发者调用该接口的时候会指定具体类型。

#### 使用集合字面量
`List、Set`以及`Map`字面量也可以是参数化的。定义参数化的`List`只需在中括号前添加`<type>`；定义参数化的`Map`只需要在大括号前添加 `<keyType, valueType>`：
``` dart 
var names = <String>['小芸', '小芳', '小民'];
var uniqueNames = <String>{'小芸', '小芳', '小民'};
var pages = <String, String>{
  'index.html': '主页',
  'robots.txt': '网页机器人提示',
  'humans.txt': '我们是人类，不是机器'
};
```
#### 使用类型参数化的构造函数
在调用构造方法时也可以使用泛型，只需在类名后用尖括号`<...>`将一个或多个类型包裹即可：
``` dart
var nameSet = Set<String>.from(names);
```
下面代码创建了一个键为`Int`类型，值为`View`类型的`Map`对象：
``` dart
var views = Map<int, View>();
```
#### 泛型集合以及它们所包含的类型
Dart的泛型类型是固化的，这意味着即便在运行时也会保持类型信息：
``` dart
var names = List<String>();
names.addAll(['小芸', '小芳', '小民']);
print(names is List<String>); // true
```

#### 限制参数化类型
有时使用泛型的时候可能会想限制泛型的类型范围，这时候可以使用`extends`关键字：
``` dart
class Foo<T extends SomeBaseClass> {
  // 具体实现……
  String toString() => "'Foo<$T>' 的实例";
}
class Extender extends SomeBaseClass {...}
```
这时候就可以使用`SomeBaseClass`或者它的子类来作为泛型参数：
``` dart
var someBaseClassFoo = Foo<SomeBaseClass>();
var extenderFoo = Foo<Extender>();
```
这时候也可以指定无参数的泛型，这时无参数泛型的类型则为 `Foo<SomeBaseClass>`：
``` dart
var foo = Foo();
print(foo); // 'Foo<SomeBaseClass>' 的例   
```
将非`SomeBaseClass`的类型作为泛型参数则会导致编译错误：
``` dart
/// 这样写是会报错的
var foo = Foo<Object>(); 
```
#### 使用泛型方法
起初`Dart`只支持在类的声明时指定泛型，现在同样也可以在方法上使用泛型，称之为`泛型方法`：
``` dart
T first<T>(List<T> ts) {
  // 处理一些初始化工作或错误检测……
  T tmp = ts[0];
  // 处理一些额外的检查……
  return tmp;
}
```
方法 `first<T>` 的泛型`T`可以在如下地方使用：
- 函数的返回值类型 `T`。
- 参数的类型 `List<T>`。
- 局部变量的类型 `T tmp`。

![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
