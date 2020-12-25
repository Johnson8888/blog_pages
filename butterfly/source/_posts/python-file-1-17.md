---
title: 【Python 1-17】Python手把手教程之——文件的读写以及I/O操作
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-23 20:46:18
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
tags:
    - Python 文件
    - Python 读写
    - Python I/O
categories: Python 
keywords: 'Python 文件，Python 读写，Python I/O操作'
description: 学习处理文件和保存数据可让你的程序使用起来更容易:用户将 能够选择输入什么样的数据，以及在什么时候输入;用户使用你的程 序做一些工作后，可将程序关闭，以后再接着往下做。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)


### 从文件中读取数据
文本文件可存储的数据量很多，每当需要分析或修改存储在文件中的信息时，读取文件都很有用，对数据分析应用程序来说尤其 如此。例如，你可以编写一个这样的程序:读取一个文本文件的内容，重新设置这些数据的格式 并将其写入文件，让浏览器能够显示这些内容。
要使用文本文件中的信息，首先需要将信息读取到内存中。为此，你可以一次性读取文件的全部内容，也可以以每次一行的方式逐步读取。
#### 读取整个文件
要读取文件，需要一个包含几行文本的文件。下面首先来创建一个文件，它包含精确到小数点后30位的圆周率值，且在小数点后每10位处都换行:
``` bash
3.1415926535 
8979323846 
2643383279
```
我们把它保存为`pi_digits.txt`文件
``` py
with open('pi_digits.txt') as file_object: 
    contents = file_object.read() 
    print(contents)
```
我们先来看看函数`open()`。要以任何方式使用文件——哪怕仅仅是打印其内容，都得先打开文件，这样才能访问它。函数`open()`接受一个参数: 要打开的文件的名称。Python在当前执行的文件所在的目录中查找指定的文件。在这个示例中，假如我们把文件保存为`file_reader.py`，因此Python在`file_reader.py`所在的目录中查找`pi_digits.txt`。函数`open()`返回一个表示文件的对象。在这里，`open('pi_digits.txt')`返回一个表示文件`pi_digits.txt`的对象，Python将这个对象存储在我们将在后面使用的变量中。
关键字`with`在不再需要访问文件后将其关闭。在这个程序中，注意到我们调用了`open()`，但没有调用`close()`，你也可以调用`open()`和`close()`来打开和关闭文件，但这样做时，如果程序存在bug，导致`close()`语句未执行，文件将不会关闭。这看似微不足道，但未妥善地关闭文件可能会导致数据丢失或受损。如果在程序中过早地调用`close()`，你会发现需要使用文件时它已关闭，这会导致更多的错误。并非在任何情况下都能轻松确定关闭文件的恰当时机，但通过使用前面所示的结构，可让Python去确定:你只管打开文件，并在需要时使用它，Python自会在合适的时候自动将其关闭。
通过打印`contents`的值，就可将这个文本文件的全部内容显示出来:
``` 
3.1415926535 
8979323846 
2643383279
```
#### 文件路径
当你将类似`pi_digits.txt`这样的简单文件名传递给函数`open()`时，Python将在当前执行的文件所在的目录中查找文件。
根据你组织文件的方式，有时可能要打开不在程序文件所属目录中的文件。例如，你可能将 程序文件存储在了文件夹`python_work`中，而在文件夹`python_work`中，有一个名为`text_files`的文件夹，用于存储程序文件操作的文本文件。虽然文件夹`text_files`包含在文件夹`python_work`中，但仅向`open()`传递位于该文件夹中的文件的名称也不可行，因为Python只在文件夹`python_work`中查找，而不会在其子文件夹`text_files`中查找。要让Python打开不与程序文件位于同一个目录中的文件，需要提供文件路径，它让Python到系统的特定位置去查找。  
由于文件夹`text_files`位于文件夹`python_work`中，因此可使用相对文件路径来打开该文件夹中的文件。相对文件路径让Python到指定的位置去查找，而该位置是相对于当前运行的程序所在目录的。在Linux和OS X中，你可以这样编写代码:
``` py
with open('text_files/filename.txt') as file_object:
```
这行代码让Python到文件夹`python_work`下的文件夹`text_files`中去查找指定的.txt文件。在Windows系统中，在文件路径中使用反斜杠`\`而不是斜杠`/`:
``` py
with open('text_files\filename.txt') as file_object:
```
你还可以将文件在计算机中的准确位置告诉Python，这样就不用关心当前运行的程序存储在什么地方了。这称为绝对文件路径。在相对路径行不通时，可使用绝对路径。例如，如果`text_files`并不在文件夹`python_work`中，而在文件夹`other_files`中，则向`open()`传递路径`'text_files/ filename.txt'`行不通，因为Python只在文件夹`python_work`中查找该位置。为明确地指出你希望Python到哪里去查找，你需要提供完整的路径。
绝对路径通常比相对路径更长，因此将其存储在一个变量中，再将该变量传递给`open()`会有所帮助。在Linux和OS X中，绝对路径类似于下面这样:
``` py
file_path = '/home/ehmatthes/other_files/text_files/filename.txt'
with open(file_path) as file_object:
```
而在Windows系统中，它们类似于下面这样:
``` py
file_path = 'C:\Users\ehmatthes\other_files\text_files\filename.txt'
with open(file_path) as file_object:
```
通过使用绝对路径，可读取系统任何地方的文件。就目前而言，最简单的做法是，要么将 据文件存储在程序文件所在的目录，要么将其存储在程序文件所在目录下的一个文件夹(如`text_files`)中。

#### 逐行读取
读取文件时，常常需要检查其中的每一行:你可能要在文件中查找特定的信息，或者要以某种方式修改文件中的文本。例如，你可能要遍历一个包含天气数据的文件，并使用天气描述中包含字样`sunny`的行。在新闻报道中，你可能会查找包含标签`<headline>`的行，并按特定的格式设置它。
要以每次一行的方式检查文件，可对文件对象使用for循环:
``` py
filename = 'pi_digits.txt'
with open(filename) as file_object: 
    for line in file_object:
    print(line)
