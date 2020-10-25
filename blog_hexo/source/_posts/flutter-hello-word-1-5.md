---
title: 【Flutter 1-5】运行Flutter的第一个项目——计数器
tags:
  - Flutter
toc: true
cover: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
categories: Flutter
date: 2020-10-25 21:06:04
---


##### **创建项目**
创建Flutter项目有很多种方法，各个IDE工具也都集成了创建Flutter项目的快捷操作。我们这里列举三种方式：使用命令行创建、使用Android Studio创建和使用VSCode创建。
<!--more-->


- 使用命令行创建
在Flutter安装完之后，我们就已经配置好了命令行工具，命令行工具很强大，可以满足我们日常开发Flutter的所有操作（如果你还没有安装好Flutter环境，可以参考[这里](http://fulade.me/2020/09/28/windows-install-flutter/)来安装）。
我们只需要打开命令行工具 输入:
    ``` bash
    flutter create flutter_app
    ```
    其中 `flutter_app`是我们项目的名字。
- 使用 Android Studio 创建
我们打开 Android Studio，点击左上角 `File`->`New`->`New Flutter Project` 即可。
![2020_10_25_android_create](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_10_25_android_create.png)
- 使用 VSCode创建
 点击VSCode上方按钮 `View`->`Command Palette..`
![2020_10_25_vscode_view.png](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_10_25_vscode_view.png)
然后在弹出的输入框内输入关键字`flutter`回车就可以了创建项目了。
![2020_10_25_vscode_flutter](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_10_25_vscode_flutter.png)

#### **使用Android Studio 运行 计数器项目**
用 Android Studio打开我们刚刚创建的项目`flutter_app`
打开之后我们先选择一下模拟器，然后直接点击运行就可以了。
![2020_10_25_android_select_device](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_10_25_android_select_device.png)

#### **使用VSCode 运行 计数器项目**
用VSCode打开项目`flutter_app`，找到目录下的 `main.dart`文件打开
![2020_10_25_vscode_main_dart](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_10_25_vscode_main_dart.png)
然后点击右上角运行按钮就可以了。
![2020_10_25_vscode_run](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_10_25_vscode_run.png)

