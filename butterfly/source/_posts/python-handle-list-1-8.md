---
title: 【Python 1-8】Python手把手教程之——管理列表List
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
cover:  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
thumbnail:  https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
toc: true
comments: true
tags:
  - Python
categories: Python
keywords: 'Python列表,Python自学教程,大学生学Python,Python教程,Python管理列表'
date: 2020-11-26 16:48:24
description:
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

在[上一节](http://fulade.me/python-list-7.html)我们学习了如何创建一个列表，在列表里面插入、删除数据等操作。
本节我们学习如何管理列表。

### 遍历列表
在日常开发中，我们经常需要遍历列表的所有元素，对每个元素执行相同的操作。例如，在管理商场的蔬菜时候，需要给所有的蔬菜商品都打7折，并重新生成价格。当我们需要对列表中的每个元素都执行相同的操作时，可使用Python中的`for`循环。
<!--more-->
假设我们有一个蔬菜名单，需要将其中每种蔬菜的名字都打印出来。为此，我们可以采用元素下标的方式分别获取名单中的每个名字，但这种做法会导致多个问题。例如，如果名单很长，将包含大量重复的代码。另外，每当名单的长度发生变化时，都必须修改代码。通过使用`for`循环，可让`Python`去处理这些问题。
下面使用for循环来打印蔬菜单中的所有名字:
``` Python
vegetables = ['potato','tomato','onion']
for name in vegetables:
    print(name)
```
这行代码让Python从列表`vegetables`中取出一个名字，并将其存储在变量`name`中。最后，我们让Python打印前面存储的变量`name`中的名字。这样，对于列表中的每个名字，Python都将重复执行`print(name)`代码。你可以这样解读这些代码：对于列表`vegetables`中的每种蔬菜，都将其名字打印出来。输出很简单，就是列表中所有蔬菜的姓名:
```
potato
tomato
onion
```

##### 详解遍历列表执行过程
循环这种概念很重要，因为它是让计算机自动完成重复工作的常见方式之一。例如，在前面的代码中使用的简单循环中，Python将首先读取其中的第一行代码:
``` Python
for name in vegetables:
```
这行代码让Python获取列表`vegetables`中的第一个值`potato`，并将其存储到变量`name` 中。接下来，Python读取下一行代码:
``` python
print(name) 
```
它让Python打印`vegetables`的值`potato`。由于该列表还包含其他值，Python返回到循环的第一行:
``` Python
for name in vegetables:
```
Python获取列表中的下一个名字`tomato`，并将其存储到变量`name`中，再执行下面这行代码:
``` python
print(name) 
```
Python再次打印变量`vegetables`的值`tomato`。
接下来，Python再次执行整个循环，对列表中的最后一个值`onion`进行处理。
至此，列表中没有其他的值了，因此Python接着执行程序的下一行代码。在这个示例中，`for`循环后面没有其他的代码，因此程序就此结束。 
刚开始使用循环时需要牢记，对列表中的每个元素，都将执行循环指定的步骤，而不管列表包含多少个元素。如果列表包含一百万个元素，Python就重复执行指定的步骤一百万次，且通常速度非常快。
另外，编写`for`循环时，对于用于存储列表中每个值的临时变量，可指定任何名称。比如说：
``` Python
for dog in dogs:
for cat in cats:
for item in item_list:
```
这些写法都是可以的。

##### 在For循环中做更多操作
在for循环中，可以获取到每一个元素，可对每个元素执行任何操作。比如说我们对每一种蔬菜都输出一句话。
``` python
vegetables = ['potato','tomato','onion']
for name in vegetables:
    print(name + ' is good !')
```
相比于前一个示例，唯一的不同是对于每种蔬菜，都打印了一条以其名字为抬头的消息。这个循环第一次迭代时，变量`name`的值为`potato`，因此Python打印的第一条消息的抬头为`potato`。第二次迭代时，消息的抬头为`tomato`，而第三次迭代时，抬头为`onion`。
下面的输出表明，对于列表中的每种蔬菜，都打印了一条个性化消息:
``` python
potato is good !
tomato is good !
onion is good !
```
在for循环中，想包含多少行代码都可以。在代码行`for name in vegetables`后面，每个**缩进的**代码行都是循环的一部分，且将针对列表中的每个值都执行一次。因此，可对列表中的每个值执行任意次数的操作。
下面再添加一行代码:
``` python
vegetables = ['potato','tomato','onion']
for name in vegetables:
    print(name + ' is good !')
    print(name + ' is a vegetable!')
```
由于两条`print`语句都缩进了，因此它们都将针对列表中的每位蔬菜都执行一次。输出结果如下：
``` python
potato is good !
potato is a vegetable!
tomato is good !
tomato is a vegetable!
onion is good !
onion is a vegetable!
```
在`for`循环中，想包含多少行代码都可以。这种方式在开发过程中很有用。

### 避免缩进错误
Python根据**缩进**来判断代码行与前一个代码行的关系。在前面的示例中，对每种蔬菜的输出代码行是`for`循环的一部分，因为它们缩进了。Python通过使用缩进让代码更易读。
简单地说，它要求你使用缩进让代码整洁而结构清晰。在较长的Python程序中，你将看到缩进程度各不相同的代码块，这让你对程序的组织结构有大致的认识。 当你开始使用缩进时，需要注意一些常见的缩进错误。
例如，有时候，程序员会将不需要缩进的代码块缩进，而对于必须缩进的代码块却忘了缩进。通过查看这些错误示例，有助于我们以后避开它们，以及在它们出现在程序中时进行修复。下面来看一些较为常见的缩进错误。

##### 忘记缩进
对于位于`for`语句后面且属于循环组成部分的代码行，一定要缩进。如果你忘记缩进，运行会直接报错:
```python
vegetables = ['potato','tomato','onion']
for name in vegetables:
print(name)
```
`print`语句应缩进却没有缩进。Python没有找到期望缩进的代码块时，会让你知道哪行代码有问题。
``` python
 File "<stdin>", line 2
    print(name)
        ^
IndentationError: expected an indented block
```
通常，将紧跟在for语句后面的代码行缩进，可消除这种缩进错误。
##### 忘记缩进额外的代码行
有时候，循环能够运行而不会报告错误，但结果可能会出乎意料。试图在循环中执行多项任务，却忘记缩进其中的一些代码行时，就会出现这种情况。
```python
vegetables = ['potato','tomato','onion']
for name in vegetables:
    print(name + ' is good !')
print(name + ' is a vegetable!')
```
第二个`print`语句原本需要缩进，但Python发现`for`语句后面有一行代码是缩进的，因此它没有报告错误。最终的结果是，对于列表中的每种蔬菜，都执行了第一条`print`语句，因为它缩进了；而第二条`print`语句没有缩进，因此它只在循环结束后执行一次。由于变量 `name` 的终值为`onion`，因此只有一条输出了`onion is a vegetable!`:
``` python
potato is good !
tomato is good !
onion is good !
onion is a vegetable!
```
这是一个逻辑错误。从语法上看，这些代码是没问题的，但由于存在逻辑错误，结果并不符合预期。如果你预期某项操作将针对每个列表元素都执行一次，但它却只执行了一次，请确定是否需要将一行或多行代码缩进。

##### 不必要的缩进
如果你不小心缩进了无需缩进的代码行，同样运行的时候也会报错:
``` python
message = "Hello Python world!"
    print(message)
```
`print`语句无需缩进，因为它并不属于前一行代码，运行的时候会帮我们指出这种错误:
``` python
    print(message)
    ^
IndentationError: unexpected indent
```
为避免意外缩进错误，请只缩进需要缩进的代码。在前面编写的程序中，只有要在`for`循环中对每个元素执行的代码就需要缩进。
##### 循环后不必要的缩进
如果我们不小心缩进了应在循环结束后执行的代码，这些代码将针对每个列表元素重复执行。 在有些情况下，这可能导致Python报告语法错误，但在大多数情况下，这只会导致逻辑错误。例如：
``` python
vegetables = ['potato','tomato','onion']
for name in vegetables:
    print(name + ' is good !')
    print(name + ' is a vegetable!')
    ## 这一行代码被缩进
    print('There are three kinds of vegetables.')
```
那么输出就会变成以下这个样子：
``` python
potato is good !
potato is a vegetable!
There are three kinds of vegetables
tomato is good !
tomato is a vegetable!
There are three kinds of vegetables
onion is good !
onion is a vegetable!
There are three kinds of vegetables.
```
这也是一个逻辑错误。Python不知道你的本意，只要代码符合语法，它就会运行。所以我们应该时刻保持警惕，不要用错了缩进。
##### 遗漏了冒号
`for`语句末尾的冒号告诉Python，下一行是循环的第一行。
``` python
vegetables = ['potato','tomato','onion']
for name in vegetables
    print(name + ' is good !')
```


``` python

    for name in vegetables
                         ^
SyntaxError: invalid syntax
```
如果你不小心遗漏了冒号，如上所示，将导致语法错误，因为Python不知道你意欲何为。这种错误虽然易于消除，但并不那么容易发现。

### 数值列表
Python函数`range()`让你能够轻松地生成一系列的数字。例如，可以像下面这样使用函数`range()`来打印一系列的数字:
``` python
for value in range(1,5):
    print(value)
```
上述代码好像应该打印数字1~5，但实际上它不会打印数字5:
``` python
1
2
3
4
```
在这个示例中，`range()`只是打印数字1~4，这是你在编程语言中经常看到的差一行为的结果。函数`range()`让Python从你指定的第一个值开始数，并在到达你指定的第二个值后停止，因此输出不包含第二个值(这里为5)。
要打印数字1~5，需要使用`range(1,6)`:
``` python
for value in range(1,6):
    print(value)
```
这样，输出将从1开始，到5结束:
``` python
1
2
3
4
5
```
使用`range()`时，如果输出不符合预期，请尝试将指定的值加`1`或减`1`。
##### 使用range()创建数字列表
要创建数字列表，可使用函数`list()`将`range()`的结果直接转换为列表。如果将`range()`作为`list()`的参数，输出将为一个数字列表。
在上面的示例中，我们打印了一系列数字。要将这些数字转换为一个列表，可使用`list():`
``` python
numbers = list(range(1,6))
print(numbers)
```
结果如下:
``` python
[1, 2, 3, 4, 5]
```
使用函数`range()`时，还可指定**步长**。例如，下面的代码打印1~10内的偶数:
``` python
even_numbers = list(range(2,11,2)) 
print(even_numbers)
```
在这个示例中，函数`range()`从2开始数，然后不断地加2，直到达到或超过终值(11)，因此 输出如下:
``` python
[2, 4, 6, 8, 10]
```
使用函数`range()`几乎能够创建任何需要的数字集，例如，如何创建一个列表，其中包含前10个整数(即1~10)的平方呢？在Python中，两个星号`**`表示乘方运算。下面的代码演示如何将前10个整数的平方加入到一个列表中:
``` python
squares = []
for value in range(1,11):
    square = value**2
    squares.append(square)
print(squares)
```
首先，我们创建了一个空列表；接下来，使用函数`range()`让Python遍历1~10的值。在循环中，计算当前值的平方，并将结果存储到变量square中。然后，将新计算得到的平方值附加到列表`squares`末尾。最后，循环结束后，打印列表`squares`:
``` python
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
##### 对数字列表执行简单的统计计算
有几个专门用于处理数字列表的Python函数。例如，你可以轻松地找出数字列表的最大值、最小值和总和:
``` python
digits = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0] 
### 输出最小值
print(min(digits))
### 输出最大值
print(max(digits))
### 计算总和
print(sum(digits))
0
9
45
```
##### 列表解析
列表解析将`for`循环和创建新元素的代码合并成一行，并自动附加新元素。下面的示例使用列表解析创建你在前面看到的平方数列表:
``` python
squares = [value**2 for value in range(1,11)] 
print(squares)
```
要使用这种语法，首先指定一个描述性的列表名，如`squares`；然后，指定一个左方括号，并定义一个表达式，用于生成你要存储到列表中的值。在这个示例中，表达式为`value**2`，它来计算平方值。接下来，编写一个for循环，用于给表达式提供值，再加上右方括号。在这个示例中，`for`循环为`for value in range(1,11)`，它将值1~10提供给表达式`value**2`。请注意，这里的for语句末尾没有冒号。
  结果与你在前面看到的平方数列表相同:
``` python
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
要创建自己的列表解析，需要经过一定的练习，但能够熟练地创建常规列表后，你会发现这样做是完全值得的。当你觉得编写三四行代码来生成列表有点繁复时，就应考虑创建列表解析了。


