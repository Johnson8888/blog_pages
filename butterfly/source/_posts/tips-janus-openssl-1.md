---
title: Jauns-gateway 报错【No package 'libssl' found No package 'libcrypto' found】
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-03 12:12:40
cover:
thumbnail:
tags: 
    - Tips
categories: Tips
keywords: janus-gateway,janus-gateway libssl error
description:
photos:
fileName:
type:
---

> No package 'libssl' found
No package 'libcrypto' found
<!--more-->
[文章首发地址](http://fulade.me/tips-janus-openssl-1.html)

在Mac下配置janus-gateway服务器的时候遇到了找不到`libssl`和`libcrypto`错误，
详情如下：
```
./configure
...
checking for
                    glib-2.0 >= 2.34
					libconfig
                    nice
                    jansson >= 2.5
                    libssl >= 1.0.1
                    libcrypto
                    zlib
                  ... no
configure: error: Package requirements (
                    glib-2.0 >= 2.34
					libconfig
                    nice
                    jansson >= 2.5
                    libssl >= 1.0.1
                    libcrypto
                    zlib
                  ) were not met:

No package 'libssl' found
No package 'libcrypto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix
```
只需要自定义`PKG_CONFIG_PATH`即可
在执行  
```
./configure --prefix=/usr/local/janus PKG_CONFIG_PATH=/usr/local/opt/openssl/lib/pkgconfig
```
之前在命令行内执行一下
```
export PKG_CONFIG_PATH=/usr/local/opt/openssl/lib/pkgconfig:/usr/local/opt/libffi/lib/pkgconfig
 ```
如果没有安装`libffi`,可以使用 `Home brew`安装一下就可以了。
