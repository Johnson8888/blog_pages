---
title: 【Python 1-14】Python手把手教程之——详解函数的高级用法
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-21 19:22:53
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


### 传递列表
你经常会发现，向函数传递列表很有用，这种列表包含的可能是名字、数字或更复杂的对象(如字典)。将列表传递给函数后，函数就能直接访问其内容。下面使用函数来提高处理列表的效率。  

假设有一个用户列表，我们要问候其中的每位用户。下面的示例将一个名字列表传递给一个名为`greet_users()`的函数，这个函数问候列表中的每个人:
``` py
def greet_users(names): 
    """向列表中的每位用户都发出简单的问候""" 
    for name in names:
        msg = "Hello, " + name.title() + "!" 
        print(msg)
        
usernames = ['hannah', 'ty', 'margot'] 
greet_users(usernames)
```

我们将`greet_users()`定义成接受一个名字列表，并将其存储在形参`names`中。这个函数遍历收到的列表，并对其中的每位用户都打印一条问候语。然后我们定义了一个用户列表——`usernames`，然后调用`greet_users()`，并将这个列表传递给它:
``` py
Hello, Hannah! 
Hello, Ty! 
Hello, Margot!
```
输出完全符合预期，每位用户都看到了一条个性化的问候语。每当你要问候一组用户时，都可调用这个函数。
#### 在函数中修改列表
将列表传递给函数后，函数就可对其进行修改。在函数中对这个列表所做的任何修改都是永久性的，这让你能够高效地处理大量的数据。  

来看一家为用户提交的设计制作3D打印模型的公司。需要打印的设计存储在一个列表中，打印后移到另一个列表中。下面是在不使用函数的情况下模拟这个过程的代码:
``` py
# 首先创建一个列表，其中包含一些要打印的设计
unprinted_designs = ['iphone case', 'robot pendant', 'dodecahedron'] 
completed_models = []
# 模拟打印每个设计，直到没有未打印的设计为止
# 打印每个设计后，都将其移到列表completed_models中 
while unprinted_designs:
    current_design = unprinted_designs.pop()
    #模拟根据设计制作3D打印模型的过程 
    print("Printing model: " + current_design) completed_models.append(current_design)
# 显示打印好的所有模型
print("\nThe following models have been printed:") 
for completed_model in completed_models:
    print(completed_model)
```
这个程序首先创建一个需要打印的设计列表，还创建一个名为`completed_models`的空列表， 每个设计打印都将移到这个列表中。  

只要列表`unprinted_designs`中还有设计，`while`循环就模拟打印设计的过程:从该列表末尾删除一个设计，将其存储到变量`current_design`中，并显示一条消息，指出正在打印当前的设计，再将该设计加入到列表`completed_models`中。循环结束后，显示已打印的所有设计:

``` py
Printing model: dodecahedron 
Printing model: robot pendant
Printing model: iphone case 

The following models have been printed: 
dodecahedron
robot pendant
iphone case
```

为重新组织这些代码，我们可编写两个函数，每个都做一件具体的工作。大部分代码都与原来相同，只是效率更高。第一个函数将负责处理打印设计的工作，而第二个将概述打印了哪些设计:
``` py
def print_models(unprinted_designs, completed_models):
    """
    模拟打印每个设计，直到没有未打印的设计为止打印每个设计后，都将其移到列表completed_models中
    """
    while unprinted_designs:
        current_design = unprinted_designs.pop()
        # 模拟根据设计制作3D打印模型的过程
        print("Printing model: " + current_design)
        completed_models.append(current_design)

def show_completed_models(completed_models): 
    """显示打印好的所有模型"""
    print("\nThe following models have been printed:") for completed_model in completed_models:
        print(completed_model)
unprinted_designs = ['iphone case', 'robot pendant', 'dodecahedron'] 
completed_models = []

print_models(unprinted_designs, completed_models) 
show_completed_models(completed_models)
```
首先，我们定义了函数`print_models()`，它包含两个形参:一个需要打印的设计列表和一个打印好的模型列表。

给定这两个列表，这个函数模拟打印每个设计的过程:将设计逐个地从未 打印的设计列表中取出，并加入到打印好的模型列表中。

然后，我们定又义了函数`show_completed_models()`，它包含一个形参:打印好的模型列表。给定这个列表，函数`show_completed_models()`显示打印出来的每个模型的名称。
这个程序的输出与未使用函数的版本相同，但组织更为有序。完成大部分工作的代码都移到了两个函数中，让主程序更容易理解。只要看看主程序，你就知道这个程序的功能容易看清得多:
``` py
unprinted_designs = ['iphone case', 'robot pendant', 'dodecahedron'] 
completed_models = []
print_models(unprinted_designs, completed_models) 
show_completed_models(completed_models)
```
我们创建了一个未打印的设计列表，还创建了一个空列表，用于存储打印好的模型。接下来，由于我们已经定义了两个函数，因此只需调用它们并传入正确的实参即可。我们调用`print_models()`并向它传递两个列表;像预期的一样，`print_models()`模拟打印设计的过程。接下来，我们调用`show_completed_models()`，并将打印好的模型列表传递给它，让其能够指出打印了哪些模型。描述性的函数名让别人阅读这些代码时也能明白，虽然其中没有任何注释。  