### 列表中的一部分
在上面的内容中，我们学习了如何访问单个列表元素。接下来，我们将学习如何处理列表的所有元素。我们还可以处理列表的部分元素——Python称之为**切片**。
##### 切片
要创建切片，可指定要使用的第一个元素和最后一个元素的索引。与函数`range()`一样，Python 在到达你指定的第二个索引前面的元素后停止。要输出列表中的前三个元素，需要指定索引0~3， 这将输出分别为0、1和2的元素。
我们还是以蔬菜列表为例:
``` python
vegetables = ['potato','tomato','onion','leek']
print(vegetables[0:3])
```
上面的代码打印该列表的一个切片，其中只包含三种蔬菜。输出也是一个列表，其中包含前三种蔬菜:
``` python
['potato', 'tomato', 'onion']
```
你可以生成列表的任何子集，例如，如果你要提取列表的第2~4个元素，可将起始索引指定为1，并将终止索引指定为4:
``` python
vegetables = ['potato','tomato','onion','leek']
print(vegetables[1:4])
```
这一次，切片始于`tomato`，终于`leek`:
``` python
['tomato', 'onion', 'leek']
```
如果你没有指定第一个索引，Python将自动从列表开头开始:
``` python
vegetables = ['potato','tomato','onion','leek']
print(vegetables[:4])
```
由于没有指定起始索引，Python从列表开头开始提取:
```python
['potato', 'tomato', 'onion', 'leek']
```
要让切片终止于列表末尾，也可使用类似的语法。例如，如果要提取从第3个元素到列表末 尾的所有元素，可将起始索引指定为2，并省略终止索引:
``` python
vegetables = ['potato','tomato','onion','leek']
print(vegetables[2:])
```
Python将返回从第3个元素到列表末尾的所有元素:
``` python
['onion', 'leek']
```
无论列表多长，这种语法都能够让你输出从特定位置到列表末尾的所有元素。前面我们了解过，负数索引返回离列表末尾相应距离的元素，因此你可以输出列表末尾的任何切片。例如，如果你要输出名单上的最后三种蔬菜，可使用切片`vegetables[-3:]`:
``` python
vegetables = ['potato','tomato','onion','leek']
print(vegetables[-3:])
['tomato', 'onion', 'leek']
```

