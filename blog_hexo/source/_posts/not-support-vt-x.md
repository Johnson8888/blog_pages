---
title: 【Flutter 1-3】在VMWare Windows 10 虚拟机下Android Studio 安装模拟器报错 Your CPU does not support VT-x
date: 2020-10-08 22:04:04
tags:
    - Flutter
---

[文章首发地址](http://fulade.me/2020/10/08/not-support-vt-x/)
#### 出现这个问题的原因
Android模拟器需要计算器的处理器必须支持以下虚拟化扩展技术之一：

- Intel 虚拟化技术（VT、VT-x 和 vmx）扩展
- AMD 虚拟化（AMD-V 和 SVM）扩展

大部分处理器都会支持，这里就以Intel处理器为例。

#### 在BOIS内开启
如果之前没有开启过虚拟化，需要我们进入到BIOS开启，各个主板进入BIOS的方式不同，这里就不一一列举了。

#### 编辑VMWare 虚拟机配置
打开`VMware Workstation Pro`，找到要编辑的虚拟机，依次点击`编辑虚拟机`->`处理器`->`虚拟化 Intel VT-x/EPT 或 AMD V/RVI(V)`
![2020_10_08_vt-x](https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/2020_10_08_vt-x.png)
编辑后保持一下，重启虚拟机就可以了。

#### HAXM is not installed
接下来在安装模拟器的时候还有可能会遇到`HAXM is not installed`错误
这里就直接点击下面的 `Install Haxm`就可以了！

