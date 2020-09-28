---
title: Mac下使用GitHub+Hexo搭建个人博客
date: 2020-09-26 14:09:54
tags:
   -Github
---


开始之前需要在电脑上安装好[Git](https://git-scm.com/)和[node.js](https://nodejs.org/en/)，Mac上可以使用Homebrew命令行工具来安装Git和node.js

##### 安装Homebrew
在命令行工具输入以下命令，如果已经安装过Homebrew可以忽略
``` bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

##### Homebrew 安装 node.js
``` bash
brew install node
```
安装后可以使用命令来检查是否安装成功
检查node
``` bash
node -v
```
输出结果：
``` bash
v12.14.1
```
检查[npm](https://www.npmjs.com/)是否安装成功，npm是node.js的包管理工具，用它来安装hexo
``` bash
nmp -v
```
输出结果:
``` bash
6.13.4
```
##### Homebrew 安装git
``` bash
brew install git
```
检查git是否安装成功
``` bash
git -v
``` 
输出结果:
``` bash
git version 2.24.3 (Apple Git-128)
```
##### 使用npm安装[hexo](https://hexo.io/zh-cn/docs/)
``` bash
sudo npm install -g hexo-cli
``` 
安装完成后，在Desktop创建一个blog文件夹，在该文件夹下初始化我们的博客
``` bash
cd ~/Desktop && mkdir blog && cd blog
``` 
在该文件件目录下执行博客初始化操作
``` bash
# 会下载一些node.js需要的依赖文件
hexo init
```
初始化成功后，在blog目录下执行预览操作
``` bash
hexo s 
``` 
当看到如下输出就可以预览我们创建的博客了
```
INFO  Validating config
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop. 
```
预览效果如下

![preview_hexo_20200928](https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/preview_hexo_20200928.jpg?token=ABHYKCYWPSQBYH2VQQDDCHC7OFJ2G)

