---
title: 【Python 1-10】Python手把手教程之——一篇讲透if语句以及if语句的特殊用法
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-08 10:11:20
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
tags:   
    - Python
    - Python if语句
    - Python 控制语句
categories: Python
keywords: 'Python，Python控制语句，Python if语句，Python教程'
description: 编程时经常需要检查一系列条件，并据此决定采取什么措施。在Python中，if语句让你能够检查程序的当前状态，并据此采取相应的措施。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)
### if 简单示例
假设你有一个汽车列表，并想将其中每辆汽车的名称打印出来。对于大多数汽车，都应以首字母大写的方式打印其名称，但对于汽车名'bmw'，应以全大写的方式打印。
下面的代码遍历一个列表，并以首字母大写的方式打印其中的汽车名，但对于汽车名'bmw'，以全大写的方式打印:
``` py
car_list = ['bmw','audi','toyota','honda']
for car in car_list:
    if car == 'bmw':
        print(car.upper())
    else: 
        print(car.title())
```

这个实例中，如果`car`的名字等于`bmw`就会调用`upper()`方法以大写的方式来输出结果，如果不等于`bmw`就以首字母大写的方式输出。
输出结果如下：
``` py
BMW
Audi
Toyota
Honda
```
### 条件语句
每条if语句的核心都是一个值为`True`或`False`的表达式，这种表达式被称为**条件语句**。Python根据条件判断的值为`True`还是`False`来决定是否执行if语句中的代码。如果条件判断的值为`True`， Python就执行紧跟在if语句后面的代码;如果为`False`，Python就不会执行这些代码。
#### 检查是否相等
大多数条件判断都将一个变量的当前值同特定值进行比较。最简单的条件判断检查变量的值是否与某个值相等:
```py
car = 'bmw'
print(car == 'bmw')
True
```
我们首先使用一个等号将car的值设置为`bmw`。接下来，使用两个等号`==`检查`car`的值是否为`bmw`。这个相等运算符在它两边的值相等时返回`True`，否则返回`False`。在这个示例中，两边的值相等，因此返回`True`。
如果变量`car`的值不是`bmw`，上述判断将返回`False`:
``` py
car = 'audi'
print(car == 'bmw')
False
```
一个第一个等号将将变量car的值设置为`audi`。两个等号是发问"变量car的值是`bmw`吗?"。大多数编程语言使用等号的方式都与这里示例的相同。
#### 使用if时不考虑大小写
在Python中检查是否相等时区分大小写，例如，两个大小写不同的值会被视为不相等:
```py
car = 'Audi' 
print(car == 'audi')
False
```
如果大小写很重要，这种行为有其优点。但如果大小写无关紧要，而只想检查变量的值，可将变量的值转换为小写，再进行比较:
``` py
car = 'Audi'
print(car.lower() == 'audi')
True
```
无论值`Audi`的大小写如何，上述判断都将返回`True`，因为该判断不区分大小写。函数`lower()`不会修改存储在变量`car`中的值，因此进行这样的比较时不会影响原来的变量:
``` py
car = 'Audi'
print(car.lower() == 'audi')
True 
print(car)
'Audi'
```
#### 检查不相等
要判断两个值是否不等，可结合使用叹号和等号`!=`，其中的叹号表示**不**，在很多编程语言中都如此。
下面再使用一条if语句来演示如何使用不等运算符。我们将把`苹果`(Apple)存储在一个变量中，而顾客想要购买的是`橘子`(Orange)，输出顾客不需要`苹果`:
``` py
fruit = 'Apple'
if (fruit != 'Orange'):
    print('do not need ' + fruit)
```
将`fruit`的值与`Orange`进行比较，如果它们不相等，Python 将返回`True`，进而执行紧跟在if语句后面的代码;如果这两个值相等，Python将返回`False`，因此 不执行紧跟在if语句后面的代码。
由于`fruit`的值不是`Orange`，因此执行了`print`语句。
我们编写的大多数条件表达式都检查两个值是否相等，但有时候检查两个值是否不等的效率更高。

