---
title: 【Python 1-12】Python手把手教程之——用户输入input函数
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-20 14:58:45
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
tags:
    - Python input语句
    - Python input
categories: Python
keywords: Python input语句,Python input
description: 函数input()让程序暂停运行，等待用户输入一些文本。获取用户输入后，Python将其存储在一个变量中，以方便你使用。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### 函数input()
函数`input()`让程序暂停运行，等待用户输入一些文本。获取用户输入后，Python将其存储在一个变量中，以方便你使用。
例如，下面的程序让用户输入一些文本，再将这些文本呈现给用户:
``` py
message = input("Tell me something, and I will repeat it back to you: ")
print(message) 
```
函数`input(`)接受一个参数：即要向用户显示的提示或说明，让用户知道该如何做。在这个示例中，用户将看到提示`Tell me something, and I will repeat it back to you:`。程序等待用户输入，并在用户按回车键后继续运行。
输入存储在变量`message`中，接下来的`print(message)`将输入呈现给用户：
``` bash
Tell me something, and I will repeat it back to you: This is Fulade!
This is Fulade! 
```
每当你使用函数`input()`时，都应指定清晰而易于明白的提示，准确地指出你希望用户提供什么样的信息——指出用户该输入任何信息的提示都行，如下所示：
``` py
name = input("Please enter your name: ")
print("Hello, " + name + "!") 
```
通过在提示末尾（这里是冒号后面）包含一个空格，可将提示与用户输入分开，让用户清楚地知道其输入始于何处，如下所示：
``` bash
Please enter your name: Fulade
Hello, Fulade! 
```
#### int()函数
使用函数`input()`时，Python将用户输入解读为字符串。请看下面让用户输入其年龄的解释器会话
``` bash
>>> age = input("How old are you? ")
How old are you? 21
>>> age
'21' 
```
用户输入的是数字21，但我们请求Python提供变量`age`的值时，它返回的是'21'——用户输入
的数值的字符串表示。我们怎么知道Python将输入解读成了字符串呢？因为这个数字用引号括起
了。  
如果我们只想打印输入，这一点问题都没有；但如果你试图将输入作为数字使用，就会引发错误：
``` py
>>> age = input("How old are you? ")
How old are you? 21
>>> age >= 18
Traceback (most recent call last):
 File "<stdin>", line 1, in <module>
TypeError: unorderable types: str() >= int()
```
你试图将输入用于数值比较时，Python会引发错误，因为它无法将字符串和整数进
行比较：不能将存储在`age`中的字符串'21'与数值18进行比较。  
为解决这个问题，可使用函数`int()`，它让Python将输入视为数值。函数`int()`将数字的字符
串表示转换为数值表示，如下所示：
``` py
>>> age = input("How old are you? ")
How old are you? 21
>>> age = int(age)
>>> age >= 18
True
```
在这个示例中，我们在提示时输入21后，Python将这个数字解读为字符串，但随后`int()`将这个字符串转换成了数值表示。  
这样Python就能运行条件测试了：将变量age（它现在包含数值21）同18进行比较，看它是否大于或等于18。测试结果为`True`。
如何在实际程序中使用函数`int()`呢？请看下面的程序，它判断一个人是否满足坐过山车的身高要求:
``` py
height = input("How tall are you, in inches? ")
height = int(height)
if height >= 36:
    print("\nYou're tall enough to ride!")
else: 
    print("\nYou'll be able to ride when you're a little older.") 
```
在这个程序中，为何可以将height同36进行比较呢？因为在比较前，height = int(height)
将输入转换成了数值表示。如果输入的数字大于或等于36，我们就告诉用户他满足身高条件：
``` bash
How tall are you, in inches? 71
You're tall enough to ride! 
```
将数值输入用于计算和比较前，务必将其转换为数值表示。


#### 使用while推出

可使用`while`循环让程序在用户愿意时不断地运行，我们在其中定义了一个退出值，只要用户输入的不是这个值，程序就可以接着运行:
``` py
prompt = "\nTell me something, and I will repeat it back to you:"
prompt += "\nEnter 'quit' to end the program. "
message = ""
while message != 'quit':
    message = input(prompt)
    print(message) 
```
我们定义了一条提示消息，告诉用户他有两个选择：要么输入一条消息，要么输
入退出值（这里为'quit'）。

接下来，我们创建了一个变量——`message`，用于存储用户
输入的值。我们将变量`message`的初始值设置为空字符串""，让Python首次执行`while`代码行时有可供检查的东西。

Python首次执行`while`语句时，需要将`message`的值与'quit'进行比较，但此时用户还没有输入。如果没有可供比较的东西，Python将无法继续运行程序。  

为解决这个问题，我们必须给变量`message`指定一个初始值。虽然这个初始值只是一个空字符串，但符合要求，让Python能够执行`while`循环所需的比较。只要`message`的值不是'quit'，这个循就会不断运行。


首次遇到这个循环时，`message`是一个空字符串，因此Python进入这个循环。执行到代码行`message = input(prompt)`时，Python显示提示消息，并等待用户输入。  

不管用户输入是什么，都 将存储到变量`message`中并打印出来；接下来，Python重新检查`while`语句中的条件。只要用户输入的不是单词`quit`，Python就会再次显示提示消息并等待用户输入。  

等到用户终于输入`quit`后，Python停止执行while循环，而整个程序也到此结束：

``` bash
Tell me something, and I will repeat it back to you:
Enter 'quit' to end the program. Hello everyone!
Hello everyone!
Tell me something, and I will repeat it back to you:
Enter 'quit' to end the program. Hello again. 
Hello again.
Tell me something, and I will repeat it back to you:
Enter 'quit' to end the program. quit
quit 
```
这个程序很好，唯一美中不足的是，它将单词`quit`也作为一条消息打印了出来。为修复这种问题，只需使用一个简单的if判断：
``` py
prompt = "\nTell me something, and I will repeat it back to you:"
prompt += "\nEnter 'quit' to end the program. "
message = ""
while message != 'quit':
    message = input(prompt)
    if message != 'quit':
        print(message) 
```
现在，程序在显示消息前将做简单的检查，仅在消息不是退出值时才打印它。





> 小作业 
12.1 编写一个程序，询问用户要咨询什么样的汽车，并打印一条消息，如"Let me see if I can find you a Subaru"。
12.2 餐馆订位：编写一个程序，询问用户有多少人用餐。如果超过 8 人，就打印一条消息，指出没有空桌；否则指出有空桌。
12.3 让用户输入一个数字，并指出这个数字是否是 10 的整数倍。

想查看作业答案可以去[我的Githu仓库](https://github.com/Johnson8888/learn_python)在文件夹**12-1_12-3**下
***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)