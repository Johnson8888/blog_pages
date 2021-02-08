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
Flutter已经帮助我们封装了操作SQLite的库，它就是：[sqflite](https://pub.dev/packages/sqflite)


### 集成sqflite库
使用`sqflite`第三方库需要我们在`pubspec.yaml`文件先添加库的名字和版本号
在`dependencies`字段下添加：
``` yaml
sqflite: ^1.1.3
```
这里以`1.1.3`为例
添加完成后保存一下，VSCode默认会执行`pub get`帮我们把需要的库下载下来，同样我们也可以在项目根目录下执行`pub get`来手动拉取需要的库。

#### 1. 创建本地数据文件
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
这里传入前面获取到的数据库地址，版本号，和`onCreate`回调函数。
在`onCreate`回调内部判断是否存在我们需要使用的表名字，如果不存就执行创建数据库表的`sql`语句。

> 除了`onCreate`回调，还有`onUpgrade`、`onDowngrade`、`onOpen`等回调。另外一个参数`singleInstance`它表示当传入相同的数据库路径是否返回同一个的实例对象，默认是`true`

#### 2. 插入数据
鉴于`sqflite`帮我们做了很多工作，所以在使用基本的`增`、`删`、`改`、`查`也很简单
``` dart
  /// 插入数据
  Future<int> insertData(Map<String, dynamic> value) async {
    return await db.insert(tableName, value);
  }
```
只需要传入表名字和要插入的数据就行
我们再来看一下`insert`函数的其他参数
``` dart
Future<int> insert(String table, Map<String, dynamic> values,
      {String nullColumnHack, ConflictAlgorithm conflictAlgorithm});
```
- nullColumnHack 是在传入的插入数据是空的时候 起到作用的
如果插入数据为空：
若不添加nullColumnHack则sql语句最终的结果将会类似insert into tableName()values()，这是不允许的。
若添加上nullColumnHack则sql语句将会变成insert into tableName (nullColumnHack)values(null)，这是可以的。
- conflictAlgorithm 是一个枚举，当插入的数据出现冲突或错误时，我们该使用哪种策略，有以下几个值
``` dart
enum ConflictAlgorithm {
  rollback,
  abort,
  fail,
  ignore,
  replace,
}
```

#### 3. 删除数据
删除数据的代码如下
``` dart
  /// 删除一条数据
Future<int> deleteData(int id) async {
    return await db.delete(tableName, where: "id = ?", whereArgs: [id]);
}
```
来看一下详细的`delete`函数都有哪些参数:
``` dart
Future<int> delete(String table, {String where, List<dynamic> whereArgs});
```
- `table`是要删除数据所在的表的名字 例如：testTable
- `where`是一个字符串，表示的是要删除的表达语句 例如："id = ?"
- `whereArgs`是一个数组，是用来补充`where`语句里面的`?`参数的 例如：[2]
当我们传入上面示例参数后，要标的意思就是：要删除testTable 表内 id = 2 的数据

#### 4. 更新数据
删除数据代码如下
``` dart
Future<int> updateData(Map<String, dynamic> value, int id) async {
    return await db.update(
        tableName,
        value,
        where: "id = ?",
        whereArgs: [id],
    );
}
```
详细的`update`函数如下
``` dart
Future<int> update(String table, Map<String, dynamic> values,
      {String where,
      List<dynamic> whereArgs,
      ConflictAlgorithm conflictAlgorithm});
```
跟`insert`函数的参数基本一致，这里就不赘述了

#### 5. 查询数据
直接来看查询语句的参数
``` dart
Future<List<Map<String, dynamic>>> query(
    String table,  /// 表名字 是必传参数
    {bool distinct,  // 是否包含重复数据
    List<String> columns,  // 需要查询的列
    String where,       //  查询条件
    List<dynamic> whereArgs, // 查询条件参数
    String groupBy,  //按列分组 列的名字
    String having,   // 给分组设置条件
    String orderBy,   // 按列排序 asc/desc
    int limit,     // 限制查询结果数量
    int offset});  // 从第几条开始查询
```
查询语句的参数比较丰富，基本可以满足我们一些复杂场景的查询需求

好了，关于`sqflite`的使用就总结这些了。

想体验以上的示例的运行效果，可以到[我的Github仓库](https://github.com/Johnson8888/learn_flutter)项目`flutter_app`->`lib`->`routes`->`sqflite_page.dart`查看，并且可以下载下来运行并体验。
***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
