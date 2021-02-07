---
title: 【Flutter 3-3】Flutter进阶教程——数据持久化sqflite使用
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-02-07 16:16:13
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Flutter sqflite
  - Flutter 数据库
  - Flutter 数据持久化
  - Flutter sqlite
categories: Flutter
keywords: Flutter sqflite，Flutter 数据库， Flutter 数据持久化，sqlite
description: 数据持久化是在移动端开发中必不可少的技术手段。我们总是有一些用户信息，应用资源，列表数据等需要存储起来，这里我们主要来讲基于SQLite数据库的数据储存。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)


### sqflite
数据持久化是在移动端开发中必不可少的技术手段。我们总是有一些用户信息，应用资源，列表数据等需要存储起来，这里我们主要来讲基于SQLite数据库的数据储存。
SQLite，是一款轻型的数据库。它的设计目标是嵌入式的，而且已经在很多嵌入式产品中使用了它，它占用资源非常的低，在嵌入式设备中，可能只需要几百K的内存就够了。更多详细信息可以参考:[维基百科](https://zh.wikipedia.org/wiki/SQLite)、[百度百科](https://baike.baidu.com/item/SQLite)。
Flutter已经帮助我们封装好了操作SQLite的库，它就是：[sqflite](https://pub.dev/packages/sqflite)


### 集成sqflite库
使用`sqflite`第三方库需要我们在`pubspec.yaml`文件先添加库的版本已经名字
在`dependencies`字段下添加：
``` yaml
sqflite: ^1.1.3
```
这里以`1.1.3`为例
添加完成后保存一下，VSCode默认会执行`pub get`帮我们把需要的库下载下载，同样我们可以在项目根目录下执行`pub get`来拉取需要的库。

#### 1.创建本地数据文件
``` dart
static Future<SqfliteManager> _initDataBase() async {
SqfliteManager manager = SqfliteManager();
String dbPath = await getDatabasesPath() + "/$sqlName";
if (manager.db == null) {
    manager.db = await openDatabase(
    dbPath,
    version: 1,
    onCreate: (db, version) async {
        /// 如果不存在 当前的表 就创建需要的表
        if (await manager.isTableExit(db, tableName) == false) {
        await db.execute(CREATE_DATA_TABLE);
        }
    },
    );
}
return manager;
}
```
首先我们通过`getDatabasesPath()`函数获取到本地保存数据库文件的路径，在此路径后面拼接上我们的数据库文件名字，就是保存数据库文件的路径。在iOS中该路径在沙河路径下的`Documents`文件夹内，在Android中时默认数据库目录。
之后我们声明一个`Database`对象，用来保存数据库操作对象
``` dart
Database db;
```
先判断此对象是否存在，如果不存在我们调用`openDatabase`来创建
这里传入前面获取到的数据库地址，版本号，和`onCreate`回调。
在`onCreate`回调内部判断是否存在我们需要使用的表名字，如果不存就执行创建数据库表的`sql`语句。

> 除了`onCreate`回调，还有`onUpgrade`、`onDowngrade`、`onOpen`等回调。另外一个参数`singleInstance`它表示当传入相同的数据库路径是否返回同一个的实例对象，默认是`true`
