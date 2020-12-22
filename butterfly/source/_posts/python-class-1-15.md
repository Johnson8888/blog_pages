---
title: 【Python 1-15】Python手把手教程之——详解类Class以及类的使用
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-22 15:48:56
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
tags:
    - Python 类
    - Python Class
categories: Python 
keywords: 'Python 类，Python Class，Python面向对象'
description: 类（Class）是面向对象程序设计（OOP，Object-Oriented Programming）实现信息封装的基础。类是一种用户定义的引用数据类型，也称类类型。每个类包含数据说明和一组操作数据或传递消息的函数。类的实例称为对象。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)
### 创建和使用类
使用类几乎可以模拟任何东西。下面来编写一个表示小狗的简单类Dog——它表示的不是特定的小狗，而是任何小狗。对于大多数宠物狗，我们都知道些什么呢?它们都有名字和年龄，我们还知道，大多数小狗还会蹲下和打滚。由于大多数小狗都具备上述两项信息(名字和年龄)和两种行为(蹲下和打滚)，我们的Dog类将包含它们。这个类让Python知道如何创建表示小狗的对象。编写这个类后，我们将使用它来创建表示特定小狗的实例。
#### 创建Dog类
根据Dog类创建的每个实例都将存储名字和年龄。我们赋予了每条小狗蹲下(`sit()`)和打滚(`roll_over()`)的能力:
``` py
class Dog():
    """一次模拟小狗的简单尝试"""
    def __init__(self, name, age):
        """初始化属性name和age"""
        self.name = name
        self.age = age
    def sit(self):
        """模拟小狗被命令时蹲下""" 
        print(self.name.title() + " is now sitting.")
    def roll_over(self): 
        """模拟小狗被命令时打滚""" 
        print(self.name.title() + " rolled over!")
```
首先我们定义了一个名为Dog的类。根据约定，在Python中，首字母大写的名称指的是类。 这个类定义中的括号是空的，因为我们要从空白创建这个类。
然后，我们编写了一个文档字符串，对这个类的功能作了描述。
##### 方法__init__() 
类中的函数称为方法，我们来第一个，`方法__init__()`是一个特殊的方法，每当你根据Dog类创建新实例时，Python都会自动运行它。在这个方法的名称中，开头和末尾各有两个下划线，这是一种**约定**，旨在避免Python默认方法与普通方法发生名称冲突。  

我们将方法`__init__()`定义成了包含三个形参:`self`、`name`和`age`。在这个方法的定义中，形参self必不可少，还必须位于其他形参的前面。因为 Python调用这个`__init__()`方法来创建Dog实例时，将自动传入实参self。每个与类相关联的方法调用都自动传递实参self，它是一个指向实例本身的引用，让实例能够访问类中的属性和方法。我们创建Dog实例时，Python将调用Dog类的方法`__init__()`。我们将通过实参向`Dog()`传递名字和年龄。self会自动传递，因此我们不需要传递它。每当我们根据Dog类创建实例时，都只需给最后两个形参(`name`和`age`)提供值。


`__init__()`内的两个变量都有前缀self。以self为前缀的变量都可供类中的所有方法使用，我们还可以通过类的任何实例来访问这些变量。`self.name = name`获取存储在形参`name`中的值，并将其存储到变量`name`中，然后该变量被关联到当前创建的实例。`self.age = age`的作用与此类似。像这样可通过实例访问的变量称为**属性**。   

Dog类还定义了另外两个方法:`sit()`和`roll_over()`。由于这些方法不需要额外的信
息，如名字或年龄，因此它们只有一个形参`self`。我们后面将创建的实例能够访问这些方法，换句话说，它们都会蹲下和打滚。当前，`sit()`和`roll_over()`所做的有限，它们只是打印一条消息，指出小狗正蹲下或打滚。但可以扩展这些方法以模拟实际情况:如果这个类包含在一个计算机游戏中，这些方法将包含创建小狗蹲下和打滚动画效果的代码。如果这个类是用于控制机器狗的，这些方法将引导机器狗做出蹲下和打滚的动作。
#### 由类生成实例
可将类视为有关如何创建实例的说明。Dog类是一系列说明，让Python知道如何创建表示特定小狗的实例。
下面来创建一个表示特定小狗的实例:
``` py
my_dog = Dog('willie', 6)
print("My dog's name is " + my_dog.name.title() + ".")
print("My dog is " + str(my_dog.age) + " years old.")
```
这里使用的是前一个示例中编写的Dog类。我们让Python创建一条名字为'willie'、 年龄为6的小狗。遇到这行代码时，Python使用实参'willie'和6调用Dog类中的方法`__init__()`。 方法`__init__()`创建一个表示特定小狗的示例，并使用我们提供的值来设置属性`name`和`age`。方法`__init__()`并未显式地包含`return`语句，但Python自动返回一个表示这条小狗的实例。我们将这个实例存储在变量`my_dog`中。在这里，命名约定很有用，我们通常可以认为首字母大写的名称(如 Dog)指的是类，而小写的名称(如my_dog)指的是根据类创建的实例。

