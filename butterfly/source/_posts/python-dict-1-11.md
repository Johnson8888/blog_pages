---
title: 【Python 1-11】Python手把手教程之——字典的用法和对字典的管理
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-09 20:18:17
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
tags:
    - Python
    - Python dict
    - Python 字典
categories: Python
keywords: 'Python,Python dict,Python 字典'
description:  字典是另一种可变容器模型，且可存储任意类型对象。字典的每个键值 key=>value 对用冒号:分割，每个键值对之间用逗号 , 分割，整个字典包括在花括号 {} 中。
photos:
fileName:
type:
---

作者 | 弗拉德 
来源 | 弗拉德（公众号：fulade_me)

### 字典
字典是另一种可变容器模型，且可存储任意类型对象。字典的每个键值 `key=>value`对用冒号`:`分割，每个键值对之间用逗号`,`分割，整个字典包括在花括号`{}`中。

#### 使用字典
在Python中，字典是一系列**键—值**对。每个键都与一个值相关联，你可以使用键来访问与之相关联的值。与键相关联的值可以是数字、字符串、列表乃至字典。事实上，可将任何Python对象用作字典中的值。  
来看一个游戏，其中包含一些外星人，这些外星人的颜色和点数各不相同，如下所示: 
``` py
alien_0 = {'color': 'green', 'points': 5}
```
键—值对是两个相关联的值。指定键时，Python将返回与之相关联的值。键和值之间用冒号分隔，而键—值对之间用逗号分隔。在字典中，你想存储多少个键—值对都可以。
最简单的字典只有一个键—值对，如下述修改后的字典`alien_0`所示: 
```py
alien_0 = {'color': 'green'}
```
这个字典只存储了一项有关`alien_0`的信息，具体地说是这个外星人的颜色。在这个字典中，字符串`color`是一个键，与之相关联的值为`green`。

#### 访问字典中的值
要获取与键相关联的值，可依次指定字典名和放在方括号内的键，如下所示:
``` py
alien_0 = {'color': 'green'}
print(alien_0['color'])
```
这将返回字典`alien_0`中与键`color`相关联的值:
``` py
green
```
字典中可包含任意数量的键—值对。例如，下面是最初的字典alien_0，其中包含两个键— 值对:
``` py
alien_0 = {'color': 'green', 'points': 5}
```
现在，你可以访问外星人`alien_0`的颜色和点数。如果玩家射杀了这个外星人，你就可以使用下面的代码来确定玩家应获得多少个点:
```py
alien_0 = {'color': 'green', 'points': 5}
new_points = alien_0['points']
print("You just earned " + str(new_points) + " points!")
```
上述代码首先定义了一个字典，然后从这个字典中获取与键`points`相关联的值，并将这个值存储在变量`new_points`中。接下来，将这个整数转换为字符串，并打印一条消息，指出玩家获得了多少个点:
``` py
You just earned 5 points!
```
#### 添加键—值对
字典是一种动态结构，可随时在其中添加键—值对。要添加键—值对，可依次指定字典名、用方括号括起的键和相关联的值。
下面在字典`alien_0`中添加两项信息:

