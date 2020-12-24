---
title: 【Python 1-16】Python手把手教程之——类Class的继承、父类、子类
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-23 19:41:48
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_python.jpg
tags:
    - Python 类
    - Python Class
    - Python 继承
    - Python 父类
    - Python 子类
categories: Python 
keywords: 'Python 类，Python Class，Python面向对象'
description: 编写类时，并非总是要从空白开始。如果你要编写的类是另一个现成类的特殊版本，可使用 继承。一个类继承另一个类时，它将自动获得另一个类的所有属性和方法;原有的类称为父类， 而新类称为子类。子类继承了其父类的所有属性和方法，同时还可以定义自己的属性和方法。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### 继承
编写类时，并非总是要从空白开始。如果你要编写的类是另一个现成类的特殊版本，可使用 继承。一个类继承另一个类时，它将自动获得另一个类的所有属性和方法;原有的类称为父类， 而新类称为子类。子类继承了其父类的所有属性和方法，同时还可以定义自己的属性和方法。

#### 子类的方法__init__()
创建子类的实例时，Python首先需要完成的任务是给父类的所有属性赋值。为此，子类的方法`__init__()`需要继承父类的方法。
例如，下面来模拟电动汽车。电动汽车是一种特殊的汽车，因此我们可以在前面创建的Car类的基础上创建新类`ElectricCar`，这样我们就只需为电动汽车特有的属性和行为编写代码。
下面来创建一个简单的`ElectricCar`类版本，它具备Car类的所有功能:
``` py
class Car(): 
    """一次模拟汽车的简单尝试"""
    def __init__(self, make, model, year): 
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0
    def get_descriptive_name(self):
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model 
        return long_name.title()

    def read_odometer(self):
        print("This car has " + str(self.odometer_reading) + " miles on it.")

    def update_odometer(self, mileage):
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage 
        else:
            print("You can't roll back an odometer!")

    def increment_odometer(self, miles): 
        self.odometer_reading += miles


class ElectricCar(Car): 
    """电动汽车的独特之处"""
    def __init__(self, make, model, year): 
        """初始化父类的属性"""
        super().__init__(make, model, year) 
        
my_tesla = ElectricCar('tesla', 'model s', 2016)
print(my_tesla.get_descriptive_name())
```
首先是Car类的代码。创建子类时，父类必须包含在当前文件中，且位于子类前面。接着我们定义了子类`ElectricCar`。定义子类时，必须在括号内指定父类的名称。方法`__init__()` 接受创建Car实例所需的信息。

`ElectricCar`内部的`super()`是一个特殊函数，帮助Python将父类和子类关联起来。这行代码让Python调用`ElectricCar`的父类的方法`__init__()`，让`ElectricCar`实例包含父类的所有属性。父类也称为超类(`superclass`)，名称super因此而得名。

接下来我们测试一下继承的作用，我们尝试创建一辆电动汽车，但提供的信息与创建普通汽车时相同。我们创建`ElectricCar`类的一个实例，并将其存储在变量`my_tesla`中。这行代码调用`ElectricCar`类中定义的方法`__init__()`，后者让Python调用父类Car中定义的方法 `__init__()`。我们提供了实参'tesla'、'model s'和2016。
除方法`__init__()`外，电动汽车没有其他特有的属性和方法。当前，我们只想确认电动汽车具备普通汽车的行为，输出结果如下:
``` py
2016 Tesla Model S
```
ElectricCar实例的行为与Car实例一样，现在可以开始定义电动汽车特有的属性和方法了。

#### 给子类定义属性和方法
让一个类继承另一个类后，可添加区分子类和父类所需的新属性和方法。
下面来添加一个电动汽车特有的属性(电瓶)，以及一个描述该属性的方法。我们将存储电瓶容量，并编写一个打印电瓶描述的方法:
``` py
class ElectricCar(Car):
    def __init__(self, make, model, year):
        """电动汽车的独特之处 初始化父类的属性，再初始化电动汽车特有的属性 """
        super().__init__(make, model, year) 
        self.battery_size = 70
    def describe_battery(self): 
        """打印一条描述电瓶容量的消息"""
        print("This car has a " + str(self.battery_size) + "-kWh battery.")

my_tesla = ElectricCar('tesla', 'model s', 2016) 
print(my_tesla.get_descriptive_name()) 
my_tesla.describe_battery()
```
我们添加了新属性`self.battery_size`，并设置其初始值。根据`ElectricCar`类创建的所有实例都将包含这个属性，但所有Car实例都不包含它。我们还添加了一个名为`describe_battery()`的方法，它打印有关电瓶的信息。我们调用这个方法时，将看到一条电动汽车特有的描述:
``` bash
2016 Tesla Model S
This car has a 70-kWh battery.
```
对于ElectricCar类的特殊化程度没有任何限制。模拟电动汽车时，你可以根据所需的准确程度添加任意数量的属性和方法。如果一个属性或方法是任何汽车都有的，而不是电动汽车特有的，就应将其加入到Car类而不是ElectricCar类中。这样，使用Car类的人将获得相应的功能，而 ElectricCar类只包含处理电动汽车特有属性和行为的代码。
#### 重写父类的方法
对于父类的方法，只要它不符合子类模拟的实物的行为，都可对其进行重写。为此，可在子类中定义一个这样的方法，即它与要重写的父类方法同名。这样，Python将不会考虑这个父类方法，而只关注你在子类中定义的相应方法。
假设`Car`类有一个名为`fill_gas_tank()`的方法，它对全电动汽车来说毫无意义，因此你可能想重写它。下面演示了一种重写方式:
``` py
def ElectricCar(Car):
    def fill_gas_tank():
        """电动汽车没有油箱"""
        print("This car doesn't need a gas tank!")
```
现在，如果有人对电动汽车调用方法`fill_gas_tank()`，Python将忽略Car类中的方法`fill_gas_tank()`，转而运行上述代码。使用继承时，可让子类保留从父类那里继承的有用的代码，用重写来覆盖不需要的代码。





> 本篇文章没有作业，下一篇我们讲解函数的高级用法


***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)