##### 1. 访问属性
要访问实例的属性，可使用句点表示法。我们编写了如下代码来访问`my_dog`的属性name的值:
``` py
my_dog.name
```
句点表示法在Python中很常用，这种语法演示了Python如何获悉属性的值。在这里，Python先找到实例`my_dog`，再查找与这个实例相关联的属性`name`。在Dog类中引用这个属性时，使用的是`self.name`。然后我们使用同样的方法来获取属性age的值。
输出如下：
``` py
My dog's name is Willie.
My dog is 6 years old.
```  
##### 2. 调用方法
根据Dog类创建实例后，就可以使用句点表示法来调用Dog类中定义的任何方法。下面来让小狗蹲下和打滚:
``` py
my_dog = Dog('willie', 6)
my_dog.sit()
my_dog.roll_over()
```
要调用方法，可指定实例的名称(这里是my_dog)和要调用的方法，并用句点分隔它们。执行代码my_dog.sit()时，Python在类Dog中查找方法`sit()`并运行其代码。Python以同样的方式解读代码`my_dog.roll_over()`。  
这种语法很有用。如果给属性和方法指定了合适的描述性名称，如`name`、`age`、`sit()`和`roll_over()`，即便是从未见过的代码块，我们也能够轻松地推断出它是做什么的。
##### 3. 创建多个实例
可按需求根据类创建任意数量的实例。下面再创建一个名为`your_dog`的实例:
``` py
my_dog = Dog('willie', 6)
your_dog = Dog('lucy', 3)
print("My dog's name is " + my_dog.name.title() + ".")
print("My dog is " + str(my_dog.age) + " years old.")
my_dog.sit()
print("\nYour dog's name is " + your_dog.name.title() + ".") 
print("Your dog is " + str(your_dog.age) + " years old.") 
your_dog.sit()
```
在这个实例中，我们创建了两条小狗，它们分别名为Willie和Lucy。每条小狗都是一个独立的实例，有自己的一组属性，能够执行相同的操作:
``` py
My dog's name is Willie. 
My dog is 6 years old. 
Willie is now sitting.
Your dog's name is Lucy. 
Your dog is 3 years old. 
Lucy is now sitting.
```
就算我们给第二条小狗指定同样的名字和年龄，Python依然会根据Dog类创建另一个实例。 你可按需求根据一个类创建任意数量的实例，条件是将每个实例都存储在不同的变量中，或占用 列表或字典的不同位置。

### 使用类和实例
你可以使用类来模拟现实世界中的很多情景。类编写好后，你的大部分时间都将花在使用根据类创建的实例上。你需要执行的一个重要任务是修改实例的属性。你可以直接修改实例的属性，也可以编写方法以特定的方式进行修改。
#### Car类
下面来编写一个表示汽车的类，它存储了有关汽车的信息，还有一个汇总这些信息的方法:
``` py
class Car():
    """一次模拟汽车的简单尝试"""
    def __init__(self, make, model, year): 
    """初始化描述汽车的属性"""
        self.make = make 
        self.model = model 
        self.year = year
    def get_descriptive_name(self):
        """返回整洁的描述性信息"""
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model
        return long_name.title()
my_new_car = Car('audi', 'a4', 2016)
print(my_new_car.get_descriptive_name())
```
我们定义了方法`__init__()`。与前面的Dog类中一样，这个方法的第一个形参为self，我们还在这个方法中包含了另外三个形参:`make`、`model`和`year`。方法`__init__()`接受这些形参的值，并将它们存储在根据这个类创建的实例的属性中。创建新的Car实例时，我们需要指定其制造商、型号和生产年份。

然后我们又定义了一个名为`get_descriptive_name()`的方法，它使用属性`year`、`make`和`model`创建一个对汽车进行描述的字符串，让我们无需分别打印每个属性的值。为在这个方法中访问属性的值，我们使用了`self.make`、`self.model`和`self.year`。我们根据Car类创建了一个实例，并将其存储到变量`my_new_car`中。接下来，我们调用方法`get_descriptive_name()`，指出我们拥有的是一辆什么样的汽车:
``` py
2016 Audi A4
```
#### 给属性指定默认值
类中的每个属性都必须有初始值，哪怕这个值是0或空字符串。在有些情况下，如设置默认值时，在方法`__init__()`内指定这种初始值是可行的，如果你对某个属性这样做了，就无需包含为它提供初始值的形参。  
下面来添加一个名为`odometer_reading`的属性，其初始值总是为0。我们还添加了一个名为
`read_odometer()`的方法，用于读取汽车的里程表:
``` py
class Car():
    def __init__(self, make, model, year): 
        """初始化描述汽车的属性""" 
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0
    def get_descriptive_name(self):
        """返回整洁的描述性信息"""
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model
        return long_name.title()

    def read_odometer(self): 
        """打印一条指出汽车里程的消息"""
        print("This car has " + str(self.odometer_reading) + " miles on it.")

my_new_car = Car('audi', 'a4', 2016) 
print(my_new_car.get_descriptive_name()) 
my_new_car.read_odometer()
```
现在，当Python调用方法`__init__()`来创建新实例时，将像前一个示例一样以属性的方式存储制造商、型号和生产年份。接下来，Python将创建一个名为`odometer_reading`的属性，并将其初始值设置为0。我们还定义了一个名为`read_odometer()`的方法，它让你能够轻松地获悉汽车的里程。
一开始汽车的里程为0: 
``` py
2016 Audi A4
This car has 0 miles on it.
```
出售时里程表读数为0的汽车并不多，因此我们需要一个修改该属性的值的途径。