#### 比较数字
检查数值非常简单，例如，下面的代码检查一个人是否是18:
```py
age = 18
print(age == 18)
True
```
你还可以检查两个数字是否不等，例如，下面的代码在提供的答案不正确时打印一条消息:
``` py
answer = 17
if answer != 42:
    print("That is not the correct answer. Please try again!")
```

条件语句中可包含各种数学比较，如**小于**、**小于等于**、**大于**、**大于等于**:
``` py
age = 19
print(age < 21) 
True
print(age <= 21) 
True
print(age > 21)
False
print(age >= 21) 
False
```
在if语句中可使用各种数学比较，使用起来也很简单。
#### 检查多个条件
你可能想同时检查多个条件，例如，我们需要在两个条件都为`True`时才执行相应的操作，而有时候你只要求一个条件为True时就执行相应的操作。在这些情况下，关键字`and`和`or`可以帮助我们省去很多事情。
**1. 使用and检查多个条件**
要检查是否两个条件都为`True`，可使用关键字`and`将两个条件判断合而为一；如果每个判断都通过了，整个表达式就为`True`；如果至少有一个判断没有通过，整个表达式就为`False`。例如，要检查是否两个人都不小于21岁，可使用下面的判断:
``` py
age_0 = 22 
age_1 = 18
print(age_0 >= 21 and age_1 >= 21)
False
age_1 = 22
print(age_0 >= 21 and age_1 >= 21)
True
```
我们定义了两个用于存储年龄的变量`age_0`和`age_1`。首先我们检查这两个变量是否都大于或等于21，左边的判断通过了，但右边的判断没有通过，因此整个条件表达式的结果为`False`。
接下来我们将`age_1`改为22，这样`age_1`的值大于21，因此两个判断都通过了，导致整个条件表达式的结果为`True`。
为改善可读性，可将每个判断都分别放在一对括号内，但并非必须这样做。如果你使用括号，判断将类似于下面这样:
``` py
(age_0 >= 21) and (age_1 >= 21)
```
**2.使用or检查多个条件**
关键字`or`也能够让你检查多个条件，但只要至少有一个条件满足，就能通过整个判断。仅当两个判断都没有通过时，使用`or`的表达式才为`False`。
下面再次检查两个人的年龄，但检查的条件是至少有一个人的年龄不小于21岁:
```py
age_0 = 22 
age_1 = 18
print(age_0 >= 21 or age_1 >= 21)
True
age_0 = 18
print(age_0 >= 21 or age_1 >= 21)
False
```
同样，我们首先定义了两个用于存储年龄的变量。对`age_0`的判断通过了， 因此整个表达式的结果为`True`。接下来，我们将`age_0`更改为18，在接下来的判断中，两个判断都没有通过，因此整个表达式的结果为`False`。

#### 检查特定值是否包含在列表中
有时候，执行操作前必须检查列表是否包含特定的值。要判断特定的值是否已包含在列表中，可使用关键字`in`。你可能为水果店编写代码，首先创建一个列表，其中包含用户要买的水果，然后检查特定的水果是否包含在该列表中：
```py
fruits = ['apple','banana','cherry']
print('apple' in fruits)
True
print('orange' in fruits)
False
```
关键字`in`可以帮助我们检查`fruits`是否包含`apple`和 `orange`。这种判断很有用，它可以帮助我们能够在创建一个列表后，轻松地检查其中是否包含特定的值。
#### 检查特定值是否不包含在列表中
还有些时候，确定特定的值未包含在列表中很重要。在这种情况下，可使用关键字`not in`。 例如，如果有一个列表，其中包含被禁止在论坛上发表评论的用户，就可在允许用户提交评论前检查他是否被禁言:
``` py
banned_users = ['andrew', 'carolina', 'david'] 
user = 'marie'
if user not in banned_users:
    print(user.title() + ", you can post a response if you wish.")
```
如果`user`的值未包含在列表`banned_users`中，`Python`将返回`True`，进而执行缩进的代码行。
用户`marie`未包含在列表`banned_users`中，因此她将看到一条邀请她发表评论的消息:
`Marie, you can post a response if you wish.`
#### 布尔表达式
与条件表达式一样，布尔表达式的结果要么为`True`，要么为`False`。
布尔值通常用于记录条件，如游戏是否正在运行，或用户是否可以编辑网站的特定内容:
```py
game_active = True 
can_edit = False
```
布尔值判断是一种高效的判断方式。

