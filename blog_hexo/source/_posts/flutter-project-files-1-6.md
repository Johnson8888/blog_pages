---
permalink: flutter-project-files-1-6.html
title: 【Flutter 1-6】Flutter项目目录结构
date: 2020-10-25 15:14:47
toc: true
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
categories: Flutter
tags:
    - Flutter
---

##### **Flutter项目结构**
了解Flutter的目录结构，可以帮助我们更好的管理和开发项目。这样我们在开发的过程中就会很清楚的知道，iOS代码该放在那里，Android代码该放在那里，Flutter代码该放在哪里，测试代码放在哪里等等。
<!--more-->
我们以[上一节](http://fulade.me/2020/10/25/flutter-hello-word-1-5/)中创建的`flutter_app`为例，我们用VSCode打开它。 
![2020_10_25_vscode_main_dart](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_10_25_vscode_main_dart.png)
如图，我们看到了下面这些目录：  



| 文件或目录 | 说明 |
| ------ | ------ |
| .dart_tool | 记录了一些dart工具库所在的位置和信息 |
|.idea | android studio 是基于idea开发的，.idea 记录了项目的一些文件的变更记录 |
| android | Android项目文件夹 |
| ios | iOS项目文件夹 |
| lib | lib文件夹内存放我们的dart语音代码 |
| test | 用于存放我们的测试代码 |
| .gitignore | git忽略配置文件 |
| .metadata | IDE 用来记录某个 Flutter 项目属性的的隐藏文件 |
| .packages | pub 工具需要使用的，包含 package 依赖的 yaml 格式的文件 |
| flutter_app.iml | 工程文件的本地路径配置 |
| pubspec.lock | 当前项目依赖所生成的文件 |
| pubspec.yaml | 当前项目的一些配置文件，包括依赖的第三方库、图片资源文件等 |
| README.md | READEME文件 |



##### **比较重要的四个文件夹是 android、ios、lib、test**
- lib 
我们日常开发的dart语言代码都放在这里，可以说是我们的“核心工作文件夹”
- ios
这里面包含了iOS项目相关的配置和文件，当我们的项目需要打包上线的时候，需要打开该文件内的`Runner.xcworkspace`文件进行编译和打包工作。
- android 
与`ios`文件夹一样，在android项目需要打包上架的时候，也需要使用此文件夹里面的文件。同样的如果我们需要原生代码的支持，原生代码也是放在这里。
- test
这里存放了我们在项目开发过程中的测试代码，良好的测试习惯是保证代码质量的必要手段，希望大家在`test`文件里写更多的代码！


***  
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)