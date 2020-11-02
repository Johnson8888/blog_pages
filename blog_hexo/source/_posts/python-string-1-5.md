---
title: python-string-1-5
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-02 09:08:51
authorDesc: 技术改变生活
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

##### **字符串**
字符串虽然看似简单，但能够以很多 不同的方式使用它们。
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
##### **使用方法修改字符串的大小写**
对于字符串，可执行的最简单的操作之一是修改其中的单词的大小写。请看下面的代码，并尝试判断其作用:
``` Python
name = "fulade blog" 
print(name.title())
```

将这个文件保存为name.py，再运行它。你将看到如下输出:

```
Fulade Blog
```
在这个示例中，小写的字符串"fulade blog"存储到了变量name中。在`print()`语句中，方法 `title()`出现在这个变量的后面。方法是Python可对数据执行的操作。在`name.title()`中，name后 面的句点(.)让Python对变量name执行方法`title()`指定的操作。每个方法后面都跟着一对括号， 这是因为方法通常需要额外的信息来完成其工作。这种信息是在括号内提供的。函数`title()`不 需要额外的信息，因此它后面的括号是空的。
`title()`以首字母大写的方式显示每个单词，即将每个单词的首字母都改为大写。
例如，你可能希望程序将值Fulade、FULADE和fulade视为同一个名字， 并将它们都显示为Fulade。
还有其他几个很有用的大小写处理方法。例如，要将符串改为全部大写或全部小写，可以像下面这样做:
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
##### **拼接字符串**
在很多情况下，都需要合并字符串。例如，你可能想将姓和名存储在不同的变量中，等要显示姓名时再将它们合而为一:
``` Python
first_name = "Fu"
last_name = "lade"
full_name = first_name + " " + last_name
print(full_name)
```
Python使用加号(+)来合并字符串。在这个示例中，我们使用+来合并first_name、空格和
last_name，以得到完整的姓名，其结果如下:
``` Python
Fu lade
```
这种合并字符串的方法称为拼接。通过拼接，可使用存储在变量中的信息来创建完整的消息。下面来看另外一个例子:
``` Python
first_name = "fu"
last_name = "lade"
full_name = first_name + " " + last_name
message = "Hello, " + full_name.title() + "!"
print(message)
```
上述代码也显示消息"Hello, Fu Lade!"，但将这条消息存储在了一个变量中， 这让最后的`print`语句简单得多。
##### **使用制表符(按Tab键产生的叫做制表符)或换行符来添加空白**
在编程中，空白泛指任何非打印字符，如空格、制表符和换行符。你可使用空白来组织输出， 以使其更易读。
要在字符串中添加制表符，可使用字符组合`\t`，如下述代码所示:
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

  ##### **删除空白和空格**