相比于没有使用函数的版本，这个程序更容易扩展和维护。如果以后需要打印其他设计，只需再次调用`print_models()`即可。如果我们发现需要对打印代码进行修改，只需修改这些代码一次，就能影响所有调用该函数的地方;与必须分别修改程序的多个地方相比，这种修改的效率更高。

这个程序还演示了这样一种理念，即每个函数都应只负责一项具体的工作。第一个函数打印每个设计，而第二个显示打印好的模型;这优于使用一个函数来完成两项工作。编写函数时，如果你发现它执行的任务太多，请尝试将这些代码划分到两个函数中。别忘了，总是可以在一个函 数中调用另一个函数，这有助于将复杂的任务划分成一系列的步骤。

### 传递任意数量的实参
有时候，你预先不知道函数需要接受多少个实参，好在Python允许函数从调用语句中收集任意数量的实参。 

例如，来看一个制作披萨的函数，它需要接受很多配料，但你无法预先确定顾客要多少种配料。下面的函数只有一个形参`*toppings`，但不管调用语句提供了多少实参，这个形参都将它们统统收入囊中:
``` py
def make_pizza(*toppings): 
    """打印顾客点的所有配料""" 
    print(toppings)
    make_pizza('pepperoni')
    make_pizza('mushrooms', 'green peppers', 'extra cheese')
```
形参名`*toppings`中的星号让Python创建一个名为`toppings`的空元组，并将收到的所有值都封装到这个元组中。函数体内的`print`语句通过生成输出来证明Python能够处理使用一个值调用函数的情形，也能处理使用三个值来调用函数的情形。 
它以类似的方式处理不同的调用，注意，Python将实参封装到一个元组中，即便函数只收到一个值也如此:
``` py
('pepperoni',)
('mushrooms', 'green peppers', 'extra cheese')
```
现在，我们可以将这条`print`语句替换为一个循环，对配料列表进行遍历，并对顾客点的披萨进行描述:
``` py
def make_pizza(*toppings):
    """概述要制作的比萨"""
    print("\nMaking a pizza with the following toppings:") 
    for topping in toppings:
        print("- " + topping)
make_pizza('pepperoni')
make_pizza('mushrooms', 'green peppers', 'extra cheese')
```
不管收到的是一个值还是三个值，这个函数都能妥善地处理:
``` py
Making a pizza with the following toppings: 
- pepperoni
Making a pizza with the following toppings: 
- mushrooms
- green peppers
- extra cheese
```
不管函数收到的实参是多少个，这种语法都管用。

### 将函数存储在模块中

函数的优点之一是，使用它们可将代码块与主程序分离。通过给函数指定描述性名称，可让主程序容易理解得多。你还可以更进一步，将函数存储在被称为模块的独立文件中，再将模块导入到主程序中。`import`语句允许在当前运行的程序文件中使用模块中的代码。
通过将函数存储在独立的文件中，可隐藏程序代码的细节，将重点放在程序的高层逻辑上。这还能让你在众多不同的程序中重用函数。将函数存储在独立文件中后，可与其他程序员共享这些文件而不是整个程序。知道如何导入函数还能让你使用其他程序员编写的函数库。 
导入模块的方法有多种，下面对每种都作简要的介绍。
#### 导入整个模块
要让函数是可导入的，得先创建模块。模块是扩展名为.py的文件，包含要导入到程序中的代码。下面来创建一个包含函数`make_pizza()`的模块。为此，我们将文件`pizza.py`中除函数`make_pizza()`之外的其他代码都删除:
``` py
def make_pizza(size, *toppings):
    """概述要制作的比萨"""
    print("\nMaking a " + str(size) + "-inch pizza with the following toppings:")
    for topping in toppings:
        print("- " + topping)
```
接下来，我们在`pizza.py`所在的目录中创建另一个名为`making_pizzas.py`的文件，这个文件导入刚创建的模块，再调用`make_pizza()`两次:
``` py
import pizza
pizza.make_pizza(16, 'pepperoni')
pizza.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```
Python读取这个文件时，代码行`import pizza`让Python打开文件`pizza.py`，并将其中的所有函数都复制到这个程序中。你看不到复制的代码，因为这个程序运行时，Python在幕后复制这些代码。你只需知道，在`making_pizzas.py`中，可以使用`pizza.py`中定义的所有函数。

