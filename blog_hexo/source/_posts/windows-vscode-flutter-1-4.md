---
permalink: windows-vscode-flutter-1-4.html
title: 【Flutter 1-4】Windows下VSCode配置Flutter开发环境
tags:
  - Flutter
toc: true
cover: https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/page_conver_flutter_blue.jpeg
categories: Flutter
date: 2020-10-11 22:53:24
---

##### **VSCode是什么**
Visual Studio Code（简称VS Code）是一个由微软开发，同时支持Windows 、 Linux和macOS等操作系统的免费代码编辑器，它支持测试，并内置了Git 版本控制功能，同时也具有开发环境功能，例如代码补全（类似于 IntelliSense）、代码片段和代码重构等。该编辑器支持用户个性化配置，例如改变主题颜色、键盘快捷方式等各种属性和参数，同时还在编辑器中内置了扩展程序管理的功能。VSCode同样支持Flutter开发，在我的日常开发中会更多的使用VSCode，而不是Android Studio。
<!--more-->
##### **下载和安装VSCode**
打开[VSCode官方网站](https://code.visualstudio.com/)
![2020_10_09_download_vscode](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_10_09_download_vscode.png)
下在完成后双击`exe`文件进行安装并打开。
打开后找到`Extensions`或使用快捷键`Ctrl+Shift+X`打开扩展中心。
在扩展中心输入`flutter`，显示的第一个便是我们要安装的Flutter扩展程序，点击安装。
![2020_10_09_vscode_flutter](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_10_09_vscode_flutter.png)

##### **新建项目**
安装完成之后依次点击`View`->`Command Palette...`(或者是使用快捷键`Ctrl+Shift+P`)
![2020_10_09_vscode_command](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_10_09_vscode_command.png)
在弹出的输入框中输入关键字`flutter`然后回车，选择项目要保持的目录，输入项目名称就可以了。
![2020_10_09_vscode_new_flutter](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_10_09_vscode_new_flutter.png)
注意：创建项目完成之后，VSCode会帮助我们来安装`Dart`语言相关的依赖。
这样我们在VSCode下配置Flutter环境就算完成了。



##### 视频教程
<div style="position: relative; width: 100%; height: 0; padding-bottom: 75%;">
    <iframe src="//player.bilibili.com/player.html?aid=287403050&bvid=BV1gf4y1B7yJ&cid=245689967&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;">
    </iframe>
</div>