---
title: 在Windows下使用Anaconda安装TesnsorFlow 2.x
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-19 13:13:50
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_10_python_artificial_intelligence.png
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_10_python_artificial_intelligence.png
tags: 
    - 人工智能
    - Anaconda
    - conda
    - TensorFlow
categories: 
keywords:
description: Anaconda是一个开源的工具，目前拥有超过六百万的用户。Anaconda致力于提供最便捷的方式来使用Python进行数据科学计算和机器学习。目前，Anaconda拥有超过250+的数据科学工具包，conda工具包可用于Windows，MacOS和Linux三种平台的虚拟环境管理系统。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### 下载 Anaconda 

首先打开[Anaconda官网](https://www.anaconda.com/products/individual#Downloads)找到网页底部，由于最新的Anaconda支持Python3.8版本，而TesnorFlow最高支持到Python3.7，我特意查了一下Python3.8发布的时间点，所以我们需要点击页面的`achrive`去找历史版本下载。
![2020_12_19_conda_0](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_12_19_conda_0.png)
点击后进入到Anaconda的历史版本页面，我们直接搜索2020-10-15，找到`Anaconda2-2019.10-Windows-x86_64.exe`进行下载即可。

![2020_12_19_conda_1](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_12_19_conda_1.png)

### 安装 Anaconda
下载完成后，我们直接双击安装文件开始安装即可，中间过程一路点击`Next`
即可。
![2020_12_19_conda_2](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_12_19_conda_2.png)


### 设置国内镜像源
由于网络问题，我这里需要添加国内的清华镜像源，这样会方便我们更快速的下载资源。  

安装完成后，我们点击`Windows`按钮，会看到有一个有`Anaconda3(64-bit)`的文件夹，这就是我们安装好`Anaconda`，然后我们点击`Anaconda Powershell Prompt`命令行工具。  
![2020_12_19_conda_3](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_12_19_conda_3.png)

进入到命令行工具之后，输入
``` bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
# 设置搜索时显示通道地址
conda config --set show_channel_urls yes
```
就可以了。
更多的`conda`使用方法，可以查看我的[上一篇博客的后半部分](http://fulade.me/tensorflow-mac-install-anaconda-01.html#conda%E5%B8%B8%E7%94%A8%E5%91%BD%E4%BB%A4)

可以使用命令`conda config --show`，在`channels`字段这里显示已经添加的源


### 开始安装TensorFlow
我们只需要在上一步中打开的命令行工具中输入
``` bash
conda install tensorflow
```
就可以了。
由于我们已经配置了国内的镜像源，很快就可以安装完成。

### 测试
安装完成后，我们接着在打开的命令行工具中输入
``` python 
import tensorflow as tf
tf.__version__
```
看到有输出`2.1.0`就说明我们的安装是正确的。
**注意**由于TensorFlow也在不停的升级中，这里输出的不一定非要是`2.1.0`输出`2.x`就是争取的。
![2020_12_19_conda_5](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2020_12_19_conda_5.png)


***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)