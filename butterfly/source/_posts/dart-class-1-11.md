---
title: 【Flutter 1-11】Flutter手把手教程Dart语言——类、类的的成员变量和方法、类的构造函数
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
cover: 
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: 
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
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
  Dart是一种面向对象的语言，所有对象都是一个类的实例，而所有的类都继承自`Object`类。每个除`Object`类之外的类都只有一个超类，一个类的代码可以在其它多个类继承中重复使用。
date: 2020-12-04 15:48:27
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

## 类
Dart是一种面向对象的语言，所有对象都是一个类的实例，而所有的类都继承自`Object`类。每个除了`Object`类之外的类都只有一个超类，一个类的代码可以在其它多个类继承中重复使用。

#### 类的实例变量
下面是声明实例变量的示例：
``` Dart
class Point {
  double x; // 声明 double 变量 x 并初始化为 null。
  double y; // 声明 double 变量 y 并初始化为 null
  double z = 0; // 声明 double 变量 z 并初始化为 0。
}
```
所有未初始化的实例变量其值均为`null`。

所有实例变量均会隐式地声明一个`Getter` 方法，非`final`类型的实例变量还会隐式地声明一个`Setter`方法
``` Dart
class Point {
  double x;
  double y;
}

void main() {
  var point = Point();
  point.x = 4; // 使用 x 的 Setter 方法。
  assert(point.x == 4); // 使用 x 的 Getter 方法。
  assert(point.y == null); // 默认值为 null。
}
```
如果你在声明一个实例变量的时候就将其初始化（而不是在构造函数或其它方法中），那么该实例变量的值就会在对象实例创建的时候被设置，该过程会在构造函数以及它的初始化器列表执行前。


##### 访问类的成员
对象的成员由函数和数据（即方法和实例变量）组成。方法的调用要通过对象来完成，这种方式可以访问对象的函数和数据。
使用`.`来访问对象的实例变量或方法：
``` Dart
var p = Point(2, 2);
// 获取 y 值
assert(p.y == 2);
// 调用变量 p 的 distanceTo() 方法。
double distance = p.distanceTo(Point(4, 4));
```
使用 `?.` 代替`.`可以避免因为左边表达式为`null` 而导致的问题：
``` Dart
// If p is non-null, set a variable equal to its y value.
var a = p?.y;
```


##### 方法
方法是对象提供行为的函数。

对象的实例方法可以访问实例变量和`this`。下面的`distanceTo()`方法就是一个实例方法的例子：
``` Dart
import 'dart:math';

class Point {
  double x, y;

  Point(this.x, this.y);

  double distanceTo(Point other) {
    var dx = x - other.x;
    var dy = y - other.y;
    return sqrt(dx * dx + dy * dy);
  }
}
```

##### 重写类成员
子类可以重写父类的实例方法（包括操作符）、 `Getter` 以及 `Setter` 方法。你可以使用 `@override`注解来表示你重写了一个成员：
``` dart
class SmartTelevision extends Television {
  @override
  void turnOn() {...}
  // ···
}
```

##### noSuchMethod 方法
如果调用了对象中不存在的方法或实例变量将会触发`noSuchMethod` 方法，你可以重写`noSuchMethod`方法来追踪和记录这一行为：
``` dart
class A {
  // 除非你重写 noSuchMethod，否则调用一个不存在的成员会导致 NoSuchMethodError。
  @override
  void noSuchMethod(Invocation invocation) {
    print('你尝试使用一个不存在的成员：' + '${invocation.memberName}');
  }
}
```
你不能调用一个未实现的方法除非满足下面其中的一个条件：
- 接收方是静态的`dynamic` 类型。
- 接收方具有静态类型，定义了未实现的方法，并且接收方的动态类型实现了`noSuchMethod`方法且具体的实现与`Object`中的不同。



#### 类的静态变量和静态方法
使用关键字`static`可以声明类变量或类方法。

##### 静态变量
静态变量（即类变量）常用于声明类范围内所属的状态变量和常量：
``` dart
class Queue {
  static const initialCapacity = 16;
  // ···
}
void main() {
  assert(Queue.initialCapacity == 16);
}
```
静态变量在其首次被使用的时候才被初始化。

