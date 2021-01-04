---
title: 【Python 1-18】Python手把手教程之——异常处理、try-except、error
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-01-04 14:50:03
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
tags:
    - Python 异常
    - Python 错误处理
    - Python Error
    - Python Exceptions
categories: Python 
keywords: 'Python 异常，Python 错误处理，Python Error，Python Exceptions'
description: Python使用被称为异常的特殊对象来管理程序执行期间发生的错误。每当发生让Python不知 所措的错误时，它都会创建一个异常对象。如果你编写了处理该异常的代码，程序将继续运行; 如果你未对异常进行处理，程序将停止，并显示一个traceback，其中包含有关异常的报告。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)


### 异常
Python使用被称为异常的特殊对象来管理程序执行期间发生的错误。每当发生让Python不知 所措的错误时，它都会创建一个异常对象。如果你编写了处理该异常的代码，程序将继续运行; 如果你未对异常进行处理，程序将停止，并显示一个`traceback`，其中包含有关异常的报告。  
异常是使用`try-except`代码块处理的。`try-except`代码块让Python执行指定的操作，同时告诉Python发生异常时怎么办。使用了`try-except`代码块时，即便出现异常，程序也将继续运行: 显示你编写的友好的错误消息，而不是令用户迷惑的`traceback`。

##### 一个简单的异常：ZeroDivisionError
下面来看一种导致Python引发异常的简单错误。你可能知道不能将一个数字除以0，但我们还是让Python这样做吧:
``` py
print(5/0)
```
显然，Python无法这样做，因此你将看到一个`traceback`:
``` py
Traceback (most recent call last):
File "division.py", line 1, in <module>
print(5/0) 
ZeroDivisionError: division by zero
```
在上述traceback中，我们看到的错误`ZeroDivisionError`是一个异常对象。Python无法按你的要求做时，就会创建这种对象。在这种情况下，Python将停止运行程序，并指出引发了哪种异常，而我们可根据这些信息对程序进行修改。下面我们将告诉Python，发生这种错误时怎么办;这样， 如果再次发生这样的错误，我们就有备无患了。
#### 使用try-except代码块
当你认为可能发生了错误时，可编写一个`try-except`代码块来处理可能引发的异常。你让Python尝试运行一些代码，并告诉它如果这些代码引发了指定的异常，该怎么办。处理`ZeroDivisionError`异常的`try-except`代码块类似于下面这样:
``` py
try:
    print(5/0)
except ZeroDivisionError:
    print("You can't divide by zero!")
```
我们将导致错误的代码行`print(5/0)`放在了一个`try`代码块中。如果`try`代码块中的代码运行 起来没有问题，Python将跳过`except`代码块，如果`try`代码块中的代码导致了错误，Python将查找这样的`except`代码块，并运行其中的代码，即其中指定的错误与引发的错误相同。
在这个示例中，`try`代码块中的代码引发了`ZeroDivisionError`异常，因此Python指出了该如何解决问题的`except`代码块，并运行其中的代码。这样，用户看到的是一条友好的错误消息，而不是`traceback`:
``` py
You can't divide by zero!
```
如果try-except代码块后面还有其他代码，程序将接着运行，因为已经告诉了Python如何处理这种错误。下面来看一个捕获错误后程序将继续运行的示例。
#### 使用异常避免崩溃
发生错误时，如果程序还有工作没有完成，妥善地处理错误就尤其重要。这种情况经常会出 现在要求用户提供输入的程序中;如果程序能够妥善地处理无效输入，就能再提示用户提供有效输入，而不至于崩溃。
下面来创建一个只执行除法运算的简单计算器，我们把一下保存为`division.py`:
``` py
print("Give me two numbers, and I'll divide them.")
print("Enter 'q' to quit.")
while True:
    first_number = input("\nFirst number: ")
    if first_number == 'q':
        break
    second_number = input("Second number: ")
    if second_number == 'q':
        break
    answer = int(first_number) / int(second_number)
    print(answer)
```
这个程序提示用户输入一个数字，并将其存储到变量`first_number`中，如果用户输入的不是表示退出的`q`，就再提示用户输入一个数字，并将其存储到变量`second_number`中。接下来，我们计算这两个数字的商(即`answer`)。这个程序没有采取任何处理错误的措施，因此让它执行除数为0的除法运算时，它将崩溃:
``` py
Give me two numbers, and I'll divide them. Enter 'q' to quit.
First number: 5
Second number: 0
Traceback (most recent call last):
    File "division.py", line 9, in <module>
        answer = int(first_number) / int(second_number)
ZeroDivisionError: division by zero
```
程序崩溃可不好，但让用户看到`traceback`也不是好主意。不懂技术的用户会被它们搞糊涂， 而且如果用户怀有恶意，他会通过`traceback`获悉你不希望他知道的信息。例如，他将知道你的程序文件的名称，还将看到部分不能正确运行的代码。有时候，训练有素的攻击者可根据这些信息 判断出可对你的代码发起什么样的攻击。
#### else 代码块
通过将可能引发错误的代码放在`try-except`代码块中，可提高这个程序抵御错误的能力。错误是执行除法运算的代码行导致的，因此我们需要将它放到`try-except`代码块中。这个示例还包含一个`else`代码块，依赖于`try`代码块成功执行的代码都应放到`else`代码块中:
``` py
print("Give me two numbers, and I'll divide them.") print("Enter 'q' to quit.")
while True:
    first_number = input("\nFirst number: ") 
    if first_number == 'q':
        break
    second_number = input("Second number: ")
    try:
        answer = int(first_number) / int(second_number)
    except ZeroDivisionError: 
        print("You can't divide by 0!")
    else: 
        print(answer)
```
我们让Python尝试执行`try`代码块中的除法运算，这个代码块只包含可能导致错误的代码。依赖于`try`代码块成功执行的代码都放在`else`代码块中，在这个示例中，如果除法运算成功，我们就使用`else`代码块来打印结果。
`except`代码块告诉Python，出现`ZeroDivisionError`异常时该怎么办。如果`try`代码块因除零错误而失败，我们就打印一条友好的消息，告诉用户如何避免这种错误。程序将继续运行，用户根本看不到`traceback`:
``` py
Give me two numbers, and I'll divide them.
Enter 'q' to quit.

First number: 5
Second number: 0
You can't divide by 0!

First number: 5 
Second number: 2 
2.5

First number: q
```

