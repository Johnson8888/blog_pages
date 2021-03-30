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

不知道有没有小伙伴跟我一样，常常在注册账号的时候输入了昵称往往会反回一个“用户名已存在”，然后尝试了好几个昵称之后才能成功。  
今天介绍的这款工具可以帮助我们迅速的检索各大网站有没有我们自己的用户昵称，同样它也可以帮助我们快速的查询同一个用户名都注册了哪些网站。

#### 简介
[sherloc](https://github.com/sherlock-project/sherlock)，在Github上面已经有24k的Star数，它的名字取自于电影《神探夏洛克》的英文名字——sherlock。
sherlock主要使用Python3来开发完成的，这使得它具有更多的灵活性，可以运行在Windows、Mac以及Linux操作系统上。

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
  --folderoutput FOLDEROUTPUT, -fo FOLDEROUTPUT #如果需要同时查询多个用户名，可以在这里定义传入保存结果的文件夹路径
  --output OUTPUT, -o OUTPUT  # 当只查询一个名字的时候，指定的保村结果的文件夹
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
使用方法也很简单，搜索单个名字，只需要在命令行输入：
`python3 sherlock username`
比如我们搜索`川建国`
搜索结果如下：
![2021_03_29_sherlock_search](https://cdn.jsdelivr.net/gh/Johnson8888/blog_pages/images/2021_03_29_sherlock_search.png)

同时搜索多个名字
`python3 sherlock tony heisenberg johnson`
搜索结果如下：
``` 
[*] Checking username tony on:
[+] 3dnews: http://forum.3dnews.ru/member.php?username=tony
[+] 7Cups: https://www.7cups.com/@tony
[+] 9GAG: https://www.9gag.com/u/tony
[+] About.me: https://about.me/tony
[+] Academia.edu: https://independent.academia.edu/tony
[+] AllTrails: https://www.alltrails.com/members/tony
....
[+] Anobii: https://www.anobii.com/tony/profile
[+] Apple Discussions: https://discussions.apple.com/profile/tony
[+] Archive.org: https://archive.org/details/@tony
[+] Asciinema: https://asciinema.org/~tony
[+] AskFM: https://ask.fm/tony

[*] Checking username heisenberg on:
[+] 9GAG: https://www.9gag.com/u/heisenberg
[+] About.me: https://about.me/heisenberg
[+] Academia.edu: https://independent.academia.edu/heisenberg
[+] AllTrails: https://www.alltrails.com/members/heisenberg
[+] Anobii: https://www.anobii.com/heisenberg/profile
[+] Archive.org: https://archive.org/details/@heisenberg
...
[+] Asciinema: https://asciinema.org/~heisenberg
[+] AskFM: https://ask.fm/heisenberg
[+] Audiojungle: https://audiojungle.net/user/heisenberg
[+] BLIP.fm: https://blip.fm/heisenberg
[+] BOOTH: https://heisenberg.booth.pm/

[*] Checking username johnson on:
[+] 7Cups: https://www.7cups.com/@johnson
[+] 9GAG: https://www.9gag.com/u/johnson
[+] About.me: https://about.me/johnson
[+] Academia.edu: https://independent.academia.edu/johnson
[+] AllTrails: https://www.alltrails.com/members/johnson
...
[+] Anobii: https://www.anobii.com/johnson/profile
[+] Archive.org: https://archive.org/details/@johnson
[+] Audiojungle: https://audiojungle.net/user/johnson
[+] BLIP.fm: https://blip.fm/johnson
[+] Bandcamp: https://www.bandcamp.com/johnson
```
多个搜索结果会按顺序来展示

#### 支持Docker
作者也增加了对docker的支持，我们只需要执行`docker build -t mysherlock-image .`就可以在docker中使用sherklock了。
更多有关docker的使用方法可以去[github主页](https://github.com/sherlock-project/sherlock)查看

#### 实现原理
作者是把每一个用户的URL地址都去请求一下，如果有返回有结果就代表存在这个昵称，如果没有返回结果或者是404，就意味着不存在当前的用户。
比如请求：`https://www.about.me/tony`,可以请求到结果就代表存在这个昵称，如果没有相应的返回就是没有这个昵称。


***  
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)