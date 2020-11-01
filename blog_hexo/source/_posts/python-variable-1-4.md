---
title: 【Python 1-4】Python教程之——变量
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
cover: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
thumbnail: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
toc: true
comments: true
tags:
  - Python
keywords: Python变量,Python教程,大学生学Python
categories: Python
date: 2020-10-30 23:14:12
description:
photos:
fileName:
type:
---
> 变量来源于《数学》
是计算机语言中能储存计算结果或能表示值的抽象概念。

##### **运行hello_world.py时发生了什么**
运行hello_world.py时，Python都做了些什么呢?下面来深入研究一下。实际上，即便是运行简单的程序，Python所做的工作也相当多:
```Python
print("Hello Python World!")
```
运行上述代码代码时，你将看到如下输出：
``` Python
Hello Python World!
```
<!--more-->
运行文件hello_world.py时，末尾的.py指出这是一个Python程序，因此编辑器将使用Python解释器来运行它。
Python解释器读取整个程序，确定其中每个单词的含义。例如，看到单词`print`时，解释器就会将括号中的内容打印到屏幕，而不会管括号中的内容是什么。
编写程序时，编辑器会以各种方式突出程序的不同部分。例如，它知道print是一个函数的名称，因此将其显示为蓝色；它知道"Hello Python world!"不是Python代码，因此将其显示为另一种颜色。这种功能称为`语法突出`。

##### **变量**
下面来尝试在hello_world.py中使用一个变量。在这个文件开头添加一行代码，并对代码进行修改，修改如下：
``` Python
message = "Hello Python world!" 
print(message) 
```
运行这个程序，看看结果如何。你会发现，输出跟前面一样：
`Hello Python world! `
我们添加了一个名为`message`的变量。每个变量都存储了一个值——与变量相关联的信息。
在这里，存储的值为文本"Hello Python world!"。
添加变量导致Python解释器需要做更多工作。处理第1行代码时，它将文本"Hello Python world!"与变量`message`关联起来；而处理第2行代码时，它将与变量`message`关联的值打印到屏幕。

下面来进一步扩展这个程序：修改hello_world.py，使其再打印一条消息。为此，在
`hello_world.py`中添加一个空行，再添加下面两行代码：
``` Python
message = "Hello Python world!" 
print(message)
message = "Hello Python Crash Course world!" 
print(message) 
```
现在如果运行这个程序，将看到两行输出：
```
Hello Python world! 
Hello Python Crash Course world! 
```
在程序中可随时修改变量的值，而Python将始终记录变量的最新值。

##### **变量的命名**
我们在命名变量的是应该遵循一定的规则，不能想怎么写就怎么写，简单来说有以下几个规则：


- 变量名只能包含字母、数字和下划线。变量名可以字母或下划线打头，但不能以数字打
头，例如，可将变量命名为message_1，但不能将其命名为1_message。 
- 变量名不能包含空格，但可使用下划线来分隔其中的单词。例如，变量名greeting_message
可行，但变量名greeting message会引发错误。
- 不要将Python关键字和函数名用作变量名，即不要使用Python保留用于特殊用途的单词，如`print`。

- 变量名应既简短又具有描述性。例如，name比n好，student_name比s_n好，name_length
比length_of_persons_name好。
- 慎用小写字母l和大写字母O，因为它们可能被人错看成数字1和0。    

要创建良好的变量名，需要经过一定的实践，在程序复杂而有趣时尤其如此。随着我们写的代码越来越多，并开始阅读别人编写的代码，将越来越善于创建有意义的变量名。


>小作业
请完成下面的练习，在做每个练习时，都编写一个独立的程序。保存每个程序时，使用符合标准 Python 约定的文件名：使用小写字母和下划线，如 simple_message.py 和simple_messages.py。
1-1 简单消息：将一条消息存储到变量中，再将其打印出来。
1-2 多条简单消息：将一条消息存储到变量中，将其打印出来；再将变量的值修改
为一条新消息，并将其打印出来。

想查看作业答案可以去[我的Githu仓库](https://github.com/Johnson8888/learn_python)

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)