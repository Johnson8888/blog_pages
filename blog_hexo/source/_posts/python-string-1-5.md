---
title: 【Python 1-5】Python教程之——字符串
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-02 09:08:51
cover: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
thumbnail: >-
  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
tags:
    - Python
keywords: Python字符串,Python自学教程,大学生学Python
description:
photos:
fileName:
type:
---
> 字符串或串(String)是由数字、字母、下划线组成的一串字符。   

#### **字符串**
字符串就是一系列字符。在Python中，用引号括起的都是字符串，其中的引号可以是单引号， 也可以是双引号，如下所示:

``` Python
"This is a string."   
'This is also a string.'
```
这种灵活性让你能够在字符串中包含引号和撇号:
``` Python
'I told my friend, "Python is my favorite language!"'
"The language 'Python' is named after Monty Python, not the snake." 
"One of Python's strengths is its diverse and supportive community."
```
<!--more-->
#### **使用方法修改字符串的大小写**
对于字符串，可执行的最简单的操作之一是修改其中的单词的大小写。
请看下面的代码，并尝试判断其作用:
``` Python
name = "fulade blog" 
print(name.title())
```  
将这个文件保存为`name.py`，再运行它。你将看到如下输出:

```
Fulade Blog
```
在这个示例中，小写的字符串"fulade blog"存储到了变量name中。在`print()`语句中，方法 `title()`出现在这个变量的后面。在`name.title()`中，name后 面的句点(.)让Python对变量name执行方法`title()`的操作。每个方法后面都跟着一对括号， 这是因为方法通常需要一些参数来完成其工作。这些参数往往写在括号内的。方法`title()`不需要参数，因此它后面的括号是空的。
`title()`的实现结果是以首字母大写的方式显示每个单词，即将每个单词的首字母都改为大写。
还有几个其他的很有用的处理大小写的方法。例如，要将符串改为全部大写或全部小写，可以像下面这样做:
``` Python
name = "Fulade Blog"  
print(name.upper()) 
print(name.lower())
```
输出如下:
```
FULADE BLOG
fulade blog
```
#### **拼接字符串**
在很多情况下，我们需要合并字符串。例如，你可能想将姓和名存储在不同的变量中，等要显示姓名时再将它们合而为一:
``` Python
first_name = "Fu"
last_name = "lade"
full_name = first_name + " " + last_name
print(full_name)
```
Python使用加号(+)来合并字符串。在这个示例中，我们使用`+`来合并first_name、空格和
last_name，以得到完整的姓名，其结果如下:
``` Python
Fu lade
```
这种合并字符串的方法称为拼接。通过拼接，可使用存储在变量中的字符串来创建完整的字符串。下面来看另外一个例子:
``` Python
first_name = "fu"
last_name = "lade"
full_name = first_name + " " + last_name
message = "Hello, " + full_name.title() + "!"
print(message)
```
上述代码显示消息"Hello, Fu Lade!"，但将这条消息存储在了一个变量中， 这让最后的`print`语句简单得多。
#### **使用制表符(按Tab键产生空格的叫做制表符)或换行符来添加空白**
在编程中，空白泛指任何非打印字符，如空格、制表符和换行符。你可使用空白来组织输出，使输出更易读。
要在字符串中添加制表符，可使用字符组合`\t`，如下代码所示:
``` Python
print("Python")
Python
print("\tPython")
    Python
```
要在字符串中添加换行符，可使用字符组合`\n`:
``` Python
print("Languages:\nPython\nC\nJavaScript") 
Languages:
Python
C
JavaScript
```
还可在同一个字符串中同时包含制表符和换行符。字符串"\n\t"让Python换到下一行，并在
  下一行开头添加一个制表符。下面的示例演示了如何使用一个单行字符串来生成四行输出:
  ``` Python
print("Languages:\n\tPython\n\tC\n\tJavaScript") 
Languages:
    Python
    C 
    JavaScript
  ```

#### **删除空白和空格**
在程序中，多余的空白可能令人迷惑。对程序员来说，`'python'`和`'python '`看起来几乎没什么两样，但对编译器来说，它们却是两个不同的字符串。Python能够发现'python '中多余的空格，并认为它是有意义的——除非你告诉它不是这样的。
空格很重要，因为你经常需要比较两个字符串是否相同。例如，在用户登陆网站的时候，我们需要对比用户名。但在有些场景下我们并不想要空格。所以，Python提供了很简单的删除空格的方法。
Python能够找出字符串开头和末尾多余的空白。要确保字符串末尾没有空白，可使用方法 `rstrip()`。

