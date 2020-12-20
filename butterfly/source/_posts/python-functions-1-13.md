---
title: 【Python 1-13】Python手把手教程之——详解函数和函数的使用
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-20 16:05:51
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
tags:
    - Python 函数
    - 函数
categories: Python 
keywords: 'Python 函数,函数'
description: 要执行函数定义的特定任务，我们可以使用函数。需要在程序中多次执行同一项任务时，你无需反复编写完成该任务的代码，而只需调用执行该任务的函数，让Python运行其中的代码。你将发现，通过使用函数，程序的编写、阅读、测试和修复都将更容易。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### 定义函数
下面是一个打印问候语的简单函数，名为greet_user()：
``` py
def greet_user():
    """显示简单的问候语"""
    print("Hello!")
greet_user()
```
这个示例演示了最简单的函数结构。使用关键字`def`来告诉Python你要定义一个
函数。在这里，函数名为`greet_user()`，它不需要任何信息就能完成其工作，因此括号是空的（即便如此，括号也必不可少）。最后，定义以冒号结尾。

紧跟在`def greet_user()`:后面的所有缩进行构成了函数体。代码行`print("Hello!"`)是函数体内的唯一一行代码，`greet_user()`只做一项工作：打印Hello!。 

由于这个函数不需要任何参数，因此调用它时只需输入`greet_user()`即可。和预期的一样，它打印`Hello!`。

#### 向函数传递信息
只需稍作修改，就可以让函数`greet_user()`不仅向用户显示`Hello!`，还将用户的名字用作参数。  

因此，可在函数定义`def greet_user()`的括号内添加`username`。通过在这里添加`username`，就可让函数接受你给`username`指定的任何值。现在，这个函数要求你调用它时给`username`指定一个值。调用`greet_user()`时，可将一个名字传递给它，如下所示：

```py
def greet_user(username):
    """显示简单的问候语"""
    print("Hello, " + username.title() + "!")
greet_user('Fulade') 
```
代码`greet_user('Fulade')`调用函数`greet_user()`，并向它提供执行`print`语句所需的信息。这个函数接受你传递给它的名字，并向这个人发出问候：
``` bash
Hello Fulade !
```
同样，`greet_user('sarah')`调用函数`greet_user()`并向它传递`sarah`，打印`Hello, Sarah!`。
你可以根据需要调用函数`greet_user()`任意次，调用时无论传入什么样的名字，都会生成相应的输出。

#### 实参和形参

前面定义函数`greet_user()`时，要求给变量`username`指定一个值。调用这个函数并提供这种参数，它将打印相应的问候语。  

在函数`greet_user()`的定义中，变量`username`是一个形参——函数完成其工作所需的一项信息。在代码`greet_user('Fulade')`中，值`Fulade`是一个实参。

实参是调用函数时传递给函数的信息。我们调用函数时，将要让函数使用的信息放在括号内。在`greet_user('Fulade')`中，将实参`Fulade`传递给了函数`greet_user()`，这个值被存储在形参`username`中。


### 传递实参
鉴于函数定义中可能包含多个形参，因此函数调用中也可能包含多个实参。向函数传递实参的方式很多，可使用位置实参，这要求实参的顺序与形参的顺序相同；也可使用关键字实参，其中每个实参都由变量名和值组成；还可使用列表和字典。下面来依次介绍这些方式。
  
#### 位置实参
你调用函数时，Python必须将函数调用中的每个实参都关联到函数定义中的一个形参。因此，最简单的关联方式是基于实参的顺序。这种关联方式被称为位置实参。为明白其中的工作原理，来看一个显示宠物信息的函数。这个函数指出一个宠物属于哪种动物以及它叫什么名字，如下所示：

``` py
def describe_pet(animal_type, pet_name):
    """显示宠物的信息"""
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet('hamster', 'harry')
```
这个函数的定义表明，它需要一种动物类型和一个名字。调用`describe_pet()`时，需要按顺序提供一种动物类型和一个名字。

例如，在前面的函数调用中，实参`hamster`存储在形参`animal_type`中，而实参`harry`存储在形参`pet_name`中。在函数体内，使用了这两个形参来显示宠物的信息。

##### 调用函数多次
你可以根据需要调用函数任意次。要再描述一个宠物，只需再次调用`describe_pet()`即可：
``` py
def describe_pet(animal_type, pet_name):
    """显示宠物的信息"""
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet('hamster', 'harry')
describe_pet('dog', 'willie') 
```
第二次调用`describe_pet()`函数时，我们向它传递了实参`dog`和`willie`。与第一次调用时一样，Python将实参`dog`关联到形参`animal_type`，并将实参`willie`关联到形参`pet_name`。  

与前面一样，这个函数完成其任务，但打印的是一条名为`Willie`的小狗的信息。至此，我们有一只名为`Harry`的仓鼠，还有一条名为`Willie`的小狗：
``` bash
I have a hamster.
My hamster's name is Harry.
I have a dog.
My dog's name is Willie. 
```

