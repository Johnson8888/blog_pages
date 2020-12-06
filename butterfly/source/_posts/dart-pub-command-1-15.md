---
title:【Flutter 1-15】Flutter手把手教程Dart语言——包管理工具Pub详解、pub get,pub cache使用
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-06 16:26:38
cover: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
tags:
  - Dart语言
  - Dart pub
  - Flutter教程
  - Flutter pub使用
categories: Flutter
keywords: Dart语言，Dart import，Flutter教程，Dart包管理，Flutter pub使用，dart pub
description: 不管是在客户端还是后端，开发过程中总是需要引用一些第三方库，想iOS端的CocoaPods,Android端的Gradle和Maven。同样的开发Flutter也有这种工具，它的名字叫：Pub工具。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

#### 什么是Pub工具
Dart 生态系统使用包来管理共享软件，比如：库和工具。我们使用Pub包管理工具 来获取Dart包。在[Pub](https://pub.flutter-io.cn/)上，可以找到公开可用的包。或者从本地文件系统或其他的位置，比如Git仓库，加载可用的包。无论包是从什么途径加载的， Pub 都会进行版本依赖管理，从而帮助我们获得版本兼容的软件包以及SDK。
**pub工具**包含管理 Package 、部署 Package 和部署命令行应用的命令。
Dart 包目录中至少包含一个pubspec文件。 
![2020_12_06_pubspec](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_12_06_pubspec.png)
pubspec 文件记录一些关于项目的依赖数据。此外还有一些其他数据比如：Dart 库，应用，资源，测试，图片，以及示例。

下面是一个 pubspec 的示例，示例中声明依赖了在 Pub 站点上托管的两个包（ js 和 intl ）：
``` yaml
name: my_app
dependencies:
  js: ^0.6.0
  intl: ^0.15.8
```

#### pub get
在项目中配置了pubspec文件后，就可以在项目根目录中执行`pub get`命令：
``` bash
 cd <path-to-my_app>
 pub get
```
`pub get`命令确定当前应用所依赖的包，并将它们保存到中央系统缓存（central system cache）中。如果当前应用依赖了一个公开包，Pub会从Pub站点 该包。对于一个Git依赖，Pub会Clone该Git仓库。
同样包括包的相关依赖也会被下载。例如，如果 js 包依赖 test 包， pub 会同时获取js包和test包。

Pub 会创建一个.packages 文件（位于应用程序的根路目录下），该文件将应用程序所依赖的每个包名相应的映射到系统缓存中的包。
![2020_12_06_packages](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_12_06_packages.png)

#### pub upgrade
第一次获取依赖时，Pub 会下载依赖及其兼容的最新版本。然后通过创建`lockfile` 锁定依赖，以始终使用这个版本。 Pub会在`pubspec`旁创建并存储一个名为`pubspec.lock`文件。它列出了使用的每个依赖包的指定版本（当前包或传递包的版本）。
![2020_12_06_pubspec_lock](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_12_06_pubspec_lock.png)
在开发项目中的每个人都能够使用所有相同版本的包。同样加入到 lockfile 可以保证部署的应用使用的是同一版本的代码。

如果已经准备更新依赖到最新版本，使用命令 pub upgrade ：
``` bash
pub upgrade
```
上面的命令用于重新生成 lockfile 文件，并使用最新可用版本的依赖包。如果仅升级某个依赖，可以在命令中指定需要升级的包：
``` bash
pub upgrade intl
```
上面的命令升级`intl`到最新版本，其它包不变。

**注意**`pub upgrade` 命令并非总是可以将所有的package更新到最新版本，原因是pubspec文件中的一些package之间有版本限制的冲突。

#### pub cache 
用于管理 Pub 的本地 Package 缓存。使用该命令你可以将一个 Package 添加至缓存，或者清除所有缓存的 Package 并重新安装。
你可以使用`pub cache add`命令将新的 Package 添加至缓存。也可以使用`pub cache repair` 命令将Package从缓存中清除并重新安装。

``` bash
pub cache add <package> [--version <constraint>] [--all]
pub cache repair
```
**选项**
``` bash

add <package>    # 在你的缓存中安装一个库。

--all   # 可选的选项。与 pub add 结合使用用于安装某个库的所有版本。

--version <constraint>  # 可选的选项。与 pub add 结合使用根据限制条件安装最适合的版本。
# 例如：pub cache add barback --version "<=0.8.0 <0.110"  如果省略掉 --version，Pub 会从已知的版本中挑选一个最适合的进行安装。

repair # 如果 Pub 缓存中的 Package 被修改坏了的。例如，有人不小心修改了依赖内的文件，但是不知道该如何修改回来。pub cache repair 命令可以对系统缓存中的所有 Package 执行重安装以修正篡改的问题。
```


#### pub deps 
该命令可以将 Package 的依赖图示打印输出到控制台。该图示中包括 Package 声明在 pubspec 文件中的**直接依赖**以及这些直接依赖所依赖的**间接依赖**。
``` bash
pub deps [--style=<style>] [--dev] [--no-dev] [--executables]
```

依赖信息默认以树状的形式打印输出。
例如，有个项目的pubspec文件中声明了如下依赖信息：
``` bash
dependencies:
  barback: ^0.15.2
  markdown: ^0.7.2
```
当你执行 pub deps 命令时则会看到项目的依赖图示如下：
``` bash
markdown_converter 0.0.0
|-- barback 0.15.2+6
|   |-- collection 1.1.2
|   |-- path 1.3.6
|   |-- pool 1.1.0
|   |   '-- stack_trace...
|   |-- source_span 1.2.0
|   |   '-- path...
|   '-- stack_trace 1.4.2
|       '-- path...
'-- markdown 0.7.2
```
**选项**

``` bash
--style=<style> 或 -s <style> ## 指定的样式输出格式。用于指定依赖项打印输出的样式。

# 共有 简洁、树状 和 列表 三种，默认是树状样式。

# tree 以树状的形式打印依赖信息。这是默认格式。

# list 以列表的形式打印依赖信息。

# compact 以紧凑列表的形式打印依赖信息。

--dev # 打印所有包依赖信息，包括开发时期依赖。它是默认选项。

--no-dev #打印除了开发期依赖之外的所有包依赖。

--executables #打印所有可用的可执行文件。

```

#### pub downgrade
在没有其它额外参数的情况下，`pub downgrade`命令会获取当前工作目录下 pubspec.yaml 文件中列出的所有依赖项以及它们间接依赖项的**最低**版本。
``` bash
pub downgrade [--[no-]offline] [-n|--dry-run] [dependencies...]
```
例如：
``` bash
$ pub downgrade
Resolving dependencies... (1.2s)
+ barback 0.13.0
+ collection 0.9.1
+ path 1.2.0
+ source_maps 0.9.0
+ source_span 1.0.0
+ stack_trace 0.9.1
Changed 6 dependencies!
```
`pub downgrade` 命令会创建一个`lockfile`文件。如果`lockfile`文件已经存在，Pub 则会忽略该文件并生成一个新的`lockfile` 文件，然后所有依赖项都会使用最低版本。

**降级指定依赖项**
你可以指定`pub downgrade`命令只将某个依赖项的版本降至最低且不影响其余依赖项。例如：
``` bash
$ pub downgrade test
Resolving dependencies...
  barback 0.15.2+2
  bot 0.27.0+2
  browser 0.10.0+2
  chrome 0.6.5
  collection 1.1.0
  path 1.3.0
  pool 1.0.1
  source_span 1.0.2
< stack_trace 0.9.2 (was 1.1.1)
  stagexl 0.10.2
< test 0.10.0 (was 0.11.4)
These packages are no longer being depended on:
- matcher 0.11.3
Changed 3 dependencies!
```
如果你降低指定依赖项的版本，且该依赖项还有间接依赖项，那么在版本变更后这些间接依赖项可能不适配降低后的新版依赖项。此时，Pub 会尝试在新版本依赖项可接受的范围内查找版本最高的该依赖项所依赖的间接依赖项。因此，通常而言，降低某个依赖项的版本后，其间接依赖项的版本也会随之降低。
**获取新的依赖项**
如果在执行`pub downgrade`命令前将某个依赖添加至 pubspec 文件中，则在执行该命令后会将该新的依赖项以及其间接依赖的其它依赖项下载并将其放到 .packages 文件中。这点与 `pub get` 命令一致。

**移除依赖项**
如果在 `pub downgrade` 命令前从 pubspec 文件移除了某个依赖项，则在执行该命令后会将该依赖项从 .packages 文件中移除，且代码使用到该依赖项的相关导入将变得不可用。所有该依赖项依赖的间接依赖项也同时会被移除，只要这些间接依赖项没有没其它的依赖项所依赖。这点也与`pub get` 命令一致。

**离线降级**
在没有网络的情况下你也依然可以运行`pub downgrade` 命令。因为 Pub 会将 Package 下载到一个统一的缓存区并将其与系统上其它的 Package 进行共享，如果你所需的 Package 是一个使用频率很高的 Package，那么很有可能它已经被其它 Package 在使用时下载到统一缓存区中了，此时你可以直接依赖使用它。

但是，默认情况下，`pub downgrade` 命令会总是尝试获取线上的依赖版本，因此 Pub 可以确定依赖项是否有更新的版本。如果你不想 Pub 去线上检查，可以使用 `--offline` 命令参数让该命令在离线模式下执行。在离线模式下，Pub 只会从本地缓存区查找已经下载到的可用 Package。


**选项**
``` bash
--[no-]offline # 默认情况下，pub 将会通过网络检查（--no-offline）。要使用缓存的包，请使用 --offline。
--dry-run 或 -n #报告将要改变的依赖项，但不会真的改变它。
```


#### pub publish
``` bash
pub publish [--dry-run] [--force]
```
该命令用于将你的 Package 发布到[pub.dev](https://pub.dev/)网站以供其他人下载和依赖。
**选项**
``` bash
--dry-run 或 -n #该选项可以让你运行上传 Package 的整个流程但不会真正地上传任何文件到 pub.dev 网站。此操作可以让你在真正上传到 pub.dev 网站前检查你的上传等相关配置是否有误。

--force 或 -f  #该选项让 Pub 在上传时不再向你进行确认。正常情况下，它会在你上传时向你显示 Package 的内容以及向你进行确认。
```
如果 Package 存在错误，Pub 则会退出且不继续进行上传。如果出现的是警告，则 Package 会依旧被上传。如果你想确保你的 Package 在上传前没有警告，请确保不要使用 `--force` 和 `--dry-run` 选项。


#### pub uploader
``` bash
pub uploader [options] {add/remove} <email>
```
该命令允许`pub.dev`网站上某个 Package的上传者为该Package添加或删除其它的上传者。其有两个子命令`add`和`remove`，可以将邮件地址作为某个上传者的标识以此来添加或删除上传者。例如：
``` bash
pub uploader add bob@example.com # 我们已经向 bob@example.com 发送了一份邀请函，在他/她确认后就会成被加入上传者（权限）
```

``` bash
pub uploader remove bob@example.com # // 成功将该上传者从 package 中移除
```

如果 Package 有且只有一个上传者，则该上传者不能再被删除。你可以将自己从上传者列表中删除（只要 Package 中还有其它的上传者即可），但是一旦你删除了自己后则不能再将自己添加回去。

默认情况下，你修改的是当前工作目录中 Package 的上传者。你可以通过 --package 标识来指定修改哪个 Package 的上传者。例如：
``` bash
pub uploader --package=transmogrify add bob@example.com 
 # // 我们已经向 bob@example.com 发送了一份邀请函，在他/她确认后就会成被加入上传者（权限）
```
通过 `pub uploader add <email>` 命令发送邀请，被邀请的用户必须**接受**。

#### 其他不常用的命令可参考：
**pub outdated** 使用方法参考：https://zhuanlan.zhihu.com/p/138638020
**pub global** 使用方法参考：https://www.jianshu.com/p/8a7f2cbac7a1

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)