``` Python
favorite_language = "'python '" 
print(favorite_language)
'python '
print(favorite_language.rstrip())
'python'
print(favorite_language)
'python ' 
```
存储在变量`favorite_language`中的字符串末尾包含多余的空格。你在运行这个代码的时候，可看到末尾的空格。对变量`favorite_language`调用方法 `rstrip()`后，这个多余的空格被删除了。然而，这种删除只是暂时的，接下来再次输出`favorite_language`的值时，你会发现这个字符串与输入时一样，依然包含多余的空格。
要永久删除这个字符串中的空格，必须将删除操作的结果保存回到变量中:
```Python
favorite_language = "'python '"
favorite_language = favorite_language.rstrip()
print(favorite_language)
'python'
```
为删除这个字符串中的空格，你需要将其末尾的空格剔除，再将结果存回到原来的变量中。
在我们的日常开发中，经常需要修改变量的值，再将新值存回到原来的变量中。
你还可以剔除字符串开头的空格，或同时剔除字符串两端的空格。为此，可分别使用方法 `lstrip()`和`strip()`:
``` Python
favorite_language = "' python '" 
print(favorite_language.rstrip())
' python'
print(favorite_language.lstrip())
'python '
print(favorite_language.strip())
'python'
```
在这个示例中，我们首先创建了一个开头和末尾都有空格的字符串。接下来，我们 分别删除末尾、开头两端的空格。在实际程序开发中，这些剔除函数最常用于在存储用户输入前对输入进行清理。

#### **使用字符串时避免语法错误**
语法错误是一种经常会出现的错误。程序中包含非法的Python代码时，就会导致语法错误。 例如，在用单引号括起的字符串中，如果包含撇号，就将导致错误。这是因为这会导致Python将 第一个单引号和撇号之间的内容视为一个字符串，进而将余下的文本视为Python代码，从而引发 错误。
下面演示了如何正确地使用单引号和双引号。
``` Python
message = "One of Python's strengths is its diverse community." 
print(message)
```
撇号位于两个双引号之间，因此Python解释器能够正确地理解这个字符串:
```Python
One of Python's strengths is its diverse community.
```
然而，如果你使用单引号，Python将无法正确地确定字符串的结束位置:
```Python
message = 'One of Python's strengths is its diverse community.'
print(message)
```
而你将看到如下输出:
``` Python
message = 'One of Python's strengths is its diverse community.'
SyntaxError: invalid syntax
```
从上面的输出我们可以看到，错误发生在第二个单引号后面。这种语法错误表明，在解释器看来，其中的有些内容不是有效的Python代码。错误的来源多种多样，这里指出一些常见的。学习 编写Python代码时，你可能会经常遇到语法错误。

所以，大家在做练习的时候也要细心，避免出现这种小错误。

> 小作业
在做下面的每个练习时，都编写一个独立的程序，并将其保存为名称类似于 `name_cases.py` 的文件。
2-1 个性化消息:将用户的姓名存到一个变量中，并向该用户显示一条消息。显示 的消息应非常简单，如“Hello Eric, would you like to learn some Python today?”。
2-2 调整名字的大小写:将一个人名存储到一个变量中，再以小写、大写和首字母 大写的方式显示这个人名。
2-3 名言:找一句你钦佩的名人说的名言，将这个名人的姓名和他的名言打印出来。输出应类似于下面这样(包括引号):
Albert Einstein once said, “A person who never made a mistake never tried anything new.”
2-4 名言 2:重复练习 2-5，但将名人的姓名存储在变量 famous_person 中，再创建 要显示的消息，并将其存储在变量 message 中，然后打印这条消息。
2-5 剔除人名中的空白:存储一个人名，并在其开头和末尾都包含一些空白字符。 务必至少使用字符组合"\t"和"\n"各一次。
打印这个人名，以显示其开头和末尾的空白。然后，分别使用剔除函数 lstrip()、 rstrip()和 strip()对人名进行处理，并将结果打印出来。



***  
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)