调用函数多次是一种效率极高的工作方式。我们只需在函数中编写描述宠物的代码一次，然后每当需要描述新宠物时，都可调用这个函数，并向它提供新宠物的信息。即便描述宠物的代码增加到了10行，你依然只需使用一行调用函数的代码，就可描述一个新宠物。  

在函数中，可根据需要使用任意数量的位置实参，Python将按顺序将函数调用中的实参关联到函数定义中相应的形参。

##### 位置实参的顺序很重要
使用位置实参来调用函数时，如果实参的顺序不正确，结果可能出乎意料：
``` py
def describe_pet(animal_type, pet_name):
    """显示宠物的信息"""
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet('harry', 'hamster') 
```
在这个函数调用中，我们先指定名字，再指定动物类型。由于实参`harry`在前，这个值将存储到形参`animal_type`中；同理，`hamster`将存储到形参`pet_name`中。结果是我们得到了一个名为`Hamster`的`harry`：
``` py
I have a harry.
My harry's name is Hamster. 
```
如果结果像上面一样搞笑，请确认函数调用中实参的顺序与函数定义中形参的顺序一致。
#### 关键字实参

关键字实参是传递给函数的名称—值对。你直接在实参中将名称和值关联起来了，因此向函数传递实参时不会混淆。

关键字实参让你无需考虑函数调用中的实参顺序，还清楚地指出了函数调用中各个值的用途。下面来重新编写`pets.py`，在其中使用关键字实参来调用`describe_pet()`：

``` py
def describe_pet(animal_type, pet_name):
    """显示宠物的信息"""
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet(animal_type='hamster', pet_name='harry') 
```

函数`describe_pet()`还是原来那样，但调用这个函数时，我们向Python明确地指出了各个实参对应的形参。看到这个函数调用时，Python知道应该将实参`hamster`和`harry`分别存储在形参`animal_type`和`pet_name`中。输出正确无误，它指出我们有一只名为`Harry`的仓鼠。  

关键字实参的顺序无关紧要，因为Python知道各个值该存储到哪个形参中。下面两个函数调用是等效的：
```py
describe_pet(animal_type='hamster', pet_name='harry')
describe_pet(pet_name='harry', animal_type='hamster') 
```
#### 默认值

编写函数时，可给每个形参指定默认值。在调用函数中给形参提供了实参时，Python将使用指定的实参值；否则，将使用形参的默认值。因此，给形参指定默认值后，可在函数调用中省略相应的实参。使用默认值可简化函数调用，还可清楚地指出函数的典型用法。  

例如，如果你发现调用`describe_pet()`时，描述的大都是小狗，就可将形参`animal_type`的默认值设置为`dog`。这样，调用`describe_pet()`来描述小狗时，就可不提供这种信息：
``` py
def describe_pet(pet_name, animal_type='dog'):
    """显示宠物的信息"""
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet(pet_name='willie') 
```
这里修改了函数`describe_pet()`的定义，在其中给形参`animal_type`指定了默认值`dog`。这样，调用这个函数时，如果没有给`animal_type`指定值，Python将把这个形参设置为`dog`：

``` bash
I have a dog.
My dog's name is Willie. 
```

请注意，在这个函数的定义中，修改了形参的排列顺序。由于给`animal_type`指定了默认值，无需通过实参来指定动物类型，因此在函数调用中只包含一个实参——宠物的名字。然而，Python依然将这个实参视为位置实参，因此如果函数调用中只包含宠物的名字，这个实参将关联到函数定义中的第一个形参。这就是需要将pet_name放在形参列表开头的原因所在。  

现在，使用这个函数的最简单的方式是，在函数调用中只提供小狗的名字：
``` py
describe_pet('willie') 
```
这个函数调用的输出与前一个示例相同。只提供了一个实参——`willie`，这个实参将关联到函数定义中的第一个形参——`pet_name`。由于没有给`animal_type`提供实参，因此Python使用其默认值`dog`。
如果要描述的动物不是小狗，可使用类似于下面的函数调用：
``` py
describe_pet(pet_name='harry', animal_type='hamster') 
```
由于显式地给`animal_type`提供了实参，因此Python将忽略这个形参的默认值。

####  等效的函数调用
由于可混合使用位置实参、关键字实参和默认值，通常有多种等效的函数调用方式。请看下
面的函数`describe_pets()`的定义，其中给一个形参提供了默认值：
``` py
def describe_pet(pet_name, animal_type='dog'): 
```
基于这种定义，在任何情况下都必须给`pet_name`提供实参；指定该实参时可以使用位置方式，也可以使用关键字方式。如果要描述的动物不是小狗，还必须在函数调用中给`animal_type`提供实参；同样，指定该实参时可以使用位置方式，也可以使用关键字方式。

下面对这个函数的所有调用都可行：
``` py
# 一条名为Willie的小狗
describe_pet('willie')
describe_pet(pet_name='willie')
# 一只名为Harry的仓鼠
describe_pet('harry', 'hamster')
describe_pet(pet_name='harry', animal_type='hamster')
describe_pet(animal_type='hamster', pet_name='harry') 
```
这些函数调用的输出与前面的示例相同。