要调用被导入的模块中的函数，可指定导入的模块的名称`pizza`和函数名`make_pizza()`，并用句点分隔它们。这些代码的输出与没有导入模块的原始程序相同:
``` bash
Making a 16-inch pizza with the following toppings:
- pepperoni
Making a 12-inch pizza with the following toppings: 
- mushrooms
- green peppers
- extra cheese
```
这就是一种导入方法:只需编写一条import语句并在其中指定模块名，就可在程序中使用该模块中的所有函数。如果你使用这种import语句导入了名为`module_name.py`的整个模块，就可使用下面的语法来使用其中任何一个函数:
``` py
module_name.function_name()
```
#### 导入特定的函数
你还可以导入模块中的特定函数，这种导入方法的语法如下:
``` py
from module_name import function_name
```
通过用逗号分隔函数名，可根据需要从模块中导入任意数量的函数:
``` py
from module_name import function_0, function_1, function_2
```
对于前面的`making_pizzas.py`示例，如果只想导入要使用的函数，代码将类似于下面这样:
``` py
from pizza import make_pizza
make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```
若使用这种语法，调用函数时就无需使用句点。由于我们在import语句中显式地导入了函数`make_pizza()`，因此调用它时只需指定其名称。
#### 使用as给函数指定别名
如果要导入的函数的名称可能与程序中现有的名称冲突，或者函数的名称太长，可指定简短而独一无二的别名——函数的另一个名称，类似于外号。要给函数指定这种特殊外号，需要在导入它时这样做。
下面给函数`make_pizza()`指定了别名`mp()`。这是在import语句中使用`make_pizza as mp`实现的，关键字`as`将函数重命名为你提供的别名:
``` py
from pizza import make_pizza as mp
mp(16, 'pepperoni')
mp(12, 'mushrooms', 'green peppers', 'extra cheese')
```
上面的import语句将函数make_pizza()重命名为mp();在这个程序中，每当需要调用`make_pizza()`时，都可简写成`mp()`，而Python将运行`make_pizza()`中的代码，这可避免与这个程序可能包含的函数`make_pizza()`混淆。指定别名的通用语法如下:
``` py
from module_name import function_name as fn
```
#### 使用as给模块指定别名
你还可以给模块指定别名。通过给模块指定简短的别名(如给模块pizza指定别名p)，让你能够更轻松地调用模块中的函数。相比于`pizza.make_pizza()`，`p.make_pizza()`更为简洁:
``` py
import pizza as p
p.make_pizza(16, 'pepperoni')
p.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```
上述import语句给模块`pizza`指定了别名p，但该模块中所有函数的名称都没变。调用函数`make_pizza()`时，可编写代码`p.make_pizza()`而不是`pizza.make_pizza()`，这样不仅能使代码更简洁，还可以让你不再关注模块名，而专注于描述性的函数名。这些函数名明确地指出了函数的功能，对理解代码而言，它们比模块名更重要。  给模块指定别名的通用语法如下:
``` bash
import module_name as mn
```
#### 导入模块中的所有函数
使用星号(*)运算符可让Python导入模块中的所有函数:
``` bash
from pizza import *
make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```
import语句中的星号让Python将模块`pizza`中的每个函数都复制到这个程序文件中。由于导入了每个函数，可通过名称来调用每个函数，而无需使用句点表示法。然而，使用并非自己编写的大型模块时，最好不要采用这种导入方法:如果模块中有函数的名称与你的项目中使用的名称相同，可能导致意想不到的结果:Python可能遇到多个名称相同的函数或变量，进而覆盖函数，而不是分别导入所有的函数。

最佳的做法是，要么只导入你需要使用的函数，要么导入整个模块并使用句点表示法。这能让代码更清晰，更容易阅读和理解。这里之所以介绍这种导入方法，只是想让你在阅读别人编写 的代码时，如果遇到类似于下面的import语句，能够理解它们:
``` py
from module_name import *
```

### 函数编写指南
编写函数时，需要牢记几个细节。应给函数指定描述性名称，且只在其中使用小写字母和下 划线。描述性名称可帮助你和别人明白代码想要做什么。给模块命名时也应遵循上述约定。 
每个函数都应包含简要地阐述其功能的注释，该注释应紧跟在函数定义后面，并采用文档字 符串格式。文档良好的函数让其他程序员只需阅读文档字符串中的描述就能够使用它:他们完全 可以相信代码如描述的那样运行;只要知道函数的名称、需要的实参以及返回值的类型，就能在 自己的程序中使用它。 
给形参指定默认值时，等号两边不要有空格:
``` py
def function_name(parameter_0, parameter_1='default value')
```
对于函数调用中的关键字实参，也应遵循这种约定:
``` py
function_name(value_0, parameter_1='value')
```
官方建议代码行的长度不要超过79字符，这样只要编辑器窗口适中，就能看到整行代码。如果形参很多，导致函数定义的长度超过了79字符，可在函数定义中输入左括号后按回车键，并在下一行按两次Tab键，从而将形参列表和只缩进一 层的函数体区分开来。
大多数编辑器都会自动对齐后续参数列表行，使其缩进程度与你给第一个参数列表行指定的 缩进程度相同:
``` py
def function_name(parameter_0, parameter_1, parameter_2, parameter_3, parameter_4, parameter_5):
    function body...
```
如果程序或模块包含多个函数，可使用两个空行将相邻的函数分开，这样将更容易知道前一 个函数在什么地方结束，下一个函数从什么地方开始。所有的import语句都应放在文件开头，唯一例外的情形是，在文件开头使用了注释来描述整个程序。

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)