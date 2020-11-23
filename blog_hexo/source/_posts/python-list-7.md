---
title: python-list-7
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-23 09:49:14
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_number.jpg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_number.jpg
tags:
    - Python
keywords: Python数字,Python自学教程,大学生学Python,Python教程
categories: Python
description:
photos:
fileName:
type:
---
### 列表
列表，在其他语言中又被称为**数组**，是由一系列按特定顺序排列的元素组成。你可以创建包含字母表中所有字母、数字0~9或 所有家庭成员姓名的列表。你也可以创建几个列表，把这几个列表又放在一个列表内。
在Python中，用方括号([])来表示列表，并用逗号来分隔其中的元素。下面是一个简单的 列表示例，这个列表包含几种常见的水果:
``` Python
fruits = ['Apple','Banana','Pear','Orange']
print(fruits)
['Apple','Banana','Pear','Orange']
```
#### 访问列表数据
列表是有序的数据集合，每一个元素都有一个位置参数。比如上面的`fruits`列表里面，其中`Apple`的位置参数是`0`，`Banana`位置参数是`1`。要访问列表元素，可指出列表的名称，再指出元素的索引，并将其放在方括号内。
例如，下面的代码从列表`fruits`中选出第一种水果:
``` Python
fruits = ['Apple','Banana','Pear','Orange']
print(fruits[0])
Apple
```

#### 索引是从0开始的
所有的列表位置参数都是从`0`开始的而不是从1开始的，对于初学者，这个一定要记牢。如果在编码过程中发现取出的元素跟自己预期的不一样，请看看你是否犯了这种简单的错误。
第二个列表元素的索引为1。根据这种简单的计数方式，要访问列表的任何元素，都可将其位置减`1`，并将结果作为索引。例如，要访问第四个列表元素，可使用索引`3`。
下面的代码访问索引`1`和`3`处的水果:
``` Python
fruits = ['Apple','Banana','Pear','Orange']
print(fruits[1])
print(fruits[3])
Banana
Orange
```
Python为访问最后一个列表元素提供了一种特殊语法。通过将索引指定为`-1`，可让Python返 回最后一个列表元素:
``` Python
fruits = ['Apple','Banana','Pear','Orange']
print(fruits[-1])
Orange
```
这里返回的是'Orange'。这种语法很有用，因为你经常需要在不知道列表长度的情况 下访问最后的元素。  
这种约定也适用于其他负数索引，例如，索引`-2`返回倒数第二个列表元素， 索引`-3`返回倒数第三个列表元素，以此类推。

#### 修改列表元素
要修改列表元素，可指定列表名和要修改的元素的索引，再指定该元素的新值。
例如，假设有一个水果列表，其中的第一个元素为'Apple'，如何修改它的值呢?
``` Python
fruits = ['Apple','Banana','Pear','Orange']
print(fruits[0])
print(fruits)
Apple
['Apple','Banana','Pear','Orange']

# 开始把第一个元素修改为 Cherry
fruits[0] = 'Cherry'
print(fruits[0])
print(fruits)
Cherry
['Cherry','Banana','Pear','Orange']
```

#### 在列表中添加元素
你可能出于众多原因要在列表中添加新元素。比如商场里又新增加了一种水果，需要在`fruits`里面中再新增一种水果。Python提供了多种在既有列表中添加新数据的方式。
**1.在列表末尾添加元素**
在列表中添加新元素时，最简单的方式是将元素附加到列表末尾。
``` Python 
fruits = ['Apple','Banana','Pear','Orange']
print(fruits)
fruits.append('Cherry')
print(fruits)
```
方法append()将元素'Cherry'添加到了列表末尾，而不影响列表中的其他所有元素。
```Python
['Apple','Banana','Pear','Orange']
['Apple','Banana','Pear','Orange','Cherry']
```
`append()`可以很好的满足我们动态创建数组的需求。例如，我们可以先创建一个空的列表，在使用一系列的`append()`语句来动态的添加元素。
例如：
``` Python
fruits = []
fruits.append('Apple')
fruits.append('Banana')
fruits.append('Pear')
print(fruits)
['Apple','Banana','Pear']
```
这种创建方式比较常见，因为很多时候，我们的代码的执行过程中才会知道哪些元素需要添加到列表中，哪些元素不需要添加。
**2.在列表中插入元素**  