##### 静态方法
静态方法（即类方法）不能被一个类的实例访问，同样地，静态方法内也不可以使用关键字`this`：
``` dart
import 'dart:math';
class Point {
  double x, y;
  Point(this.x, this.y);
  static double distanceBetween(Point a, Point b) {
    var dx = a.x - b.x;
    var dy = a.y - b.y;
    return sqrt(dx * dx + dy * dy);
  }
}

void main() {
  var a = Point(2, 2);
  var b = Point(4, 4);
  var distance = Point.distanceBetween(a, b);
  assert(2.8 < distance && distance < 2.9);
  print(distance);
}
```


#### 使用构造函数构建对象
可以使用构造函数来创建一个对象。构造函数的命名方式可以为类名或类名`.`标识符的形式。例如下述代码分别使用`Point()`和`Point.fromJson()`两种构造器来创建`Point`对象：
``` Dart
var p1 = Point(2, 2);
var p2 = Point.fromJson({'x': 1, 'y': 2});
```
以下代码具有相同的效果，构造函数名前面的的`new`关键字是可选的：
``` Dart
var p1 = new Point(2, 2);
var p2 = new Point.fromJson({'x': 1, 'y': 2});
```

一些类提供了常量构造函数。使用常量构造函数，在构造函数名之前加 `const`关键字，来创建编译时常量时：
``` Dart
var p = const ImmutablePoint(2, 2);
```
两个使用相同构造函数相同参数值构造的编译时常量是同一个对象：
``` Dart
var a = const ImmutablePoint(1, 1);
var b = const ImmutablePoint(1, 1);

assert(identical(a, b)); // 它们是同一个实例 (They are the same instance!)
```
根据使用常量上下文的场景，你可以省略掉构造函数或字面量前的`const` 关键字。例如下面的例子中我们创建了一个常量`Map`：
``` Dart
// 这里有很多 const 关键字
const pointAndLine = const {
  'point': const [const ImmutablePoint(0, 0)],
  'line': const [const ImmutablePoint(1, 10), const ImmutablePoint(-2, 11)],
};
```

根据上下文，你可以只保留第一个`const`关键字，其余的全部省略：
``` Dart
// 只需要一个 const 关键字，其它的则会隐式地根据上下文进行关联。
const pointAndLine = {
  'point': [ImmutablePoint(0, 0)],
  'line': [ImmutablePoint(1, 10), ImmutablePoint(-2, 11)],
};
```
但是如果无法根据上下文判断是否可以省略`const`，则不能省略掉 `const`关键字，否则将会创建一个**非**常量对象 例如：
``` Dart
var a = const ImmutablePoint(1, 1); // 创建一个常量 (Creates a constant)
var b = ImmutablePoint(1, 1); // 不会创建一个常量
assert(!identical(a, b)); // 这两变量并不相同 
```

#### 获取对象的类型
可以使用`Object`对象的`runtimeType`属性在运行时获取一个对象的类型，该对象类型是`Type`的实例。
``` Dart
var = Point(2, 2);
print('The type of a is ${a.runtimeType}');
```




#### 构造函数
声明一个与类名一样的函数即可声明一个构造函数（对于命名式构造函数 还可以添加额外的标识符)。大部分的构造函数形式是生成式构造函数，其用于创建一个类的实例：
``` Dart
class Point {
  double x, y;
  Point(double x, double y) {
    // 还会有更好的方式来实现此逻辑，敬请期待。
    this.x = x;
    this.y = y;
  }
}
```
使用 `this` 关键字引用当前实例。
对于大多数编程语言来说在构造函数中为实例变量赋值的过程都是类似的，而`Dart`则提供了一种特殊的语法糖来简化该步骤：
``` Dart
class Point {
  double x, y;
  // 在构造函数体执行前用于设置 x 和 y 的语法糖。
  Point(this.x, this.y);
}
```

##### 默认构造函数
如果你没有声明构造函数，那么`Dart`会自动生成一个无参数的构造函数并且该构造函数会调用其父类的无参数构造方法。

##### 构造函数不被继承
子类不会继承父类的构造函数，如果子类没有声明构造函数，那么只会有一个默认无参数的构造函数。

