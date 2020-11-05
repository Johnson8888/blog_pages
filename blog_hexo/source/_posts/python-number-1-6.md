---
title: Python 1-6】Python教程之——数字
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-05 17:06:36
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_number.jpg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_number.jpg
tags:
    - Python
keywords: Python数字,Python自学教程,大学生学Python,Python教程
description:
photos:
fileName:
type:
---

> 数字是一种用来表示数的书写符号：
中文数字写作三十七、卅七
罗马数字写作XXXVII
阿拉伯数字二进制写作100101
<!--more-->
[文章首发地址](http://fulade.me/python-number-1-6.html)

#### **数字**
在编程中，经常使用数字来记录游戏得分、表示可视化数据、存储Web应用信息等。Python 根据数字的用法以不同的方式处理它们。我们平时最常见的就是整数，下面就先来看看Python是如何管理整数的。

##### **整数**
在Python中，可对整数执行加`+`减`-`乘`*`除`/`运算。
``` Python
>>> 2 + 3 
5
>>> 3 - 2 
1
>>> 2 * 3 
6
>>> 3 / 2 
1.5
```
在终端(命令行)会话中，Python直接返回运算结果。Python使用两个乘号表示乘方运算:
``` Python
>>> 3 ** 2 
9
>>> 3 ** 3 
27
>>> 10 ** 6 
1000000
```
Python还支持运算次序，因此你可在同一个表达式中使用多种运算。当然我们也可以使用括号来修改运算次序，让Python按你指定的次序执行运算，如下所示:
``` Python
>>> 2 + 3*4
14
>>> (2 + 3) * 4 
20
```
##### **浮点数**
Python将带小数点的数字都称为浮点数。大多数编程语言都使用了这个术语，它指出了这样 一个事实:小数点可出现在数字的任何位置。  
每种编程语言都须细心设计，以妥善地处理浮点数， 确保不管小数点出现在什么位置，数字的行为都是正常的。  
从很大程度上说，使用浮点数时都无需考虑其行为。你只需输入要使用的数字，Python通常都会按你期望的方式处理它们:
``` Python 
>>> 0.1 + 0.1
0.2
>>> 0.2 + 0.2 9 0.4
>>>2 * 0.1
0.2
>>>2 * 0.2
0.4
```
但需要注意的是，结果包含的小数位数可能是不确定的:
```Python
>>> 0.2 + 0.1 
0.30000000000000004 
>>> 3 * 0.1 
0.30000000000000004
```
所有语言都存在这种问题，没有什么可担心的。Python会尽力找到一种方式，以尽可能**精确**地表示结果，但鉴于计算机内部表示数字的方式，这在有些情况下很难。就现在而言，暂时忽略多余的小数位数即可。

##### **使用函数str()避免类型错误**
你经常需要在消息中使用变量的值。例如，假设你要祝别人生日快乐，可能会编写类似于下面的代码(将下面代码保存为`birthday.py`):
``` Python
age = 23
message = "Happy " + age + "rd Birthday!"
print(message)
```
你可能认为，上述代码会打印一条简单的生日祝福语:`Happy 23rd birthday!`。但如果你运行这些代码，将发现它们会引发错误:
``` Python
Traceback (most recent call last):
File "birthday.py", line 2, in <module>
message = "Happy " + age + "rd Birthday!"
TypeError: Can't convert 'int' object to str implicitly
```
这是一个类型错误，意味着Python无法识别你使用的信息。在这个示例中，Python发现你使 用了一个值为整数(int)的变量，但它不知道该如何解读这个值(见)。Python知道，这个变 量表示的可能是数值23，也可能是字符2和3。像上面这样在字符串中使用整数时，需要显式地指 出你希望Python将这个整数用作字符串。为此，可调用函数str()，它让Python将非字符串值表示 为字符串:
``` Python
age = 23
message = "Happy " + str(age) + "rd Birthday!"
print(message)
```
这样，Python就知道你要将数值23转换为字符串，进而在生日祝福消息中显示字符2和3。经 过上述处理后，将显示你期望的消息，而不会引发错误:
``` Python
Happy 23rd Birthday!
```
大多数情况下，在Python中使用数字都非常简单。如果结果出乎意料，请检查Python是否按 你期望的方式将数字解读为了数值或字符串。
>小作业
6-1 编写 4 个表达式，它们分别使用加法、减法、乘法和除法运算，但结果都是数字 `8`。
为使用 print 语句来显示结果，务必将这些表达式用括号括起来，也就是说，你应该编写4行类似于下面的代码:
`print(5 + 3)`
输出应为 4 行，其中每行都只包含数字8。命名为`eight.py`
6-2 将你最喜欢的数字存储在一个变量中，再使用这个变量创建一条消息，指出你最喜欢的数字，然后将这条消息打印出来。命名为`number.py`

想查看作业答案可以去[我的Githu仓库](https://github.com/Johnson8888/learn_python)


***
<center><strong>THE END</strong></center>

![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)