### if语句
理解条件语句后，就可以开始编写if语句了。前面讨论条件语句时，列举了多个if语句示例，下面更深入地讨论这个主题。

#### if-else 语句
经常需要在条件语句通过了时执行一个操作，并在没有通过时执行另一个操作。在这种情况 下，可使用Python提供的`if-else`语句。`if-else`语句块类似于简单的if语句，但其中的else语句让你能够指定条件不满足时要执行的操作。
下面的代码在一个人够投票的年龄时显示与前面相同的消息，同时在这个人不够投票的年龄时也显示一条消息:
``` py
age = 17
if age >= 18:
    print("You are old enough to vote!")  
    print("Have you registered to vote yet?")
else:
    print("Sorry, you are too young to vote.")
    print("Please register to vote as soon as you turn 18!")
```
条件语句通过了，就执行第一个缩进的print语句块。如果判断结果为`False`，就执行后面的`else`代码块。这次`age`小于`18`，条件判断未通过，因此执行`else`代码块中的代码。
上述代码之所以可行，是因为只存在两种情形:要么够投票的年龄，要么不够。`if-else`结构非常适合用于要让`Python`执行两种操作之一的情形。在这种简单的`if-else`结构中，总是会执行两个操作中的一个。
#### if-elif-else 结构
经常需要检查超过两个的情形，为此可使用Python提供的`if-elif-else`结构。Python只执行`if-elif-else`结构中的一个代码块，它依次检查每个条件判断，直到遇到通过了的条件判断。判断通过后，Python将执行紧跟在它后面的代码，并跳过余下的判断。
在现实世界中，很多情况下需要考虑的情形都超过两个。例如，来看一个根据年龄段收费的 游乐场:
1. 4岁以下免费;
2. 4-18岁收费5元;
3. 18岁(含z以上收费10元。  

如果只使用一条if语句，如何确定门票价格呢?下面的代码确定一个人所属的年龄段，并打印一条包含门票价格的消息:
``` py
age = 12
if age < 4:
    print("Your admission cost is ¥0.")
elif age < 18:
    print("Your admission cost is ¥5.")
else:
    print("Your admission cost is ¥10.")
```
首先if判断一个人是否不满4岁，如果是这样，就打印一条合适的消息，并跳过余下的判断。`elif`代码行其实是另一个if判断，它仅在前面的判断未通过时才会运行。在这里，我们知道这个人不小于4岁，因为第一个判断未通过。如果这个人未满18岁，Python将打印相应的消息，并跳过`else`代码块。如果if判断和elif判断都未通过，Python将运行最后一个`else`代码块中的代码。
在这个示例中，第一个`if`的结果为False，因此不执行其代码块。然而，第二个判断的结果为`True`(12小于18)，因此将执行其代码块。输出为一个句子，向用户指出了门票价格:
``` py
Your admission cost is ¥5.
```
只要年龄超过17岁，前两个判断就都不能通过。在这种情况下，将执行`else`代码块，指出门票价格为10元。为让代码更简洁，可不在`if-elif-else`代码块中打印门票价格，而只在其中设置门票价格， 并在它后面添加一条简单的print语句:
``` py
age = 12
if age < 4:
    price = 0
elif age < 18:
    price = 5
else:
    price = 10
print("Your admission cost is ¥" + str(price) + ".")
```
#### 使用多个elif代码块
可根据需要使用任意数量的`elif`代码块，例如，假设前述游乐场要给老年人打折，可再添加 一个条件判断，判断顾客是否符合打折条件。下面假设对于65岁(含)以上的老人，可以半价(即5元)购买门票:
``` py
age = 12
if age < 4:
    price = 0
elif age < 18:
    price = 5
elif age < 65:
    price = 10
else:
    price = 5
print("Your admission cost is ¥" + str(price) + ".")
```
这些代码大都未变。第二个`elif`代码块通过检查确定年龄不到65岁后，才将门票价格设置为全票价格——10元。
#### 省略else代码块
Python并不要求`if-elif`结构后面必须有else代码块。在有些情况下，`else`代码块很有用,而在其他一些情况下，使用一条`elif`语句来处理特定的情形更清晰:
```py
age = 12
if age < 4: 
    price = 0
elif age < 18: 
    price = 5
elif age < 65: 
    price = 10
elif age >= 65: 
    price = 5
print("Your admission cost is ¥" + str(price) + ".")
```
第三个`elif`代码块在顾客的年龄超过65(含)时，将价格设置为5元，这比使用`else`代码块更清晰些。经过这样的修改后，每个代码块都仅在通过了相应的判断时才会执行。 

`else`是一条包罗万象的语句，只要不满足任何`if`或`elif`中的条件判断，其中的代码就会执行，这可能会引入无效甚至恶意的数据。如果知道最终要的条件，应考虑使用一个`elif`代码块来代替`else`代码块。这样，你就可以肯定，仅当满足相应的条件时，你的代码才会执行。

#### 判断多个条件
`if-elif-else`结构功能强大，但仅适合用于只有一个条件满足的情况，遇到通过了的判断后，Python就跳过余下的判断。这种行为很好，效率很高。
然而，有时候必须检查你关心的所有条件。在这种情况下，应使用一系列不包含`elif`和`else`代码块的简单if语句。在可能有多个条件为`True`，且你需要在每个条件为`True`时都采取相应措施时，适合使用这种方法。
下面再来看前面的水果店示例。如果顾客要了两种水果，就需要确保在货架上包含这些水果:
``` py
requested_fruits = ['pear','banana']
if 'apple' in requested_fruits: 
    print("Adding apple.")
if 'pear' in requested_fruits: 
    print("Adding pear.")
if 'banana' in requested_fruits: 
    print("Adding banana.")
print("\nFinished adding your fruits!")
```
我们首先创建了一个列表，其中包含顾客要的水果。第一个if语句检查顾客是否要了`apple`，如果要了，就打印一条确认消息。第二个if检查水果`pear`的代码也是一个简单的if语句，而不是`elif`或`else`语句，因此不管前一个判断是否通过，都将进行这个判断。第三个if的代码检查顾客是否要了`banana`;不管前两个判断的结果如何，都会执行这些代码。每当这个程序运行时，都会进行这三个独立的判断。 3
在这个示例中，会检查每个条件，因此将在列表中添加`pear`和`banana`输出结果:
``` py
Adding pear.
Adding banana.

Finished adding your fruits!
```
如果像下面这样转而使用`if-elif-else`结构，代码将不能正确地运行，因为有一个判断通过:
``` py
requested_fruits = ['pear','banana']
if 'apple' in requested_fruits: 
    print("Adding apple.")
elif 'pear' in requested_fruits: 
    print("Adding pear.")
elif 'banana' in requested_fruits: 
    print("Adding banana.")
print("\nFinished adding your fruits!")
```
第一个判断检查列表中是否包含`apple`，它通过了，因此在购物车里面添加`apple`。然而，Python将跳过`if-elif-else`结构中余下的判断，不再检查列表中是否包含`pear`和 `banana`。其结果是，将添加顾客要的第一种水果，但不会添加其他的水果:
```py
Adding pear.

Finished adding your fruits!
```
总之，如果你只想执行一个代码块，就使用`if-elif-else`结构，如果要运行多个代码块，就使用一系列独立的if语句。
### 使用if语句处理列表
通过结合使用if语句和列表，可完成一些有趣的任务:对列表中特定的值做特殊处理;高效地管理不断变化的情形，如餐馆是否还有特定的食材;证明代码在各种情形下都将按预期那样运行。
#### 检查特殊元素
在我们开头通过一个简单示例演示了如何处理特殊值`bmw`——它需要采用不同的格式进行打印。既然你对条件判断和if语句有了大致的认识，下面来进一步研究如何检查列表中的特殊值，并对其做合适的处理。
继续使用前面的比水果列表示例。每添加一种水果刀购物车都打印一条消息。通过创建一个列表，在其中包含顾客需要购买的水果，并使用一个循环来指出添加到购物车中的谁，可以以极高的效率编写这样的代码:
``` py
requested_fruits = ['apple', 'pear', 'banana']
for fruit in requested_fruits: 
    print("Adding " + fruit + ".")
print("\nFinished adding your fruits!")
```
输出很简单，因为上述代码不过是一个简单的for循环:
```py
Adding apple.
Adding pear.
Adding banana.

Finished adding your fruits!
```
然而，如果水果店的`apple`卖完了，该如何处理呢?为妥善地处理这种情况，可在for循环中包含一条if语句:
``` py
requested_fruits = ['apple', 'pear', 'banana']
for fruit in requested_fruits: 
    if fruit == 'apple':
        print("Sorry, we are apple right now.")
    else:
        print("Adding " + fruit + ".")
print("\nFinished adding your fruits!")
```
这里在往购物车里面添加的每种水果都进行检查。if代码判断顾客想要的是不是`apple`，如果是，就显示一条消息，已经没有`apple`了。else代码块确保其他水果都能添加到购物车内:
``` py
Sorry, we are apple right now.
Adding pear.
Adding banana.

Finished adding your fruits!
```
#### 确定列表不是空的
到目前为止，对于处理的每个列表都做了一个简单的假设，即假设它们都至少包含一个元素。但是在运行for循环前确定列表是否为空很重要。
下面在给顾客添加购物车时，先判断线上商品列表是不是空的。如果列表是空的，就向顾客确认他是否要点蔬菜，如果列表不为空，就像前面的示例那样添加到购物车:
``` py
requested_fruits = []
if requested_fruits:
    for fruit in requested_fruits:
        print("Adding " + fruit + ".") 
        print("\nFinished adding your fruits!")
else:
    print("Are you sure you want some vegetables?")
```
在这里，我们首先创建了一个空列表，其中不包含任何水果。首先我们进行了判断，而不是直接执行for循环。当我们直接判断一个列表是，Python将在列表至少包含一个元素时返回`True`，并在列表为空时返回`False`。如果`requested_fruits`不为空，就运行与前一个示例相同的for循环，否则，就打印一条消息
在这里，这个列表为空，因此输出如下——询问顾客是否需要蔬菜: 
``` py
Are you sure you want some vegetables?
```
如果这个列表不为空，则会将水果添加到购物车中。





> 小作业:
10-1 检查两个数字相等、不等、大于、小于、大于等于和小于等于。
10-2 请创建一个名为 brush_color 的画笔变量，并将其设置为'green'、'yellow'或'red'。编写一条if语句，检查画笔是否是绿色的，如果是，就打印一条消息。
10-3 像练习 10-2 那样设置画笔的颜色，并编写一个if-else结构。如果画笔是绿色的，就打印一条消息。如果画笔不是绿色的，就打印另一条消息。
10-4 将练习 10-3 中的 if-else 结构改为 if-elif-else 结构。实现以下逻辑
如果画笔是绿色的，就打印一条消息，这是绿色。
如果画笔是黄色的，就打印一条消息，这是黄色。
如果画笔是红色的，就打印一条消息，这是红色。
10-5 人生的不同阶段:设置变量 age 的值，再编写一个if-elif-else 结构，根据 age的值判断处于人生的哪个阶段。
如果一个人的年龄小于 2 岁，就打印一条消息，指出他是婴儿。
如果一个人的年龄为 2(含)-4 岁，就打印一条消息，指出他正蹒跚学步。
如果一个人的年龄为 4(含)-13 岁，就打印一条消息，指出他是儿童。
如果一个人的年龄为 13(含)-20 岁，就打印一条消息，指出他是青少年。
如果一个人的年龄为 20(含)-65 岁，就打印一条消息，指出他是成年人。  
如果一个人的年龄超过 65(含)岁，就打印一条消息，指出他是老年人。


想查看作业答案可以去[我的Githu仓库](https://github.com/Johnson8888/learn_python)
***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)