```
我们将要读取的文件的名称存储在变量`filename`中，这是使用文件时一种常见的做法。由于变量`filename`表示的并非实际文件——它只是一个让Python知道到哪里去查找文件的字符串，因此可轻松地将'pi_digits.txt'替换为你要使用的另一个文件的名称。

调用`open()`后，将一个表示文件及其内容的对象存储到了变量`file_object`中。这里也使用了关键字`with`，让Python负责妥善地打开和关闭文件。为查看文件的内容，我们通过对文件对象执行循环来遍历文件中的每一行，我们打印每一行时，发现空白行更多了:
``` bash
3.1415926535 

8979323846

2643383279
```
为何会出现这些空白行呢?因为在这个文件中，每行的末尾都有一个看不见的换行符，而`print`语句也会加上一个换行符，因此每行末尾都有两个换行符:一个来自文件，另一个来自`print`语句。
#### 创建一个包含文件各行内容的列表
使用关键字with时，`open()`返回的文件对象只在`with`代码块内可用。如果要在`with`代码块外访问文件的内容，可在`with`代码块内将文件的各行存储在一个列表中，并在`with`代码块外使用该列表:你可以立即处理文件的各个部分，也可推迟到程序后面再处理。
下面的示例在`with`代码块中将文件`pi_digits.txt`的各行存储在一个列表中，再在`with`代码块外打印它们:
``` py
filename = 'pi_digits.txt'
with open(filename) as file_object:
    lines = file_object.readlines() 
for line in lines:
    print(line.rstrip())
```
我们先使用方法`readlines()`从文件中读取每一行，并将其存储在一个列表中接下来，该列表被存储到变量`lines`中;在`with`代码块外，我们依然可以使用这个变量。我们使用一个简单的for循环来打印`lines`中的各行。由于列表`lines`的每个元素都对应于文件中的一行，因此输出 与文件内容完全一致。

#### 使用文件的内容
将文件读取到内存中后，就可以以任何方式使用这些数据了。下面以简单的方式使用圆周率 的值。首先，我们将创建一个字符串，它包含文件中存储的所有数字，且没有任何空格:
``` py

filename = 'pi_digits.txt'
with open(filename) as file_object: 
    lines = file_object.readlines()
pi_string = '' 
for line in lines:
    pi_string += line.rstrip()
print(pi_string) 
print(len(pi_string))
```
就像前一个示例一样，我们首先打开文件，并将其中的所有行都存储在一个列表中。我们创建了一个变量——`pi_string`，用于存储圆周率的值。接下来，我们使用一个循环将各行都加入`pi_string`，并删除每行末尾的换行符。接着，我们打印这个字符串及其长度:
``` py
3.1415926535 8979323846 2643383279
36
```
在变量`pi_string`存储的字符串中，包含原来位于每行左边的空格，为删除这些空格，可使用`strip()`而不是`rstrip()`:
``` py
filename = 'pi_30_digits.txt'
with open(filename) as file_object: 
    lines = file_object.readlines()
