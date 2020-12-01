---
title: 一台电脑2个或多个Git账号如何配置和管理
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-10-29 19:40:51
tags:
    - Git
keywords: 'Git多账号,Git2个账号,管理Git'
description:
photos:
fileName:
type:
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_git.jpg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_git.jpg
---

#### **引言**
由于我在公司的Git源码服务器有一套账号和密码，我个人的Github又有一套账号和密码，这两个账号都需要PUSH和PULL代码，如果对Git使用的不太熟练，经常会遇到`git@github.com: Permission denied (publickey)`这种错误，那么我们该如何同时管理多个Git账号呢？
<!--more-->
这里我们以MacOS系统为例。
##### **同一台电脑两个Git账号且账号相同**
这里所说的账号相同，指的是：邮箱相同。比如我在公司Gitlab用的账号和Github的账号就是同一个邮箱，这种情况比较好处理，Gitlab和Github在校验的时候是只认邮箱的。只要我们把秘钥，也就是 `id_ras.pub`里面的内容在Gitlab和Github上都配置好就可以了。也就说多个Git源码服务器且都是使用同一个邮箱的情况下，我们只要把`id_ras.pub`配置到多个源码服务器就OK了！

##### **同一台电脑多个账号且账号不同**
这个时候就需要我们指明哪个账号使用哪一个`.pub`文件了。我们需要在`~/.ssh`文件夹下创建名为`config`的文件，如果已经存在了该文件则需要修改一下。  
`config`的内容参考以下写法:
``` bash

# 第一个账号为 
# Email:fulade1@gmail.com  
# User:fulade1

host gitlab.ttal.com
    hostname gitlab.ttal.com
    Port 65095
    User fulade1
    IdentityFile /home/Fulade/.ssh/id_rsa

# 第二个账号为 
# Email:fulade2@gmail.com  
# User:fulade2

host gitlab-test.ttal.com
    hostname gitlab.ttal.com
    Port 65095
    User fulade2
    IdentityFile /home/Fulade/.ssh/id_rsa_second

# 第三个账号 
# Email:fulade2@gmail.com  
# User:fulade2

host github.com
    hostname github.com
    Port 22
    User fulade2
    IdentityFile /home/Fulade/.ssh/id_rsa_second


# 其中第二个账号跟第三个账号相同，只是源码服务器不同。
```
因为配置了多个邮箱账号，所有git的global配置就要删除了。
``` bash
# 取消全局配置
git config --global --unset user.name
git config --global --unset user.email
```
然后在每个Repo下配置账号就可以了
``` bash
# 每个项目Repo设置自己的user.email
git config  user.email "xxxx@xx.com"
git config  user.name "fulade"
```
这样就可以了。

##### **补充**
指定`.pub`文件路径的方法：  
需要使用命令`ssh-keygen -t rsa -C "fulade@gmail.com"`，接下来输入路径就可以了
``` bash
ssh-keygen -t rsa -C "fulade@gmail.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/Fulade/.ssh/id_rsa):/Users/Fulade/.ssh/id_rsa_second
```
其中`/Users/Fulade/.ssh/id_rsa_second`是要输入的部分。
Have Fun !
***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)