##### 命名式构造函数
可以为一个类声明多个命名式构造函数来表达更明确的意图：
``` Dart
class Point {
  double x, y;

  Point(this.x, this.y);

  // 命名式构造函数
  Point.origin() {
    x = 0;
    y = 0;
  }
}
```
构造函数是不能被继承的，这将意味着子类不能继承父类的命名式构造函数，如果你想在子类中提供一个与父类命名构造函数名字一样的命名构造函数，则需要在子类中显式地声明。

##### 调用父类非默认构造函数
默认情况下，子类的构造函数会调用父类的匿名无参数构造方法，并且该调用会在子类构造函数的函数体代码执行前，如果子类构造函数还有一个初始化列表，那么该初始化列表会在调用父类的该构造函数之前被执行，总的来说，这三者的调用顺序如下：

1. 初始化列表
2. 父类的无参数构造函数
3. 当前类的构造函数

如果父类没有匿名无参数构造函数，那么子类必须调用父类的其中一个构造函数，为子类的构造函数指定一个父类的构造函数只需在构造函数体前使用`:`指定。

因为参数会在子类构造函数被执行前传递给父类的构造函数，因此该参数也可以是一个表达式，比如一个函数：
``` Dart
class Employee extends Person {
  Employee() : super.fromJson(defaultData);
  // ···
}
```

##### 初始化列表
除了调用父类构造函数之外，还可以在构造函数体执行之前初始化实例变量。每个实例变量之间使用逗号分隔。
``` Dart
// 使用初始化列表在构造函数体执行前设置实例变量。
Point.fromJson(Map<String, double> json)
    : x = json['x'],
      y = json['y'] {
  print('In Point.fromJson(): ($x, $y)');
}
```
在开发模式下，你可以在初始化列表中使用`assert`来验证输入数据：
``` Dart
Point.withAssert(this.x, this.y) : assert(x >= 0) {
  print('In Point.withAssert(): ($x, $y)');
}
```

##### 重定向构造函数
有时候类中的构造函数会调用类中其它的构造函数，该重定向构造函数没有函数体，只需在函数签名后使用`:`指定需要重定向到的其它构造函数即可：
``` Dart
class Point {
  double x, y;

  // 该类的主构造函数。
  Point(this.x, this.y);

  // 委托实现给主构造函数。
  Point.alongXAxis(double x) : this(x, 0);
}
```
##### 常量构造函数
如果类生成的对象都是不会变的，那么可以在生成这些对象时就将其变为编译时常量。你可以在类的构造函数前加上`const`关键字并确保所有实例变量均为`final`来实现该功能。
``` Dart
class ImmutablePoint {
  static final ImmutablePoint origin =
      const ImmutablePoint(0, 0);

  final double x, y;

  const ImmutablePoint(this.x, this.y);
}
```
常量构造函数创建的实例并不总是常量。


##### 工厂构造函数
使用`factory`关键字标识类的构造函数将会令该构造函数变为工厂构造函数，这将意味着使用该构造函数构造类的实例时并非总是会返回新的实例对象。例如，工厂构造函数可能会从缓存中返回一个实例，或者返回一个子类型的实例。

在如下的示例中，`Logger`的工厂构造函数从缓存中返回对象，和 `Logger.fromJson`工厂构造函数从`JSON`对象中初始化一个最终变量。
``` Dart
class Logger {
  final String name;
  bool mute = false;

  // _cache 变量是库私有的，因为在其名字前面有下划线。
  static final Map<String, Logger> _cache =
      <String, Logger>{};

  factory Logger(String name) {
    return _cache.putIfAbsent(
        name, () => Logger._internal(name));
  }

  factory Logger.fromJson(Map<String, Object> json) {
    return Logger(json['name'].toString());
  }

  Logger._internal(this.name);

  void log(String msg) {
    if (!mute) print(msg);
  }
}
```
工厂构造函的调用方式与其他构造函数一样：
``` Dart
var logger = Logger('UI');
logger.log('Button clicked');

var logMap = {'name': 'UI'};
var loggerJson = Logger.fromJson(logMap);
```