外星人的x坐标和y坐标，让我们能够在屏幕的特定位置显示该外星人。我们将这个外星人放在屏幕左边缘，且离屏幕上边缘25像素的地方。由于屏幕坐标系的原点通常为左上角，因此要将该外星人放在屏幕左边缘，可将x坐标设置为0，要将该外星人放在离屏幕顶部25像素的地方，可将y坐标设置为25，如下所示:
``` py
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)
alien_0['x_position'] = 0 
alien_0['y_position'] = 25
print(alien_0)
```
我们首先定义了前面一直在使用的字典，然后打印这个字典，以显示其信息快照。我们在这个字典中新增了一个键—值对，其中的键为`x_position`，而值为0。接着我们重复这样的操作，但使用的键为`y_position`。打印修改后的字典时，将看到这两个新增的键—值对:
``` py
{'color': 'green', 'points': 5}
{'color': 'green', 'points': 5, 'y_position': 25, 'x_position': 0}
```
这个字典的最终版本包含四个键—值对，其中原来的两个指定外星人的颜色和点数，而新增的两个指定位置。注意，键—值对的排列顺序与添加顺序不同。Python不关心键—值对的添加顺序，而只关心键和值之间的关联关系。
#### 创建空字典
有时候，在空字典中添加键—值对是为了方便，而有时候必须这样做。为此，可先使用一对空的花括号定义一个字典，再分行添加各个键—值对。例如，下例演示了如何以这种方式创建字典`alien_0`:
``` py
alien_0 = {}
alien_0['color'] = 'green' 
alien_0['points'] = 5
print(alien_0)
```
这里首先定义了空字典`alien_0`，再在其中添加颜色和点数，得到前述示例一直在使用的字典:
``` py
{'color': 'green', 'points': 5}
```
使用字典来存储用户提供的数据或在编写能自动生成大量键—值对的代码时，通常都需要先定义一个空字典。
#### 修改字典中的值
要修改字典中的值，可依次指定字典名、用方括号括起的键以及与该键相关联的新值。
例如，假设随着游戏的进行，需要将一个外星人从绿色改为黄色:
``` py
alien_0 = {'color': 'green'}
print("The alien is " + alien_0['color'] + ".")
alien_0['color'] = 'yellow'
print("The alien is now " + alien_0['color'] + ".")
```
我们首先定义了一个表示外星人`alien_0`的字典，其中只包含这个外星人的颜色。接下来，我们将与键`color`相关联的值改为`yellow`。输出表明，这个外星人确实从绿色变成了黄色:
``` py
The alien is green.
The alien is now yellow.
```
来看一个更有趣的例子，对一个能够以不同速度移动的外星人的位置进行跟踪。我们将存储该外星人的当前速度，并据此确定该外星人将向右移动多远:
``` py
alien_0 = {'x_position': 0, 'y_position': 25, 'speed': 'medium'} 
print("Original x-position: " + str(alien_0['x_position']))
# 向右移动外星人
# 据外星人当前速度决定将其移动多远 
if alien_0['speed'] == 'slow':
    x_increment = 1
elif alien_0['speed'] == 'medium':
    x_increment = 2 
else:
# 这个外星人的速度一定很快 
    x_increment = 3
# 新位置等于老位置加上增量
alien_0['x_position'] = alien_0['x_position'] + x_increment
print("New x-position: " + str(alien_0['x_position']))
```
我们首先定义了一个外星人，其中包含初始的x坐标和y坐标，还有速度`medium`。出于简化考虑，我们省略了颜色和点数，但即便包含这些键值对，这个示例的工作原理也不会有任何变化。我们还打印了`x_position`的初始值，这让用户知道这个外星人向右移动了多远。  
然后，使用了一个`if-elif-else`结构来确定外星人应向右移动多远，并将这个值存储在变量`x_increment`中。如果外星人的速度为`slow`，它将向右移动一个单位，如果速度为`medium`，将向右移动两个单位，如果为`fast`，将向右移动三个单位。确定移动量后，将其与`x_position`的当前值相加，再将结果关联到字典中的键`x_position`。
由于这是一个速度中等的外星人，因此其位置将向右移动两个单位:
``` py
Original x-position: 0
New x-position: 2
```
通过修改外星人字典中的值，可改变外星人的行为。例如，要将这个速度中等的外星人变成速度很快的外星人，可添加如下代码行: 
```py
alien_0['speed'] = fast 
```
这样，再次运行这些代码时，其中的`if-elif-else`结构将把一个更大的值赋给变量
`x_increment`。

#### 删除键—值对
对于字典中不再需要的信息，可使用`del`语句将相应的键—值对彻底删除。使用`del`语句时，必须指定字典名和要删除的键。
例如，下面的代码从字典`alien_0`中删除键`points`及其值:
``` py
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)
del alien_0['points'] 
print(alien_0)
```
上述代码将键`points`从字典`alien_0`中删除，同时删除与这个键相关联的值。输出表明，键`points`及其值5已从字典中删除，但其他键—值对不受影响:
``` py
{'color': 'green', 'points': 5}
{'color': 'green'}
```

