---
title: 【Python 1-3】Python的第一个程序 Hello World
tags:
  - Python
categories: Python
keywords: Python
toc: true
cover: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
thumbnail: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
date: 2020-10-20 22:15:45
---


##### **Hello World**
"Hello, World!" 程序是一个经典的，确立已久的传统电脑程序。"Hello, World!" 因为能展示一个语言的基本句法，因此常被用作初学者的第一个"简单但完整"的程序，并可以被用来测试编程环境。

下面我们将写出Python中的"Hello, World!"程序，并使用两种方式运行它。
<!--more-->    
<br>

##### **书写 Hello World程序**
首先我们打开VSCode，新建一个文件，想必大家也都知道了，`Python`的输出语句非常简单，我们只需要在新建的文件中写入如下一行代码就可以了
``` Python
print("hello world!")
```
然后使用快捷键`Ctrl+S`保存文件到`桌面`，文件名我们就命名为`hello_world.py`这样我们的Hello World程序就写完了！是不是很简单！
##### **使用 VSCode运行 hello_world.py**
然后点击右上角的`绿色三角按钮`运行，看到有控制台输出`hello world!`，我们的程序运行成功了！
![2020_10_17_vscode_run](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_17_vscode_run.png)
##### **使用命令行运行 hello_world.py**
我们打开`Windows PowerShell`，输入`cd .\Desktop` 按回车，这样就进入到`hello_world.py`所在的文件夹，接着再输入`python.exe .\hello_world.py`
看到有输出`hello world!`，我们用命令行工具也运行成功了！
![2020_10_17_command_run](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_17_command_run.png)
##### **两种运行方式的使用场景**
其实在日常工作中，我个人就是使用VSCode来开发，所以也是使用VSCode来运行和调试Python程序的，这样简单也方便，直接使用快捷键运行一下就可以了。
但是当我们的Python程序需要部署在一台没有安装任何IDE工具的机器上的时候，这个时候我们就可以使用命令行来启动我们的Python程序来运行。
同样的，当其他脚本想启动我们的Python程序的时候，大多数情况也是通过命令行工具来运行的。


#####  **视频教程**
<div style="position: relative; width: 100%; height: 0; padding-bottom: 75%;">
    <iframe src="//player.bilibili.com/player.html?aid=800034187&bvid=BV1My4y187ov&cid=247600869&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</div>