#### 抽象类

使用关键字`abstract` 标识类可以让该类成为抽象类，抽象类将无法被实例化。抽象类常用于声明接口方法、有时也会有具体的方法实现。如果想让抽象类同时可被实例化，可以为其定义工厂构造函数。

抽象类常常会包含抽象方法。下面是一个声明具有抽象方法的抽象类示例：
``` dart
// 该类被声明为抽象的，因此它不能被实例化。
abstract class AbstractContainer {
  // 定义构造函数、字段、方法等……
  void updateChildren(); // 抽象方法。
}
```
#### 隐式接口
每一个类都隐式地定义了一个接口并实现了该接口，这个接口包含所有这个类的实例成员以及这个类所实现的其它接口。如果想要创建一个`A`类支持调用`B`类的API且不想继承`B`类，则可以实现`B`类的接口。

一个类可以通过关键字`implements`来实现一个或多个接口并实现每个接口定义的 API：
``` dart
// Person 类的隐式接口中包含 greet() 方法。
class Person {
  // _name 变量同样包含在接口中，但它只是库内可见的。
  final _name;

  // 构造函数不在接口中。
  Person(this._name);

  // greet() 方法在接口中。
  String greet(String who) => '你好，$who。我是$_name。';
}

// Person 接口的一个实现。
class Impostor implements Person {
  get _name => '';

  String greet(String who) => '你好$who。你知道我是谁吗？';
}

String greetBob(Person person) => person.greet('小芳');

void main() {
  print(greetBob(Person('小芸')));
  print(greetBob(Impostor()));
}
```
如果需要实现多个类接口，可以使用逗号分割每个接口类：
``` dart
class Point implements Comparable, Location {

}
```

#### 扩展一个类
使用`extends`关键字来创建一个子类，并可使用`super`关键字引用一个父类：
```dart
class Television {
  void turnOn() {
    _illuminateDisplay();
    _activateIrSensor();
  }
}
class SmartTelevision extends Television {
  void turnOn() {
    super.turnOn();
    _bootNetworkInterface();
    _initializeMemory();
    _upgradeApps();
  }
}
```





#### 使用 Mixin 为类添加功能
`Mixin`是一种在多重继承中复用某个类中代码的方法模式。
使用`with`关键字并在其后跟上`Mixin`类的名字来使用`Mixin`模式：
``` dart
class Musician extends Performer with Musical {
  // ···
}

class Maestro extends Person
    with Musical, Aggressive, Demented {
  Maestro(String maestroName) {
    name = maestroName;
    canConduct = true;
  }
}
```
定义一个类继承自`Object`并且不为该类定义构造函数，这个类就是 `Mixin`类，除非你想让该类与普通的类一样可以被正常地使用，否则可以使用关键字`mixin`替代`class`让其成为一个单纯的`Mixin`类：

``` dart
mixin Musical {
  bool canPlayPiano = false;
  bool canCompose = false;
  bool canConduct = false;

  void entertainMe() {
    if (canPlayPiano) {
      print('Playing piano');
    } else if (canConduct) {
      print('Waving hands');
    } else {
      print('Humming to self');
    }
  }
}
```
可以使用关键字`on`来指定哪些类可以使用该`Mixin`类，比如有 `Mixin`类 `A`，但是`A`只能被`B`类使用，则可以这样定义 `A：
``` dart
class Musician {
  // ...
}
mixin MusicalPerformer on Musician {
  // ...
}
class SingerDancer extends Musician with MusicalPerformer {
  // ...
}
```



#### Extension 方法
Dart 2.7 中引入的`Extension`方法是向现有库添加功能的一种方式。
这里是一个在 String 中使用 `extension `方法的样例，我们取名为 `parseInt()`，它在 `string_apis.dart` 中定义：
``` dart
extension NumberParsing on String {
  int parseInt() {
    return int.parse(this);
  }

  double parseDouble() {
    return double.parse(this);
  }
}
```
然后使用`string_apis.dart`里面的`parseInt()`方法
``` dart
import 'string_apis.dart';
print('42'.padLeft(5)); // Use a String method.
print('42'.parseInt()); // Use an extension method.
```

![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
