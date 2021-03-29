---
title: 起名字老重名？使用这款利器可以快速帮你查询有哪些站点用了你的名字！
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-03-29 17:10:30
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_03_29_sherlock_tag.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_03_29_sherlock_tag.jpeg
tags: 
    - Tips
categories: Tips
keywords: sherlock
description:
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

![2021_03_29_sherlock_demo](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2021_03_29_sherlock_demo.gif)

不知道有没有小伙伴跟我一样，常常在注册账号的时候输入了昵称都会反馈一个“用户名已存在”，然后尝试了好几个之后才可以成功。  
今天介绍的这款工具可以帮助我们迅速的检索各大网站有没有我们自己的用户昵称，同样它也可以帮助我们快速的查询同一个用户名昵称都注册了哪些网站。

#### 简介
[sherloc](https://github.com/sherlock-project/sherlock)，在Github上面已经有23.7k的Star数。它的名字取自于《神探夏洛克》的英文名字——sherlock。
sherlock主要使用Python3来开发完成的，这使它具有更多的灵活性，可以运行在Windows、Mac以及Linux上面。

#### 安装步骤 
我们这里以Linux为例
``` bash
# 从Github上面下载源码
$ git clone https://github.com/sherlock-project/sherlock.git

# 进入到源码文件夹内
$ cd sherlock

# 安装所需要的依赖
$ python3 -m pip install -r requirements.txt
```
得益于Python良好的包管理工具，使得我们的安装非常的简单和方便，只需要几个命令就可搞定。

#### 使用方法
``` bash
$ python3 sherlock --help
usage: sherlock [-h] [--version] [--verbose] [--folderoutput FOLDEROUTPUT]
                [--output OUTPUT] [--tor] [--unique-tor] [--csv]
                [--site SITE_NAME] [--proxy PROXY_URL] [--json JSON_FILE]
                [--timeout TIMEOUT] [--print-all] [--print-found] [--no-color]
                [--browse] [--local]
                USERNAMES [USERNAMES ...]

Sherlock: Find Usernames Across Social Networks (Version 0.14.0)

optional arguments:
  -h, --help           #展示帮助页面
  --version            # 输出当前的版本号以及项目的依赖
  --verbose, -v, -d, --debug # Log的输出等级
  --folderoutput FOLDEROUTPUT, -fo FOLDEROUTPUT #如果需要同时查询多个用户名，可以在这里定义传入保持结果的文件夹路径
  --output OUTPUT, -o OUTPUT  # 当只查询一个名字的时候，指定的保持结果的文件夹
  --tor, -t             # 通过Tor来发送请求，Tor必须安装在系统目录里面
  --unique-tor, -u      # 通过Tor来发送请求，并且每次都使用新的连接
  --csv                 # 创建CVS文件
  --site SITE_NAME      # 要查询的网站名字，可以传入多个
  --proxy PROXY_URL, -p PROXY_URL # 使用的代理
  --json JSON_FILE, -j JSON_FILE # 输入格式为json文件，支持从网络获取的json文件
  --timeout TIMEOUT     # 超时时间
  --print-all           # 输出所有结果 包括没有找到昵称的网站
  --print-found         # 只输出找到结果的信息
  --no-color            # 控制台不带有颜色的输出结果
  --browse, -b          # 使用默认浏览器打开所有的搜索结果
  --local, -l           # 强制使用本地的 data.json文件
```
使用方法也很简单
搜索单个名字
`python3 sherlock user123`
比如我们搜索`川建国`
搜索结果如下：

同时搜索多个名字
`python3 sherlock tony johnson heisenberg`


***  
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)