使用方法`insert()`可在列表的任何位置添加新元素。但是，你需要指定新元素的索引和值。
``` Python
fruits = ['Apple','Banana','Pear']
fruits.insert(0,'Orange')
print(fruits)
['Orange','Apple','Banana','Pear']
```
在该实例中，`Orange`被插入到了索引为`0`的这个位置。这种操作会使列表内的其他的每个元素都右移一个位置。
需要注意的是：插入数据的索引不能超过列表当前最大的索引值，如果我们执行`fruits.insert(10,'Orange')`就会报错。你可以试一下。
#### 从列表中删除元素
我们经常需要从列表中删除一个元素，比如说有`Apple`这种水果因为缺货需要下架了，我们需要将`Apple`从列表中移除掉。你可以根据位置或值来删除列表中的元素。
**1.使用del语句删除元素**  
如果知道要删除的元素在列表中的位置，可直接使用`del`语句。
``` Python
fruits = ['Apple','Banana','Pear']
print(fruits)
['Apple','Banana','Pear']
del fruits[0]
print(fruits)
['Banana','Pear']
```
使用del可删除任何位置处的列表元素，条件是知道其索引。下例演示了如何删除`fruits`列表中的第二个元素
``` Python
fruits = ['Apple','Banana','Pear']
print(fruits)
['Apple','Banana','Pear']
del fruits[1]
print(fruits)
['Apple','Pear']
```
从输出来看，第二个元素已经被删除了。
**2.使用方法pop()删除元素**
有时候，你要将元素从列表中删除，并接着使用它的值。比如你下架了某种水果，需要把这种水果放入到明天的采购列表中。
方法`pop()`可删除列表末尾的元素，并让你能够接着使用它。
``` Python
fruits = ['Apple','Banana','Pear']
print(fruits)
poped_fruit = fruits.pop()
print(fruits)
['Apple', 'Banana']
print(poped_fruit)
Pear
```
执行`pop()`方法后，原数组最后一个元素被移除掉且最后一个元素作为返回值被返回。
**3.pop列表中任何位置处的元素**
想必你已经猜到了，我们只需要在`pop()`方法内传入想移除的元素索引就可以。
``` Python
fruits = ['Apple','Banana','Pear']
print(fruits)
['Apple', 'Banana', 'Pear']
first_fruit = fruits.pop(0)
print(first_fruit)
Apple
```
别忘了，每当你使用pop()时，被弹出的元素就不再在列表中了。
如果你不确定该使用del语句还是`pop()`方法，下面是一个简单的判断标准:如果你要从列表 中删除一个元素，且不再以任何方式使用它，就使用`del`语句;如果你要在删除元素后还能继续 使用它，就使用方法`pop()`。
**4.根据值删除元素**
有时候，我们并不知道要从列表中删除的值所处的位置。如果你只知道要删除的元素的值，可使用`remove()`方法。
``` Python
fruits = ['Apple','Banana','Pear']
print(fruits)
['Apple', 'Banana', 'Pear']
fruits.remove('Apple')
print(fruits)
['Banana', 'Pear']
```
方法remove()只删除在列表中出现的第一个指定的值。也就是说假如`Apple`在`fruits`列表中出现了多次，调用`remove()`方法，只会删除第一个`Apple`。
``` Python
fruits = ['Apple','Banana','Pear','Apple']
print(fruits)
['Apple', 'Banana', 'Pear','Apple']
fruits.remove('Apple')
print(fruits)
['Banana', 'Pear','Apple']
```

### 整合列表
在我们创建的列表中，元素的排列顺序常常是无法预测的。因为我们并非总能控制用户提供数据的顺序。我们又经常需要以特定的顺序呈现信息。有时候，你希望保留列表元素最初的排列顺序，而有时候又需要调整排列顺序。Python提供了很多组织列表的方式，可根据具体情况选用。
#### 使用方法sort()对列表进行永久性排序
Python方法`sort()`让你能够轻松地对列表进行排序。假设你有一个水果列表，并要让其中的水果按字母顺序排列。为简化这项任务，我们假设该列表中的所有值都是小写的。
``` Python
fruits = ['pear','banana','apple']
print(fruits)
['pear', 'banana', 'apple']
fruits.sort()
print(fruits)
['apple', 'banana', 'pear']
```
方法`sort()`永久性地修改了列表元素的排列顺序。现在，`fruits`是按字母顺序排列的，再也无法恢复到原来的排列顺序。  
我们还可以按与字母顺序相反的顺序排列列表元素，为此，只需向`sort()`方法传递参数`reverse=True`即可。
``` Python
fruits.sort(reverse=True)
print(fruits)
['pear', 'banana', 'apple']
```
#### 使用函数sorted()对列表进行临时排序
要保留列表元素原来的排列顺序，同时以特定的顺序呈现它们，可使用函数`sorted()`。函数`sorted()`让你能够按特定顺序显示列表元素，同时不影响它们在列表中的原始排列顺序。下面尝试对`fruits`列表调用这个函数。
``` Python
fruits = ['pear','banana','apple']
print(fruits)
['pear', 'banana', 'apple']
print(sorted(fruits))
['apple', 'banana', 'pear']
# 再一次输出 fruits
print(fruits)
['pear', 'banana', 'apple']
```
注意，调用函数`sorted()`后，列表元素的排列顺序并没有变。如果你要按与字母顺 序相反的顺序显示列表，也可向函数`sorted()`传递参数`reverse=True`。
在并非所有的值都是小写时，按字母顺序排列列表要复杂些，这个问题我们后面再详细解答。
#### 倒序输出列表
要反转列表元素的排列顺序，可使用方法`reverse()`。假设`fruist`列表是按购买时间排列的，可轻松地按相反的顺序排列其中的水果:
``` Python
fruits = ['pear','banana','apple']
print(fruits)
['pear', 'banana', 'apple']
fruits.reverse()
print(fruits)
['apple', 'banana', 'pear']
```
`reverse()`不是指按与字母顺序相反的顺序排列列表元素，而**只是反转**列表元素的排列顺序。
方法`reverse()`永久性地修改列表元素的排列顺序，但可随时恢复到原来的排列顺序，为此 只需对列表再次调用reverse()即可
#### 列表的长度
使用函数`len()`可快速获悉列表的长度
``` Python

fruits = ['pear','banana','apple']
len(fruits)
3
```
获取列表的长度在开发过程中很有用，比如我们利用`len()`方法一下就可以获取到当前有多少种水果正在销售。