#### 修改属性的值
可以以三种不同的方式修改属性的值:直接通过实例进行修改;通过方法进行设置;通过方 法进行递增(增加特定的值)。下面依次介绍这些方法。
**1. 直接修改属性的值**
要修改属性的值，最简单的方式是通过实例直接访问它。下面的代码直接将里程表读数设置为23:
``` py
my_new_car = Car('audi', 'a4', 2016) 
print(my_new_car.get_descriptive_name())
my_new_car.odometer_reading = 23 
my_new_car.read_odometer()
```
我们使用句点表示法来直接访问并设置汽车的属性`odometer_reading`。这行代码让 Python在实例`my_new_car`中找到属性`odometer_reading`，并将该属性的值设置为23:
``` py
2016 Audi A4
This car has 23 miles on it.
```
有时候需要像这样直接访问属性，但其他时候需要编写对属性进行更新的方法。
##### 2. 通过方法修改属性的值
如果有替你更新属性的方法，将大有裨益。这样，你就无需直接访问属性，而可将值传递给一个方法，由它在内部进行更新。下面的示例演示了一个名为`update_odometer()`的方法:
``` py
class Car():
    #### 前面的代码省略
    def update_odometer(self, mileage): 
        """将里程表读数设置为指定的值"""
        self.odometer_reading = mileage

my_new_car = Car('audi', 'a4', 2016) 
print(my_new_car.get_descriptive_name())
my_new_car.update_odometer(23) 
my_new_car.read_odometer()
```
对Car类所做的唯一修改是，添加了方法`update_odometer()`。这个方法接受一个里程值，并将其存储到`self.odometer_reading`中。然后我们调用了`update_odometer()`，并向它提供了实参23(该实参对应于方法定义中的形参`mileage`)。它将里程表读数设置为23;而方法`read_odometer()`打印该读数:
``` py
2016 Audi A4
This car has 23 miles on it.
```
可对方法`update_odometer()`进行扩展，使其在修改里程表读数时做些额外的工作。下面来添加一些逻辑，禁止任何人将里程表读数往回调:
``` py
class Car():
    #### 前面的代码省略
    def update_odometer(self, mileage): 
        """将里程表读数设置为指定的值 禁止将里程表读数往回调"""
        if mileage >= self.odometer_reading: 
            self.odometer_reading = mileage
        else:
            print("You can't roll back an odometer!")
```
现在，`update_odometer()`在修改属性前检查指定的读数是否合理。如果新指定的里程 (`mileage`)大于或等于原来的里程(`self.odometer_reading`)，就将里程表读数改为新指定的里程，否则就发出警告，指出不能将里程表往回拨。
##### 3. 通过方法对属性的值进行递增
有时候需要将属性值递增特定的量，而不是将其设置为全新的值。假设我们购买了一辆二手
车，且从购买到登记期间增加了100英里的里程，下面的方法让我们能够传递这个增量，并相应地增加里程表读数:
``` py
class Car():        
    def increment_odometer(self, miles): 
        """将里程表读数增加指定的量""" 
        self.odometer_reading += miles

my_used_car = Car('subaru', 'outback', 2013) 
print(my_used_car.get_descriptive_name())
my_used_car.update_odometer(23500) 
my_used_car.read_odometer()
my_used_car.increment_odometer(100) 
my_used_car.read_odometer()
```
新增的方法`increment_odometer()`接受一个单位为英里的数字，并将其加入到`self.odometer_reading`中。然后我们创建了一辆二手车——`my_used_car`。我们调用方法`update_odometer()`并传入23500，将这辆二手车的里程表读数设置为23500。然后我们调用`increment_odometer()`并传入100，以增加从购买到登记期间行驶的100英里:
``` py
2013 Subaru Outback
This car has 23500 miles on it. 
This car has 23600 miles on it.
```
你可以轻松地修改这个方法，以禁止增量为负值，从而防止有人利用它来回拨里程表。


>  小作业
15-1 用户:创建一个名为 User 的类，其中包含属性 first_name 和 last_name，还有 用户简介通常会存储的其他几个属性。在类 User 中定义一个名为 describe_user()的方 法，它打印用户信息摘要，创建多个表示不同用户的实例，并对每个实例都调用上述两个方法。
15-2 在为完成练习 15-1 而编写的User类中，添加一个名为login_attempts的属性。编写一个名为increment_login_attempts()的方法，它将属性login_attempts 的值加 1。再编写一个名为 reset_login_attempts()的方法，它将属性login_attempts 的值重置为0。
根据User类创建一个实例，再调用方法increment_login_attempts()多次。打印属性login_attempts的值，确认它被正确地递增;然后，调用方法 reset_login_attempts()，并再次打印属性 login_attempts 的值，确认它被重置为0。