### 遍历字典
一个Python字典可能只包含几个键—值对，也可能包含数百万个键—值对。鉴于字典可能包含大量的数据，Python支持对字典遍历。字典可用于以各种方式存储信息，因此有多种遍历字典的方式，可遍历字典的所有键—值对、键或值。
#### 遍历所有的键—值对
探索各种遍历方法前，先来看一个新字典，它用于存储有关网站用户的信息。下面的字典存储一名用户的用户名、名和姓:
``` py
user_0 = {
    'username': 
    'efermi', 
    'first': 
    'enrico', 
    'last': 
    'fermi',
}
```
我们可以使用一个for循环来遍历这个字典:
``` py
for key, value in user_0.items(): 
    print("\nKey: " + key)
    print("Value: " + value)
```
要实现遍历字典的for循环，可声明两个变量，用于存储键—值对中的键和值。 对于这两个变量，可使用任何名称。下面的代码使用了简单的变量名，这完全可行:
``` py
for k, v in user_0.items()
```
for语句的第二部分包含字典名和方法`items()`，它返回一个键—值对列表。接下来，for循环依次将每个键—值对存储到指定的两个变量中。我们使用这两个变量来打印每个键及其相关联的值。第一条`print`语句中的"\n"确保在输出每个键—值对前都插入一个空行:
``` py
Key: last 
Value: fermi

Key: first 
Value: enrico

Key: username 
Value: efermi
```
即便遍历字典时，键—值对的返回顺序也与存储顺序不同。Python不关心键—值对的存储顺序，而只跟踪键和值之间的关联关系。

#### 遍历字典中的所有键
在不需要使用字典中的值时，方法keys()很有用。下面来遍历字典`favorite_languages`，并将每个被调查者的名字都打印出来:
``` py
favorite_languages = {'jen': 'python',
                     'sarah': 'c', 
                     'edward': 'ruby', 
                     'phil': 'python'}
for name in favorite_languages.keys(): 
    print(name.title())
```
`.keys()`方法提取字典`favorite_languages`中的所有键，并依次将它们存储到变量`name`中。输出列出了每个被调查者的名字:
``` py
Jen 
Sarah 
Phil 
Edward
```
遍历字典时，会默认遍历所有的键，因此，如果将上述代码中的`for name in favorite_ languages.keys():`替换为`for name in favorite_languages:`，输出将不变。如果显式地使用方法`keys()`可让代码更容易理解，你可以选择这样做，也可省略它。在这种循环中，可使用当前键来访问与之相关联的值。

下面来打印两条消息，指出两位朋友喜欢的语言。我们像前面一样遍历字典中的名字，但在名字为指定朋友的名字时，打印一条消息，指出其喜欢的语言:
``` py
favorite_languages = { 'jen': 'python',
                        'sarah': 'c', 
                        'edward': 'ruby', 
                        'phil': 'python'}
friends = ['phil', 'sarah']
for name in favorite_languages.keys():
    print(name.title())
    if name in friends:
        print(" Hi " + name.title() + ", I see your favorite language is " + favorite_languages[name].title() + "!")
```
我们创建了一个列表，其中包含我们要通过打印消息，指出其喜欢的语言的朋友。 在循环中，我们打印每个人的名字，并检查当前的名字是否在列表`friends中`。
如果在列表中，就打印一句特殊的问候语，其中包含这位朋友喜欢的语言。为访问喜欢的语言，我们使用了字典名，并将变量`name`的当前值作为键。每个人的名字都会被打印，但只对朋友打印特殊消息:
``` py
Jen
Sarah
 Hi Sarah, I see your favorite language is C!
Edward
Phil
 Hi Phil, I see your favorite language is Python!
```
#### 按顺序遍历字典中的所有键