pi_string = ''
for line in lines:
    pi_string += line.strip()
print(pi_string) 
print(len(pi_string))
```
这样，我们就获得了一个这样的字符串:它包含精确到30位小数的圆周率值。这个字符串长32字符，因为它还包含整数部分的3和小数点:
``` py
3.141592653589793238462643383279
36
```

### 写入文件
保存数据的最简单的方式之一是将其写入到文件中。通过将输出写入文件，即便关闭包含程 序输出的终端窗口，这些输出也依然存在:你可以在程序结束运行后查看这些输出，可与别人分享输出文件，还可编写程序来将这些输出读取到内存中并进行处理。

#### 写入空文件
要将文本写入文件，你在调用open()时需要提供另一个实参，告诉Python你要写入打开的文 件。为明白其中的工作原理，我们来将一条简单的消息存储到文件中，而不是将其打印到屏幕上:
``` py
filename = 'programming.txt'
with open(filename, 'w') as file_object:
    file_object.write("I love programming.")
```
在这个示例中，调用`open()`时提供了两个实参。第一个实参也是要打开的文件的名称; 第二个实参`w`告诉Python，我们要以写入模式打开这个文件。打开文件时，可指定读取模式`r`、写入模式`w`、附加模式`a`或让你能够读取和写入文件的模式`r+`。如果 你省略了模式实参，Python将以默认的只读模式打开文件。

如果你要写入的文件不存在，函数`open()`将自动创建它。然而，以写入`w`模式打开文件时千万要小心，因为如果指定的文件已经存在，Python将在返回文件对象前清空该文件。
我们使用文件对象的方法`write()`将一个字符串写入文件。这个程序没有终端输出，但如果你打开文件`programming.txt`，将看到其中包含如下一行内容:
``` py
I love programming.
```
相比于你的计算机中的其他文件，这个文件没有什么不同。你可以打开它、在其中输入新文本、复制其内容、将内容粘贴到其中等。
#### 写入多行
函数`write()`不会在你写入的文本末尾添加换行符，因此如果你写入多行时没有指定换行符，
文件看起来可能不是你希望的那样:
``` py
filename = 'programming.txt'
with open(filename, 'w') as file_object:
    file_object.write("I love programming.") 
    file_object.write("I love creating new games.")
```
如果你打开programming.txt，将发现两行内容挤在一起:
``` py
I love programming.I love creating new games.
```
要让每个字符串都单独占一行，需要在`write()`语句中包含换行符:
``` py
filename = 'programming.txt'
with open(filename, 'w') as file_object:
    file_object.write("I love programming.\n") 
    file_object.write("I love creating new games\n")
```
现在，输出出现在不同行中:
```py
I love programming.
I love creating new games.
```
#### 追加写入文件
如果你要给文件添加内容，而不是覆盖原有的内容，可以附加模式打开文件。你以**附加模式**打开文件时，Python不会在返回文件对象前清空文件，而你写入到文件的行都将添加到文件末尾。如果指定的文件不存在，Python将为你创建一个空文件。
``` py
filename = 'programming.txt'
with open(filename, 'a') as file_object:
    file_object.write("I also love finding meaning in large datasets.\n")
    file_object.write("I love creating apps that can run in a browser.\n")
``` 
我们打开文件时指定了实参`a`，以便将内容附加到文件末尾，而不是覆盖文件原来的内容。然后，我们又写入了两行，它们被添加到文件`programming.txt`末尾:
``` bash
I love programming.
I love creating new games.
I also love finding meaning in large datasets.
I love creating apps that can run in a browser.
```
最终的结果是，文件原来的内容还在，它们后面是我们刚添加的内容。 19



> 小作业
17-1 在文本编辑器中新建一个文件，写几句话来总结一下你至
此学到的Python知识。将这个文件命名为 learning_python.txt，并将其存储到为完成本章练习而编写的程序所在的目录中。编写一个程序，读取整个文件，并打印。
17-2 访客:编写一个程序，提示用户输入其名字;用户作出响应后，将其名字写入到文件 guest.txt中。


想查看作业答案可以去[我的Githu仓库](https://github.com/Johnson8888/learn_python)在文件夹**17-1_17-2**下

***  
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)