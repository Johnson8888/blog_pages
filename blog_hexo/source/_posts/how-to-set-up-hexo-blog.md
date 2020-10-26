---
permalink: how-to-set-up-hexo-blog.html
title: Mac下使用GitHub+Hexo搭建个人博客
date: 2020-09-26 14:09:54
cover: https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/page_conver_hexo.png
thumbnail: https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/page_conver_hexo.png
toc: true
description: 安装和配置Hexo博客
tags:
   - Github
---


开始之前需要在电脑上安装好[Git](https://git-scm.com/)和[node.js](https://nodejs.org/en/)，Mac上可以使用Homebrew命令行工具来安装Git和node.js

##### **安装Homebrew**
在命令行工具输入以下命令，如果已经安装过Homebrew可以忽略
``` bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
<!--more-->
##### **Homebrew 安装 node.js**
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
##### **Homebrew 安装git**
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
##### **使用 npm 安装 [hexo](https://hexo.io/zh-cn/docs/)**
``` bash
sudo npm install -g hexo-cli
``` 
安装完成后，在Desktop创建一个blog文件夹，在该文件夹下初始化我们的博客
``` bash
cd ~/Desktop && mkdir blog && cd blog
``` 
在该文件件目录下执行博客初始化操作
``` bash
# 会下载一些node.js的依赖文件
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
![preview_hexo_20200928](https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/preview_hexo_20200928.jpg)



##### **配置客户端git  添加SSH Key到github**
如果已经配置过，该步骤可以忽略
在命令行输入配置用户名和账号的命令
``` bash
git config --global user.name "username"
git config --global user.email "email@gmail.com"
```
其中 `username` 是你的用户名，`email@gmail.com`是你github的登录邮箱
然后通过终端命令生成SSH Key
``` bash
ssh-keygen -t rsa -C "email@gmail.com"
```
如果已经创建过会出现 `Overwrite (y/n)? n`提示可以输入 `n`，如果没有创建过会要求我们输入密码，然后一路回车下去就行，执行完成后会在`~/.ssh/id_rsa.pub`目录下生成 需要使用的 key。

可以使用命令行输出key并复制
``` bash
cat ~/.ssh/id_rsa.pub
```
或者可以找到这个文件并打开它，复制里面的内容。

登录github账号 找到 `setting`
![setting_20200928](https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/setting_20200928.png)

先点击 ` SSH and GPG keys` 然后再点击 ` New SSH key ` 进入到配置 SSH Key 的页面
![select_sshkey_20200928](https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/select_sshkey_20200928.jpg?token=ABHYKC5WITD7CZYQDC4ABAK7OFO3W)

然后输入复制好的key的内容

![set_my_pc_ssh_key_20200928](https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/set_my_pc_ssh_key_20200928.png?token=ABHYKC4PWIEGG63VBN3Q3NS7OFPEC)

点击 ` Add SSH Key ` 即可

##### **本地博客关联到Github主页**
登录Github并且创建一个名字为 `username.githug.io` 的仓库，比如我的仓库名字为 `Johnson8888.github.io`
因为我已经创建过了，所以会显示红色，如果创建过，会显示绿色的，然后点击创建。切记一定要选择 `Public`，否定不能访问。
![create_my_repo_20200928](https://raw.githubusercontent.com/Johnson8888/blog_pages/master/images/create_my_repo_20200928.png?token=ABHYKCYY4HSYNU4W6VVG5Q27OFPVO)

然后命令行切换到本地blog目录下 `cd ~/Desktop/blog`
执行命令
``` bash 
sudo npm install hexo-deployer-git --save
```
然后开始修改配置文件 `~/Desktop/blog/_config.yml`
修改 `deploy`部分为
``` yaml
deploy:
  type: git
  repo: git@github.com:Johnson8888/Johnson8888.github.io.git
  branch: master
```
然后就可以把博客push到github了
在命令行执行
``` bash
#生成我们想要的博客文件
hexo g
#将本地的博客文件push到github
hexo d
```
`hexo d `执行成功后，就可以查看我们的[Blog](https://johnson8888.github.io)了

##### **开始写博客**
在命令行执行
```
hexo new firstPage.md 
```
会在 `~/Desktop/blog/source/_post`目录下生成 `firstPage.md` 打开这个文件就可以开心的写博客了
写完后重新执行
``` bash
hexo g
hexo d
```
就可以同步博客到github
#### **Todo**
- 申请域名指向博客，这样就可以直接使用域名访问了
- hexo支持很多模板样式 可以去[官网](https://hexo.io/themes/)选择自己喜欢的使用

##### **附 hexo常用命令**
```
hexo n "博客名称"  => hexo new "博客名称"   #这两个都是创建新文章，前者是简写模式
hexo p  => hexo publish
hexo g  => hexo generate  #生成
hexo s  => hexo server  #启动服务预览
hexo d  => hexo deploy  #部署  

hexo server   #Hexo 会监视文件变动并自动更新，无须重启服务器。
hexo server -s   #静态模式
hexo server -p 5000   #更改端口
hexo server -i 192.168.1.1   #自定义IP
hexo clean   #清除缓存，网页正常情况下可以忽略此条命令
hexo g   #生成静态网页
hexo d   #开始部署
```