字典总是明确地记录键和值之间的关联关系，但获取字典的元素时，获取顺序是不可预测的。
要以特定的顺序返回元素，一种办法是在`for`循环中对返回的键进行排序。可使用函数`sorted()`来获得按特定顺序排列的键列表的副本:
``` py
favorite_languages = { 'jen': 'python','sarah': 'c','edward': 'ruby','phil': 'python'}
for name in sorted(favorite_languages.keys()):
    print(name.title() + ", thank you for taking the poll.")
```
这个示例中，对方法`dictionary.keys()`的结果调用了函数`sorted()`。 这让Python列出字典中的所有键，并在遍历前对这个列表进行排序。输出表明，按顺序显示了所有被调查者的名字:
``` py
Edward, thank you for taking the poll. 
Jen, thank you for taking the poll. 
Phil, thank you for taking the poll. 
Sarah, thank you for taking the poll.
```
#### 遍历字典中的所有值
如果你只想知道字典包含的值，可使用方法`values()`，它返回一个值列表，而不包含任何键。
例如，如果我们想获得一个这样的列表，即其中只包含被调查者选择的各种语言，而不包含被调查者的名字，可以这样做:
``` py
favorite_languages = { 'jen': 'python','sarah': 'c', 'edward': 'ruby', 'phil': 'python'}
print("The following languages have been mentioned:")  
for language in favorite_languages.values():
    print(language.title())
```
这条for语句提取字典中的每个值，并将它们依次存储到变量`language`中。通过打印这些值，就获得了一个列表，其中包含被调查者选择的各种语言:
``` py
The following languages have been mentioned: 
Python
C
Python
Ruby
```
这种做法提取字典中所有的值，而没有考虑是否重复。涉及的值很少时，这也许不是问题，但如果被调查者很多，最终的列表可能包含大量的重复项。为剔除重复项，我们可使用集合`set`。 集合类似于列表，但每个元素都必须是独一无二的:
``` py
favorite_languages = { 'jen': 'python',
'sarah': 'c', 'edward': 'ruby', 'phil': 'python', }
print("The following languages have been mentioned:")
    for language in set(favorite_languages.values()): 
        print(language.title())
```
通过对包含重复元素的列表调用`set()`，可以帮我们找出列表中独一无二的元素，并使用这些元素来创建一个集合。我们使用了`set()`来提取`favorite_languages.values()`中不同的语言。
结果是一个不重复的列表，其中列出了被调查者提及的所有语言:
``` py
The following languages have been mentioned: 
Python
C
Ruby
```
### 嵌套
有时候，需要将一系列字典存储在列表中，或将列表作为值存储在字典中，这称为**嵌套**。你可以在列表中嵌套字典、在字典中嵌套列表甚至在字典中嵌套字典，嵌套是一项强大的功能。
#### 字典列表
字典`alien_0`包含一个外星人的各种信息，但无法存储第二个外星人的信息，更别说屏幕上全部外星人的信息了。如何管理成群结队的外星人呢?一种办法是创建一个外星人列表，其中每个外星人都是一个字典，包含有关该外星人的各种信息。
例如，下面的代码创建一个包含三个外 星人的列表:
``` py
alien_0 = {'color': 'green', 'points': 5}
alien_1 = {'color': 'yellow', 'points': 10}
alien_2 = {'color': 'red', 'points': 15}
aliens = [alien_0, alien_1, alien_2]
for alien in aliens:
    print(alien)
```
我们首先创建了三个字典，其中每个字典都表示一个外星人。我们将这些字典都放到一个名为`aliens`的列表中。最后，我们遍历这个列表，并将每个外星人都打印出来:
``` py
{'color': 'green', 'points': 5} 
{'color': 'yellow', 'points': 10} 
{'color': 'red', 'points': 15}
```
更符合现实的情形是，外星人不止三个，且每个外星人都是使用代码自动生成的。在下面的示例中，我们使用`range()`生成了30个外星人:
``` py
# 创建一个用于存储外星人的空列表 
aliens = []
# 创建30个绿色的外星人
for alien_number in range(30):
    new_alien = {'color': 'green', 'points': 5, 'speed': 'slow'} 
    aliens.append(new_alien)
# 显示前五个外星人 
for alien in aliens[:5]:
    print(alien) 
    # 显示创建了多少个外星人
print("Total number of aliens: " + str(len(aliens)))
```
在这个示例中，首先创建了一个空列表，用于存储接下来将创建的所有外星人。`range()`返回一系列数字，其用途是告诉Python我们要重复这个循环多少次。每次执行这个循环时，都创建一个外星人，并将其附加到列表`aliens`末尾。然后使用一个切片来打印前五个外星人，然后打印列表的长度，以证明确实创建了30个外星人
``` py
{'color': 'green', 'points': 5, 'speed': 'slow'}
{'color': 'green', 'points': 5, 'speed': 'slow'}
{'color': 'green', 'points': 5, 'speed': 'slow'}
{'color': 'green', 'points': 5, 'speed': 'slow'}
{'color': 'green', 'points': 5, 'speed': 'slow'}
Total number of aliens: 30
```
这些外星人都具有相同的特征，但在Python看来，每个外星人都是独立的，这让我们能够独立地修改每个外星人。
在什么情况下需要处理成群结队的外星人呢？想象一下，可能随着游戏的进行，有些外星人会变色且移动速度会加快。必要时，我们可以使用`for`循环和`if`语句来修改某些外星人的颜色。   
例如，要将前三个外星人修改为黄色的、速度为中等且值10个点，可以这样做:
``` py
# 创建一个用于存储外星人的空列表 
aliens = []
# 创建30个绿色的外星人
for alien_number in range (0,30):
    new_alien = {'color': 'green', 'points': 5, 'speed': 'slow'} 
    aliens.append(new_alien)
for alien in aliens[0:3]:
    if alien['color'] == 'green':
        alien['color'] = 'yellow' 
        alien['speed'] = 'medium' 
        alien['points'] = 10

# 显示前五个外星人
for alien in aliens[0:5]:
    print(alien) 
```
由于我们要修改前三个外星人，需要遍历一个只包含这些外星人的切片。当前，所有外星人都是绿色的，但情况并非总是如此，因此我们编写了一条`if`语句来确保只修改绿色外星人。如果外星人是绿色的，我们就将其颜色改为`yellow`，将其速度改为`medium`，并将其点数改为`10`， 如下面的输出所示:
``` py
{'color': 'yellow', 'points': 10, 'speed': 'medium'}
{'color': 'yellow', 'points': 10, 'speed': 'medium'}
{'color': 'yellow', 'points': 10, 'speed': 'medium'}
{'color': 'green', 'points': 5, 'speed': 'slow'}
{'color': 'green', 'points': 5, 'speed': 'slow'}
```
你可以进一步扩展这个循环，在其中添加一个`elif`代码块，将黄色外星人改为移动速度快且值15个点的红色外星人，如下所示(这里只列出了循环，而没有列出整个程序):
``` py
for alien in aliens[0:3]:
    if alien['color'] == 'green':
        alien['color'] = 'yellow'
        alien['speed'] = 'medium'
        alien['points'] = 10
    elif alien['color'] == 'yellow': 
        alien['color'] = 'red' 
        alien['speed'] = 'fast' 
        alien['points'] = 15
```