##### 遍历切片
如果要遍历列表的部分元素，可在for循环中使用切片。在下面的示例中，我们遍历前三种蔬菜，并打印它们的名字:
``` Python
vegetables = ['potato','tomato','onion','leek']
print("Here are the first three vegetable:")
for name in vegetables[:3]:
    print(name.title())
```
输出结果：
``` python
Here are the first three vegetable:
Potato
Tomato
Onion
```
在很多情况下，切片都很有用。例如，编写游戏时，你可以在玩家退出游戏时将其最终得分加入到一个列表中。然后，为获取该玩家的三个最高得分，你可以将该列表按降序排列，再创建一个只包含前三个得分的切片。处理数据时，可使用切片来进行批量处理；编写Web应用程序时，可使用切片来分页显示信息，并在每页显示数量合适的信息。

##### 复制列表
我们经常需要根据既有列表创建全新的列表。下面来介绍复制列表的工作原理，以及复制列表可提供极大帮助。
要复制列表，可创建一个包含整个列表的切片，方法是同时省略起始索引和终止索引(`[:]`)。 这让Python创建一个始于第一个元素，终止于最后一个元素的切片，即复制整个列表。
例如，假设有一个列表，其中包含你最喜欢的四种食品，而你还想创建另一个列表，在其中包含一位朋友喜欢的所有食品。不过，你喜欢的食品，这位朋友都喜欢，因此你可以通过复制来创建这个列表:
``` python
my_foods = ['pizza', 'falafel', 'carrot cake'] friend_foods = my_foods[:]
print("My favorite foods are:") 
print(my_foods)
print("\nMy friend's favorite foods are:") 
print(friend_foods)
```
我们首先创建了一个名为`my_foods`的食品列表，然后创建了一个名为`friend_foods`的新列表。我们在不指定任何索引的情况下从列表`my_foods`中提取一个切片，从而创建了这个列表的副本，再将该副本存储到变量`friend_foods`中。打印每个列表后，我们发现它们包含的食品相同:
``` python
My favorite foods are:
['pizza', 'falafel', 'carrot cake']
My friend's favorite foods are: 
['pizza', 'falafel', 'carrot cake']
```
为了核实我们确实有两个列表，下面在每个列表中都添加一种食品，并核实每个列表都记录了相应人员喜欢的食品:
``` python
my_foods = ['pizza', 'falafel', 'carrot cake'] 5
friend_foods = my_foods[:]
my_foods.append('cannoli')
friend_foods.append('ice cream') 
print("My favorite foods are:")
print(my_foods)
print("\nMy friend's favorite foods are:") 
print(friend_foods)
```
与前一个示例一样，我们首先将`my_foods`的元素复制到新列表`friend_foods`中。接下来，在每个列表中都添加一种食品:在列表`my_foods`中添加`cannoli`，而在`friend_foods`中添加`ice cream`。最后，打印这两个列表，核实这两种食品包含在正确的列表中。
``` python
My favorite foods are:
['pizza', 'falafel', 'carrot cake', 'cannoli']
My friend's favorite foods are:
['pizza', 'falafel', 'carrot cake', 'ice cream']
``` 
上面的输出表明，`cannoli`包含在你喜欢的食品列表中，而`ice cream`没有。`ice cream`包含在你朋友喜欢的食品列表中，而`cannoli`没有。倘若我们只是简单地将`my_foods`赋给`friend_foods`，就不能得到两个列表。例如，下例演示了在不使用切片的情况下复制列表的情况:
``` python
my_foods = ['pizza', 'falafel', 'carrot cake']
#这行不通 
friend_foods = my_foods
my_foods.append('cannoli') 
friend_foods.append('ice cream')
print("My favorite foods are:") 
print(my_foods)
print("\nMy friend's favorite foods are:") 
print(friend_foods)
```
这里将`my_foods`赋给`friend_foods`，而不是将`my_foods`的副本存储到`friend_foods`。这种语法实际上是让Python将新变量`friend_foods`关联到包含在`my_foods`中的列表，因此这两个变量都指向同一个列表。鉴于此，当我们将`cannoli`添加到`my_foods`中时，它也将出现在`friend_food`中；同样，虽然`ice cream`好像只被加入到了`friend_foods`中，但它也将出现在这两个列表中。
输出表明，两个列表是相同的，这并非我们想要的结果:
``` python
My favorite foods are:
['pizza', 'falafel', 'carrot cake', 'cannoli', 'ice cream']
My friend's favorite foods are:
['pizza', 'falafel', 'carrot cake', 'cannoli', 'ice cream']
```



