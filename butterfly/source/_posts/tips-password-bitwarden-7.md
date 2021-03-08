---
title: LastPass即将收费，是时候更换一款新的密码管理工具了！
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-02-23 16:31:37
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_02_23_tips_lastpass.jpeg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_02_23_tips_lastpass.jpeg
tags:   
    - Tips
categories: Tips
keywords: LastPass收费，1Password，Bitwarden，密码管理工具
description: 提到2021年3月16日起，登录账号所在的平台将决定账号的走向，一方是电脑和笔记本端，一方是手机和平板端，全平台免费服务变成二选一（选了一方就不能使用另外一方了）。 
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

前几天收到了`LastPass`的邮件：自2021年3月16日起，不再提供全平台的免费服务，用户只能选择一个平台享受免费(iOS、Android 或者 PC端)

邮件里还提到，购买会员享受25%折扣，打完折27美元。
![2021_02_23_lastpass_details](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_02_23_lastpass_details.png)
感谢`LastPass`这些年来的陪伴，不管是在移动端还是PC网页端都很好用，特别是PC网页端自动填充密码功能真心不错，填充率非常高。

让我们来看看其他除了`LastPass`还有哪些密码管理工具

### [1Password](https://1password.com/sign-up/)
毫无疑问`1Password`是人气最高的一款密码管理工具，支持跨平台而且还配备了中文版。浏览器扩展支持：Chrome, FireFox, Opera, Safari，桌面版同样支持 Windows, Mac, Android, iPhone, iPad。如果不差钱，完全可以选择`1Password`

#### 费用
- 个人版：每月 2.99 美元；
- 家庭版：每月4.99 美元，可以包含 5 个账号使用。
- 购买后，一个账号可以在多个平台登录进行同步使用。
- 另外：1Password 提供 30 天免费试用，可以体验后根据需求选择购买。



### [Enpass](https://www.enpass.io/)
`Enpass`同样支持跨平台，最大的特点是密码不统一存储在官方的服务器上。如果我们想跨终端同步数据，可以借助一些云盘服务（比如DropBox、坚果云等）来实现，如果不想把数据上传到云盘也可以通过局域网来备份和传输。
#### 费用
- `Enpass`桌面版是不收费的，移动端只能免费同步20条账号和密码
- 如果想在移动端查看更多的数据，可以购买专业版，价格为68元，一次购买终生享用。



### [Bitwarden](https://bitwarden.com/pricing/)
`Bitwarden`也是一款免费的密码管理工具(基础功能免费)，对于我们个人来说，这些功能就够用的。我平时就使用一个PC端外加一个移动端。
`Bitwarden`最大的优势是开源，并且支持我们自建云端存储服务器，可以使用官方提供的客户端连接到我们自己服务器上，然后自己的密码就可以存储在自己的服务器上，这样做的目的是更安全。

#### 费用
- 基础版本免费
- 可以自建服务器



我选择使用`Bitwarden`，前几天刚刚把`LastPass`的密码同步过来
#### LastPass迁移到Bitwarden

#### 1. 把LastPass数据导出

![2021_02_23_lastpass_export](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_02_23_lastpass_export.png)

- 登录到LastPass官方网站
- 选择菜单——>登录 
- 在打开的页面上，从边栏菜单中选择“Advanced Options”，然后选择“Export”。
- 输入您的LastPass电子邮件和密码，确认导出请求。
- LastPass以原始文本格式显示数据，打开新的页面后，选择页面上的所有内容，进行复制以将所选数据复制到剪贴板。
- 在桌面创建一个新的文本文件。
- 打开它，然后将复制的内容粘贴到其中，将文件重命名为lastpass.csv

#### 2. 将数据导入到Bitwarden

![2021_02_23_lastpass_import](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2021_02_23_lastpass_import.png)

- 在Bitwarden网站上打开Web Vault。
- 选择顶部菜单中的工具。
- 在“工具”页面上，选择“导入数据”。
- 使用打开的页面上的下拉菜单选择LastPass（csv）。
- 选择“选择文件”，然后选择导出的lastpass.csv文件。
- 选择导入数据以完成该过程。

***  
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)