> 动手试一试
 请尝试编写一些简短的程序来完成下面的练习，以获得一些使用 Python 列表的第 一手经验。你可能需要为每章的练习创建一个文件夹，以整洁有序的方式存储为完成各 章的练习而编写的程序。
3-1 姓名:将一些朋友的姓名存储在一个列表中，并将其命名为 names。依次访问 该列表中的每个元素，从而将每个朋友的姓名都打印出来。
    3-2 问候语:继续使用练习 3-1 中的列表，但不打印每个朋友的姓名，而为每人打 15 印一条消息。每条消息都包含相同的问候语，但抬头为相应朋友的姓名。
 3-3 自己的列表:想想你喜欢的通勤方式，如骑摩托车或开汽车，并创建一个包含 多种通勤方式的列表。根据该列表打印一系列有关这些通勤方式的宣言，如“I would like to own a Honda motorcycle”。

 3-4 嘉宾名单:如果你可以邀请任何人一起共进晚餐(无论是在世的还是故去的)， 你会邀请哪些人?请创建一个列表，其中包含至少 3 个你想邀请的人;然后，使用这个 列表打印消息，邀请这些人来与你共进晚餐。
3-5 修改嘉宾名单:你刚得知有位嘉宾无法赴约，因此需要另外邀请一位嘉宾。
 以完成练习 3-4 时编写的程序为基础，在程序末尾添加一条 print 语句，指出哪
位嘉宾无法赴约。
 修改嘉宾名单，将无法赴约的嘉宾的姓名替换为新邀请的嘉宾的姓名。
 再次打印一系列消息，向名单中的每位嘉宾发出邀请。
3-6 添加嘉宾:你刚找到了一个更大的餐桌，可容纳更多的嘉宾。请想想你还想邀
请哪三位嘉宾。
 以完成练习 3-4 或练习 3-5 时编写的程序为基础，在程序末尾添加一条 print 语
句，指出你找到了一个更大的餐桌。
使用 insert()将一位新嘉宾添加到名单开头。
 使用 insert()将另一位新嘉宾添加到名单中间。
使用 append()将最后一位新嘉宾添加到名单末尾。
 打印一系列消息，向名单中的每位嘉宾发出邀请。
3-7 缩减名单:你刚得知新购买的餐桌无法及时送达，因此只能邀请两位嘉宾。 以完成练习 3-6 时编写的程序为基础，在程序末尾添加一行代码，打印一条你只 3
  能邀请两位嘉宾共进晚餐的消息。
使用 pop()不断地删除名单中的嘉宾，直到只有两位嘉宾为止。每次从名单中弹
出一位嘉宾时，都打印一条消息，让该嘉宾知悉你很抱歉，无法邀请他来共进
晚餐。
 对于余下的两位嘉宾中的每一位，都打印一条消息，指出他依然在受邀人之列。 使用 del 将最后两位嘉宾从名单中删除，让名单变成空的。打印该名单，核实程
序结束时名单确实是空的。

    
       3-8 放眼世界:想出至少 5 个你渴望去旅游的地方。
 将这些地方存储在一个列表中，并确保其中的元素不是按字母顺序排列的。
 按原始排列顺序打印该列表。不要考虑输出是否整洁的问题，只管打印原始 18
 Python 列表。
使用 sorted()按字母顺序打印这个列表，同时不要修改它。
 再次打印该列表，核实排列顺序未变。
使用 sorted()按与字母顺序相反的顺序打印这个列表，同时不要修改它。
    再次打印该列表，核实排列顺序未变。
使用 reverse()修改列表元素的排列顺序。打印该列表，核实排列顺序确实变了。 使用 reverse()再次修改列表元素的排列顺序。打印该列表，核实已恢复到原来
的排列顺序。
使用 sort()修改该列表，使其元素按字母顺序排列。打印该列表，核实排列顺
序确实变了。
使用 sort()修改该列表，使其元素按与字母顺序相反的顺序排列。打印该列表，
核实排列顺序确实变了。
3-9 晚餐嘉宾:在完成练习 3-4~练习 3-7 时编写的程序之一中，使用 len()打印一 条消息，指出你邀请了多少位嘉宾来与你共进晚餐。
3-10 尝试使用各个函数:想想可存储到列表中的东西，如山岳、河流、国家、城 市、语言或你喜欢的任何东西。编写一个程序，在其中创建一个包含这些元素的列表， 然后，对于本章介绍的每个函数，都至少使用一次来处理这个列表。