#### 在字典中存储列表
有时候，需要将列表存储在字典中，而不是将字典存储在列表中。例如，你如何描述顾客点的比萨呢?如果使用列表，只能存储要添加的比萨配料，但如果使用字典，就不仅可在其中包含配料列表，还可包含其他有关比萨的描述。  
在下面的示例中，存储了比萨的两方面信息，外皮类型和配料列表。其中的配料列表是一个与键`toppings`相关联的值。要访问该列表，我们使用字典名和键`toppings`，就像访问字典中的其他值一样。这将返回一个配料列表，而不是单个值:
``` py
# 存储所点比萨的信息 
pizza = {
'crust': 'thick',
'toppings': ['mushrooms', 'extra cheese']}
# 概述所点的比萨
print("You ordered a " + pizza['crust'] + "-crust pizza " +
"with the following toppings:")
for topping in pizza['toppings']: 
    print("\t" + topping)
```
我们首先创建了一个字典，其中存储了有关顾客所点比萨的信息。在这个字典中，一个键是`crust`，与之相关联的值是字符串`thick`，下一个键是`toppings`，与之相关联的值是一个列表，其中存储了顾客要求添加的所有配料。制作前我们概述了顾客所点的比萨。为打印配料，我们编写了一个for循环。为访问配料列表，我们使用了键`toppings`，这样Python将从字典中提取配料列表。
  下面的输出概述了要制作的比萨:
