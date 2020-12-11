---
title: Anaconda和conda命令的安装和使用
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-12-11 09:35:17
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_10_python_artificial_intelligence.png
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_10_python_artificial_intelligence.png
tags: 
    - 人工智能
    - Anaconda
    - conda
    - TensorFlow
categories: 
keywords:
description: Anaconda是一个开源的工具，目前拥有超过六百万的用户。Anaconda致力于提供最便捷的方式来使用Python进行数据科学计算和机器学习。目前，Anaconda拥有超过250+的数据科学工具包，conda工具包可用于Windows，MacOS和Linux三种平台的虚拟环境管理系统。Anaconda支持当前比较流行的一些人工智能的库，比如Sklearn，TensorFlow，Scipy。
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

#### Anaconda
[Anaconda](https://www.anaconda.com/products/enterprise)是一个开源的工具，目前拥有超过六百万的用户。Anaconda致力于提供最便捷的方式来使用Python进行数据科学计算和机器学习。目前，Anaconda拥有超过250+的数据科学工具包，conda工具包可用于Windows，MacOS和Linux三种平台的虚拟环境管理系统。Anaconda支持当前比较流行的一些人工智能的库，比如Sklearn，TensorFlow，Scipy。

#### 下载安装包
直接去到Anaconda的官网，找到[下载地址](https://www.anaconda.com/products/individual)，点击`Download`按钮，然后找到页面最下方的下载部分。
![2020_12_11_anaconda_command_installer](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_11_anaconda_command_installer.png)
我们可以看到Anaconda提供了两种安装方式，一种是带有图形界面的安装方式`Graphical Installer`，另一种是 以命令行的方式`Command Line Installer`安装。  
我们选择`64-Bit Graphical Installer`使用图形界面的方式来安装，点击下载。
#### 安装步骤(基于MacOS)
1. 双击下载好的安装文件(下载好的安装文件如下图所示)，开始安装。
![2020_12_11_anaconda_pkg](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_11_anaconda_pkg.png)

2. 一路点击`继续`
![2020_12_11_anaconda_install_step_1](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_11_anaconda_install_step_1.png)
 这里也选择`继续`即可。
![2020_12_11_anaconda_install_step_2](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_11_anaconda_install_step_2.png)

3. 在Mac里面的`启动图`找到刚安装好好的`Anaconda`，名字叫：`Anaconda-Navigator`，点击启动，启动后的样子如下：
![2020_12_11_anaconda_launch](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_12_11_anaconda_launch.png)


#### 配置命令行工具
此时，我们已经安装好的`Anaconda`的客户端，但是很多情况我们都需要在命令使用`conda`命令，这个时候在命令行工具输入
``` bash
conda -version
```
显示如下(我电脑配置了zsh，所以会显示zsh):
``` py
zsh: command not found: conda
```
显然我们还不能使用`conda`命令。

##### 1. zsh配置流程
找到`.zshrc`文件，一般在`/Users/{username}/.zshrc`，其中`{username}`是你当前Mac的用户名字哦。
用记事本打开`.zshrc`文件(你也可以使用`vim`命令来编辑)，在该文件的最后一行添加:
```
export PATH="/opt/anaconda3/bin:$PATH"
```
然后保存
命令行工具进入到`/Users/{username}`目录下，执行
``` bash
source .zshrc
```
接着执行
``` bash
conda --version
```
就可以看到输出的版本号了：
``` bash
conda 4.9.2
```
##### 2. bash_profile 配置
找到`.bash_profile`文件，一般在`/Users/{username}/.bash_profile`，其中`{username}`是你当前Mac的用户名字哦。
用记事本打开`.bash_profile`文件(你也可以使用`vim`命令来编辑)，在该文件的最后一行添加:
```
export PATH="/opt/anaconda3/bin:$PATH"
```
然后保存
命令行工具进入到`/Users/{username}`目录下，执行
``` bash
source .bash_profile
```
接着执行
``` bash
conda --version
```
就可以看到输出的版本号了：
``` bash
conda 4.9.2
```

#### 添加常用源
由于网络问题，有些时候直接同国外下载库会比较慢，我们可以给`conda`配置国内的镜像源，添加国内的镜像源命令如下：
1. 清华源
``` bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge 
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
# 设置搜索时显示通道地址
conda config --set show_channel_urls yes
```
2. 添加中科院源

``` bash 
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/bioconda/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/menpo/
# 设置搜索时显示通道地址
conda config --set show_channel_urls yes
```
查看是否添加成功可是用命令
``` bash
conda config --show
```
在 `channels`这个字段这里显示已经添加的源
```
channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
  - defaults
```

#### conda常用命令
**升级**
``` bash
conda update conda  # 更新 conda
conda update anaconda # 更新 anaconda
conda update anaconda-navigator    #update最新版本的anaconda-navigator  
conda update python # 更新 python
```

**管理环境**
``` bash
conda env list  #显示所有的虚拟环境
conda create --name fulade python=3.7 # 创建一个名为 fulade 环境，指定Python版本是3.7
activate fulade  # 激活名为 fulade 的环境 (Windows 使用)
source activate fulade  # 激活名为 fulade 的环境 (Linux & Mac使用用)
deactivate fulade   #关闭名为 fulade的环境( Windows使用)
source deactivate fulade  # 关闭名为 fulade的环境(Linux & Mac使用）
conda remove --name fulade --all # 删除一个名为 fulade 的环境
conda create --name newname --clone oldname # 克隆oldname环境为newname环境
```

**package管理**
``` bash 
conda list  #查看当前环境下已安装的package
conda search numpy # 查找名为 numpy 的信息 package 的信息
conda install numpy  # 安装名字为 fulade 的package 安装命令使用-n指定环境 --channel指定源地址
conda install -n fulade numpy  # 在fulade的环境中 安装名字为 fulade 的package
conda install --channel https://conda.anaconda.org/anaconda tensorflow=1.8.0  # 使用地址 https://conda.anaconda.org/anaconda 来安装tensorflow
conda update numpy   #更新numpy package
conda uninstall numpy   #卸载numpy package
```
**清理conda**
``` bash 
conda clean -p      //删除没有用的包
conda clean -t      //删除tar包
conda clean -y --all //删除所有的安装包及cache
```

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)