`try-except-else`代码块的工作原理大致如下:Python尝试执行`try`代码块中的代码，只有可能引发异常的代码才需要放在`try`语句中。有时候，有一些仅在`try`代码块成功执行时才需要运行的代码;这些代码应放在`else`代码块中。`except`代码块告诉Python，如果它尝试运行`try`代码块中的代码时引发了指定的异常，该怎么办。  
通过预测可能发生错误的代码，可编写健壮的程序，它们即便面临无效数据或缺少资源，也能继续运行，从而能够抵御无意的用户错误和恶意的攻击。

#### 处理FileNotFoundError异常
使用文件时，一种常见的问题是找不到文件:你要查找的文件可能在其他地方、文件名可能不正确或者这个文件根本就不存在。对于所有这些情形，都可使用`try-except`代码块以直观的方式进行处理。
我们来尝试读取一个不存在的文件。下面的程序尝试读取文件`alice.txt`的内容，但我没有将这个文件存储在`alice.py`所在的目录中，我们将一下代码保存为`alice.py`:
``` py
filename = 'alice.txt'
with open(filename) as f_obj: 
    contents = f_obj.read()
```
Python无法读取不存在的文件，因此它引发一个异常:
``` py
Traceback (most recent call last): 
    File "alice.py", line 3, in <module>
        with open(filename) as f_obj:
FileNotFoundError: [Errno 2] No such file or directory: 'alice.txt'
```
在上述`traceback`中，最后一行报告了`FileNotFoundError`异常，这是Python找不到要打开的文件时创建的异常。在这个示例中，这个错误是函数`open()`导致的，因此要处理这个错误，必须将`try`语句放在包含`open()`的代码行之前:
``` py
filename = 'alice.txt'
try:
    with open(filename) as f_obj: 
        contents = f_obj.read()
except FileNotFoundError:
    msg = "Sorry, the file " + filename + " does not exist." 
    print(msg)
```
在这个示例中，try代码块引发`FileNotFoundError`异常，因此Python找出与该错误匹配的`except`代码块，并运行其中的代码。最终的结果是显示一条友好的错误消息，而不是`traceback`:
``` py
Sorry, the file alice.txt does not exist.
```
如果文件不存在，这个程序什么都不做，因此错误处理代码的意义不大。下面来扩展这个示例，看看在你使用多个文件时，异常处理可提供什么样的帮助。

> 本篇文章没有作业，下一篇我们讲解函数的高级用法


***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
