---
title: 【Flutter 1-13】Flutter手把手教程Dart语言——异步、Future、Stream、async、await详解
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
cover: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
toc: true
comments: true
tags:
  - Dart语言
  - Dart异步
  - Flutter教程
  - Dart类
  - Dart Future
categories: Flutter
keywords: Dart语言，Dart Future，Flutter教程，Dart异步，Dart类
description: >-
  Dart代码库中有大量返回Future或Stream对象的函数，这些函数都是异步的，它们会在耗时操作（比如I/O）执行完毕前直接返回而不会等待耗时操作执行完毕。
date: 2020-12-05 20:16:27
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

## 异步
Dart 代码库中有大量返回`Future`或`Stream`对象的函数，这些函数都是**异步**的，它们会在耗时操作执行完毕前直接返回而不会等待耗时操作执行完毕。
`async`和`await`关键字用于实现异步编程，并且让你的代码看起来就像是同步的一样。


#### Future
可以通过下面两种方式，获得`Future`执行完成的结果：
- 使用`async`和`await`；
- 使用`Future API`；

使用`async`和`await`的代码是异步的，但是看起来有点像同步代码。例如，下面的代码使用`await`等待异步函数的执行结果。
``` dart
await lookUpVersion();
```
必须在带有`async`关键字的**异步函数**中使用 `await`：
``` dart
Future checkVersion() async {
  var version = await lookUpVersion();
  // 使用 version 继续处理逻辑
}
```
尽管异步函数可以处理耗时操作，但是它并不会等待这些耗时操作完成，异步函数执行时会在其遇到第一个 `await`表达式的时候返回一个`Future`对象，然后等待`await`表达式执行完毕后继续执行。

使用`try`、`catch`以及`finally`来处理使用`await`导致的异常：
``` dart
try {
  version = await lookUpVersion();
} catch (e) {
  // 无法找到版本时做出的反应
}
```
你可以在异步函数中多次使用`await`关键字。例如，下面代码中等待了三次函数结果：
``` dart
var entrypoint = await findEntrypoint();
var exitCode = await runExecutable(entrypoint, args);
await flushThenExit(exitCode);
```
`await`表达式的返回值通常是一个`Future`对象；
如果不是的话也会自动将其包裹在一个`Future`对象里。`Future`对象代表一个"承诺",`await`表达式会阻塞直到需要的对象返回。

如果在使用`await`时导致编译错误，请确保`await`在一个异步函数中使用。例如，如果想在`main()`函数中使用`await`，那么`main()`函数就必须使用`async`关键字标识。
``` dart
Future main() async {
  checkVersion();
  print('在 Main 函数中执行：版本是 ${await lookUpVersion()}');
}
```
#### 声明异步函数
定义**异步函数**只需在普通方法上加上`async`关键字即可。
将关键字`async`添加到函数并让其返回一个`Future` 对象。假设有如下返回`String`对象的方法：
``` dart
String lookUpVersion() => '1.0.0';
```
将其改为异步函数，返回值是`Future`：
``` dart
Future<String> lookUpVersion() async => '1.0.0';
```
注意，函数体不需要使用`Future API`。如有必要，`Dart`会创建`Future`对象。
如果函数没有返回有效值，需要设置其返回类型为 `Future<void>`
#### Stream
`Stream`也是用于接收异步事件数据，和`Future`不同的是，它可以接收多个异步操作的结果（成功或失败）。 也就是说，在执行异步任务时，可以通过多次触发成功或失败事件来传递结果数据或错误异常。`Stream`常用于会多次读取数据的异步任务场景，如网络内容下载、文件读写等。举个例子：
``` dart
Stream.fromFutures([
  // 1秒后返回结果
  Future.delayed(new Duration(seconds: 1), () {
    return "hello 1";
  }),
  // 抛出一个异常
  Future.delayed(new Duration(seconds: 2),(){
    throw AssertionError("Error");
  }),
  // 3秒后返回结果
  Future.delayed(new Duration(seconds: 3), () {
    return "hello 3";
  })
]).listen((data){
   print(data);
}, onError: (e){
   print(e.message);
},onDone: (){

});
```
上面的代码依次会输出：
``` dart
hello 1
Error
hello 3
```

![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)