#### 避免实参错误

等你开始使用函数后，如果遇到实参不匹配错误，不要大惊小怪。你提供的实参多于或少于函数完成其工作所需的信息时，将出现实参不匹配错误。
例如，如果调用函数`describe_pet()`时没有指定任何实参，结果将如何呢？
``` py
def describe_pet(animal_type, pet_name):
    """显示宠物的信息"""
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet()
```
Python发现该函数调用缺少必要的信息，而`traceback`指出了这一点：

``` py
Traceback (most recent call last):
 File "pets.py", line 6, in <module>
 describe_pet()
 TypeError: describe_pet() missing 2 required positional arguments: 'animal_
type' and 'pet_name' 
```


### 返回值
函数并非总是直接显示输出，相反，它可以处理一些数据，并返回一个或一组值。函数返回的值被称为返回值。在函数中，可使用`return`语句将值返回到调用函数的代码行。返回值让你能够将程序的大部分繁重工作移到函数中去完成，从而简化主程序。

#### 返回简单值
下面来看一个函数，它接受名和姓并返回姓名：
``` py
def get_formatted_name(first_name, last_name):
    """返回的姓名"""
    full_name = first_name + ' ' + last_name
    return full_name.title()
    musician = get_formatted_name('jimi', 'hendrix')
print(musician) 
```
函数`get_formatted_name()`的定义通过形参接受名和姓。它将姓和名合而为一，在它们之间加上一个空格，并将结果存储在变量`full_name`中。然后，将`full_name`的值转换为首字母大写格式，并将结果返回到函数调用行。调用返回值的函数时，需要提供一个变量，用于存储返回的值。

在这里，将返回值存储在了变量`musician`中。输出是姓名：
``` bash
Jimi Hendrix 
```

#### 让实参变成可选的

有时候，需要让实参变成可选的，这样使用函数的人就只需在必要时才提供额外的信息。可使用默认值来让实参变成可选的。
例如，假设我们要扩展函数`get_formatted_name()`，使其还处理中间名。为此，可将其修改成类似于下面这样：
``` bash
def get_formatted_name(first_name, middle_name, last_name):
    """返回姓名"""
    full_name = first_name + ' ' + middle_name + ' ' + last_name
    return full_name.title()
musician = get_formatted_name('john', 'lee', 'hooker')
print(musician) 
```
只要同时提供名、中间名和姓，这个函数就能正确地运行。它根据这三部分创建一个字符串，在适当的地方加上空格，并将结果转换为首字母大写格式：
``` py
John Lee Hooker 
```
然而，并非所有的人都有中间名，但如果你调用这个函数时只提供了名和姓，它将不能正确地运行。为让中间名变成可选的，可给实参`middle_name`指定一个默认值——空字符串，并在用户没有提供中间名时不使用这个实参。
为让`get_formatted_name()`在没有提供中间名时依然可行，可给实参`middle_name`指定一个默认值——空字符串，并将其移到形参列表的末尾：
``` py
def get_formatted_name(first_name, last_name, middle_name=''):
 """返回姓名"""
    if middle_name:
        full_name = first_name + ' ' + middle_name + ' ' + last_name
    else:
        full_name = first_name + ' ' + last_name
    return full_name.title()
musician = get_formatted_name('jimi', 'hendrix')
print(musician)
musician = get_formatted_name('john', 'hooker', 'lee')
print(musician) 
```


在这个示例中，姓名是根据三个可能提供的部分创建的。由于人都有名和姓，因此在函数定义中首先列出了这两个形参。中间名是可选的，因此在函数定义中最后列出该形参，并将其默认值设置为空字符串。  

在函数体中，我们检查是否提供了中间名。Python将非空字符串解读为True，因此如果函数调用中提供了中间名，`if middle_name`将为`True`。如果提供了中间名，就将名、中间名和姓合并为姓名，然后将其修改为首字母大写格式，并返回到函数调用行。

在函数调用行，将返回的值存储在变量`musician`中；然后将这个变量的值打印出来。如果没有提供中间名，`middle_name`将为空字符串，导致`if`测试未通过，进而执行`else`代码块：只使用名和姓来生成姓名，并将设置好格式的姓名返回给函数调用行。

在函数调用行，将返回的值存储在变量`musician`中；然后将这个变量的值打印出来。调用这个函数时，如果只想指定名和姓，调用起来将非常简单。如果还要指定中间名，就必须确保它是最后一个实参，这样Python才能正确地将位置实参关联到形参。
这个修改后的版本适用于只有名和姓的人，也适用于还有中间名的人：
``` py
Jimi Hendrix
John Lee Hooker
```
可选值让函数能够处理各种不同情形的同时，确保函数调用尽可能简单。

> 本篇文章没有作业，下一篇我们讲解函数的高级用法


***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)