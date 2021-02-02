---
title: 【Flutter 3-3】Flutter进阶教程——http请求和FutureBuilder
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-02-02 11:30:11
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter 异步
  - Flutter await
  - Flutter FutureBuilder
  - Flutter async
categories: Flutter
keywords: Flutter 异步，Flutter await， Flutter FutureBuilder，async
description: 在移动开发过程中很多时候我们都需要依赖异步请求数据然后再来刷新UI。在用户打开界面的时候，先给出一个Loading提示，等数据请求完成后，我们再把数据展示在页面上，这是很常见的操作。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### 异步请求
在移动开发过程中很多时候我们都需要依赖异步请求数据然后再来刷新UI。在用户打开界面的时候，先给出一个Loading提示，等数据请求完成后，我们再把数据展示在页面上，这是很常见的操作。  

异步请求的好处就是不会阻塞主线程，用户虽然在“等”，但是页面不会卡死。
同步请求不适应于这种情况，同步请求会出现页面卡死现象，此时用户不能点击(即使点击也没有效果)，体验非常不好。
所以大多数时候我们都是使用异步请求来获取数据

### http 库
在Flutter中，我们可以用[http库](https://pub.dev/packages/http)来做网络请求，它支持异步请求，并且有良好的API接口
使用http库的步骤：
- 在项目中，打开`pubspec.yaml`文件
- 找到`dependencies`字段，在下面添加`http: ^0.12.2`，其中`0.12.2`是版本号
- 然后保存`pubspec.yaml` 并执行`pub get`命令把我们要使用的第三方库下载下来  

> 具体 `pub get`命令的使用在之前的[文章](http://fulade.me/dart-pub-command-1-15.html)有介绍过 

![2021_02_02_http_request_yaml](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_02_02_http_request_yaml.jpg)

然后在要使用http库的文件里面引入头文件
``` dart
import 'package:http/http.dart' as http;
```
发送http请求的代码也比较简单，我们这里以`get`请求为例
``` dart
http.get("https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/request_demo_test.json");
```
只要传入要请求的地址即可，这里的URL地址是我自己上传的测试文件。

### http 异步请求返回结果
前面我知道http库发送请求是支持异步的，那么异步请求的返回结果我们该如何接收呢？
- 通过`then`函数获取，在`get`请求之后我们可以直接跟上`then`函数来作为回调，在回调内部可以获取到请求的结果
``` dart
http.get(getURL).then((value) {
  print(value);
});
```
这样写确实很方便，但当我们的网络请求很多，并且一个网络请求依赖另外一个网络请求的时候，这个时候就会多个回调函数嵌套在一起(又称为`回调地狱`)，代码就会显得很凌乱，很不适合Debug。
- 使用`await`来接收异步操作的结果
``` dart
var data = await http.get(getURL);
```
这样写代码就比上面的代码清爽多了
但是需要注意的是，如果函数内部有被`await`修饰的方法，那么函数应该被`async`来修饰，并且返回值需要被`Future`修饰，`Future`是一个延时计算的对象，在被`await`修饰的函数返回的时候才能拿到`Future`的具体值。
示例入下：
``` dart
Future<Map> getData() async {
  var data = await http.get(getURL);
  return data.body; 
}
```

### 刷新页面
我们前面已经知道：调用`setState()`函数可以刷新页面，所以在http请求之后我们调用`setState()`函数即可刷新页面
``` dart
http.get(getURL).then((value) {
  print(value);
  var data = jsonDecode(data.body);
  setState(() {
    /// 此处执行刷新页面的代码
  });
});
```

### 使用FutureBuilder来刷新页面
`setState()`固然是可以刷新页面，但是当我们页面内有多个网络请求的时候，就会不停的调用`setState()`来全量刷新页面，显然这就有点冗余。
Flutter为我们提供了更好的方式来实现获取数据并且刷新UI的操作，那就是`FutureBuilder`
来看它的初始化方法
``` dart
const FutureBuilder({
  /// key
  Key key,
  /// 异步的操作
  this.future,
  /// 初始化数据
  this.initialData,
  /// 构建UI的函数
  @required this.builder,
}) 
```
由构造函数可见，我们需要传入`future`参数，也就是我们的耗时操作函数，还需要传入`builder`函数   
在`builder`方法里可以捕捉到两个参数`BuildContext context`和`AsyncSnapshot snap`
其中`snap`的属性会携带`future`的耗时函数的返回值，也就是说：在耗时操作函数返回结果之后，我们可以在`builder`方法内获取到这一返回值。
所以上面的请求我们也可以这么来实现:
``` dart
FutureBuilder(
  future: getData(),
  builder: (BuildContext context, AsyncSnapshot snap) {
    /// 如果没有数据 我们就显示loading页面
    if (snap.hasData == false) {
      return CircularProgressIndicator();
    } else {
    /// 如果获取到了数据 我们就初始化一个 ListView来展示获取到的数据
      var dataSource = snap.data["tracks"];
      return ListView.builder(
        itemCount: dataSource.length,
        itemBuilder: (context, index) {
          return ListTile(
            title: Text(dataSource[index]["title"]),
            subtitle: Text(dataSource[index]["cover"]),
          );
        },
      );
    }
  },
),
```
在获取到数据之后，我们通过`ListView.builder`来构建一个`ListView`并返回，此时就完成了刷新UI的工作

我这里写的比较简单，只是用`hasData`来做为判断的依据
其实还有更优雅的做法：使用`snap`的另一个属性`connectionState`
``` dart
enum ConnectionState {
  /// 没有异步任务，
  none,
  /// 异步任务正在等待
  waiting,
  /// 异步任务正在执行 或者 数据正在传输
  active,
  /// 异步任务已经终止.
  done,
}
```
我们也可以在`connectionState`是`done`的时候在来判断是否存在数据
如果存在就展示数据！




想体验以上的示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`http_page.dart`查看，并且可以下载下来运行并体验。

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
