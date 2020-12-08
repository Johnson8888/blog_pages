---
title: 【Python 1-9】Python手把手教程之——元组和元组的使用技巧
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
  - Python元组
  - Python数据管理
categories: Python
keywords: 'Python列表,Python自学教程,大学生学Python,Python教程,Python管理列表'
date: 2020-12-07 16:48:24
description: 列表非常适合用于存储在程序运行期间可能变化的数据集。列表是可以修改的，这对处理网站的用户列表或游戏中的角色列表至关重要。然而，有时候你需要创建一系列不可修改的元素，元组可以满足这种需求。Python将不能修改的值称为不可变的，而不可变的列表被称为元组。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)


### 元组
列表非常适合用于存储在程序运行期间可能变化的数据集。列表是可以修改的，这对处理网 站的用户列表或游戏中的角色列表至关重要。然而，有时候你需要创建一系列不可修改的元素， 元组可以满足这种需求。Python将不能修改的值称为**不可变**的，而不可变的列表被称为**元组**。


#### 定义元组
元组看起来跟列表很想，但使用**圆括号**而不是方括号来标识。定义元组后，就可以使用索引来访问其元素，就像访问列表元素一样。
例如，如果有一个大小不应改变的矩形，可将其长度和宽度存储在一个元组中，从而确保它们是不能修改的:
``` python
rectangle = (200, 50) 
print(rectangle[0]) 
print(rectangle[1])
```
我们首先定义了元组rectangle，为此我们使用了圆括号而不是方括号。接下来，我们分别打印该元组的各个元素。
输出是
```
200
50
```
下面来尝试修改元组rectangle中的一个元素，看看结果如何:
``` py
rectangle[0] = 250
```
如果我们运行一下上面的代码，就会发现Python返回类型错误消息。因为元组是**不允许被修改的**，因此会出现如下错误：
``` py
TypeError: 'tuple' object does not support item assignment
```
需要记住的是：元组是不可以被修改的，所以使用过程中不能修改元组的值。
#### 遍历元组
像列表一样，也可以使用for循环来遍历元组中的所有值:
``` py
rectangle = (200, 50) 
for r in rectangle:
    print(r)
```
输出结果为：
``` py
200 
50
```
#### 给元组重新赋值
虽然我们不能修改元组内部的值，但是我们可以通过给元组重新赋值的方式来来改变元组的值：
``` py
rectangle = (200, 50) 
for r in rectangle:
    print(r)
rectangle = (400,100)
for r in rectangle:
    print(r)
```
输出如下：
``` py
200
50
400
100
```
相比于列表，元组是更简单的数据结构。如果需要存储的一组值在程序的整个生命周期内都 不变，可使用元组。




> 小作业
9-1 有一个菜摊，提供五种蔬菜。请想出五种简单的蔬菜，并将其存储在一个元组中。
9-2 使用一个 for 循环将该菜摊提供的五种蔬菜都打印出来。
9-3给元组变量赋值，修改其中一种蔬菜为新品种，并使用一个 for 循环将新元组的每个元素都打印出来。
9-4尝试修改其中的一个元素，核实 运行时会报错。

想查看作业答案可以去[我的Githu仓库](https://github.com/Johnson8888/learn_python)
***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)