``` py
You ordered a thick-crust pizza with the following  toppings: 
    mushrooms
    extra cheese
```
每当需要在字典中将一个键关联到多个值时，都可以在字典中嵌套一个列表。在前面有关喜欢的编程语言的示例中，如果将每个人的回答都存储在一个列表中，被调查者就可选择多种喜欢的语言。在这种情况下，当我们遍历字典时，与每个被调查者相关联的都是一个语言列表，而不是一种语言，因此，在遍历该字典的`for`循环中，我们需要再使用一个`for`循环来遍历与被调查者相关联的语言列表:
``` py
favorite_languages = {'jen': ['python', 'ruby'],
                    'sarah': ['c'],
                    'edward': ['ruby', 'go'], 
                    'phil': ['python', 'haskell'], }

for name, languages in favorite_languages.items():
    print("\n" + name.title() + "'s favorite languages are:")
    for language in languages: 
        print("\t" + language.title())
```
现在与每个名字相关联的值都是一个列表。请注意，有些人喜欢的语言只有一种，而有些人有多种。遍历字典时，我们使用了变量`languages`来依次存储字典中的每个值，因为我们知道这些值都是列表。在遍历字典的主循环中，我们又使用了一个`for`循环来遍历每个人喜欢的语言列表。现在，每个人想列出多少种喜欢的语言都可以:
``` py
Jen's favorite languages are:
    Python
    Ruby
Sarah's favorite languages are:
    C
Phil's favorite languages are:
    Python
    Haskell
Edward's favorite languages are:
    Ruby
    Go
```
#### 在字典中存储字典
可在字典中嵌套字典，但这样做时，代码可能很快复杂起来。例如，如果有多个网站用户，每个都有独特的用户名，可在字典中将用户名作为键，然后将每位用户的信息存储在一个字典中，并将该字典作为与用户名相关联的值。  
在下面的程序中，对于每位用户，我们都存储了其三项信息:名、姓和居住地，为访问这些信息，我们遍历所有的用户名，并访问与每个用户名相关联的信息字典:
``` py
users = {'aeinstein': {
            'first': 'albert', 
            'last': 'einstein', 
            'location': 'princeton'},
        'mcurie': {
            'first': 'marie', 
            'last': 'curie', 
            'location': 'paris'}}
            
for username, user_info in users.items():
    print("\nUsername: " + username)
    full_name = user_info['first'] + " " + user_info['last']
    location = user_info['location']
    print("\tFull name: " + full_name.title()) 
    print("\tLocation: " + location.title())
```
我们首先定义了一个名为`users`的字典，其中包含两个键:用户名`aeinstein`和`mcurie`，与每个键相关联的值都是一个字典，其中包含用户的名、姓和居住地。我们先遍历字典`users`，让Python依次将每个键存储在变量`username`中，并依次将与当前键相关联的字典存储在变量`user_info`中。
在主循环内部，我们将用户名打印出来。接着我们开始访问内部的字典。变量`user_info`包含用户信息字典，而该字典包含三个键:`first`、`last`和`location`，对于每位用户，我们都使用这些键来生成整洁的姓名和居住地，然后打印有关用户的简要信息:
``` py
Username: aeinstein
Full name: Albert Einstein Location: Princeton
Username: mcurie
Full name: Marie Curie Location: Paris
```


> 小作业
11-1 请想出5个人的名字，并将这些名字用作字典中的键，想出每个人喜欢的一个数字，并将这些数字作为值存储在字典中。打印每个人的名字和喜欢的数字。
11-2 创建一个字典，在其中存储三条大河流及其流经的国家。其中一个键—值对可能是'nile':'egypt'。使用循环为每条河流打印一条消息，如"The Nile runs through Egypt."。使用循环将该字典中每条河流的名字都打印出来。使用循环将该字典包含的每个国家的名字都打印出来。   
11-3 创建多个字典，对于每个字典，都使用一个宠物的名称来给它命名;在每个字典中，包含宠物的类型及其主人的名字。将这些字典存储在一个名为pets的列表中，再遍历该列表，并将宠物的所有信息都打印出来。



想查看作业答案可以去[我的Githu仓库](https://github.com/Johnson8888/learn_python)在文件夹(11-1——11-3)
***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)