> 8-1 动物:想出至少三种有共同特征的动物，将这些动物的名称存储在一个列表中，再使用for循环将每种动物的名称都打印出来。
 修改这个程序，使其针对每种动物都打印一个句子，如"A dog would make a great pet"。在程序末尾添加一行代码，指出这些动物的共同之处，如打印诸如"Any of these animals would make a great pet!"这样的句子。
8-2  数到 20:使用一个 for 循环打印数字 1~20(含)。
8-3 计算 1~ 1000000 的总和:创建一个列表，其中包含数字1~1000000，再使用min()和max()核实该列表确实是从1开始，到1000000 结束的。另外，对这个列表调用函数sum()，体会一下Python将一百万个数字相加需要多长时间。
8-4 3的倍数:创建一个列表，其中包含 3~30 内能被3整除的数字;再使用一个for循环将这个列表中的数字都打印出来。
8-5 切片:修改8-1的代码，在末尾添加几行代码，以完成如下任务。 打印消息"The first three items in the list are:"，再使用切片来打印列表的前三个元素。打印消息"Three items from the middle of the list are:"，再使用切片来打印列表中间的三个元素。打印消息"The last three items in the list are:"，再使用切片来打印列表末尾的三个元素。

想查看作业答案可以去[我的Githu仓库](https://github.com/Johnson8888/learn_python)
***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)