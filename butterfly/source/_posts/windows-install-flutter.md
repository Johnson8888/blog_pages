---
permalink: windows-install-flutter.html
title: 【Flutter 1-2】在 Windows 10下配置Flutter开发环境
date: 2020-09-28 22:30:08
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/flutter-cover.jpg
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/flutter-cover.jpg
toc: true
categories: Flutter
tags:
    - Flutter

---



#### **在 Windows 10下安装Flutter+Dart+Android Studio 配置Flutter开发环境**
[文章首发地址](https://johnson8888.github.io/2020/09/28/windows-install-flutter/)
##### **配置环境变量**
由于部分网站被墙的原因，我们需要先配置Flutter国内镜像地址，这两个地址是由Flutter官方维护的，可以放心使用
首先我们找到`此电脑`点击右键，然后点击`属性`

![2020_10_07_my_computer](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_my_computer.png)


然后点击`高级系统设置`
![2020_10_07_heigh_setting](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_heigh_setting.png)

点击`高级`然后找到下面的`环境变量`并点击
![2020_10_07_huanjingbianliang](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_huanjingbianliang.png)
点击`新建`
![2020_10_07_xinjian](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_xinjian.png)
变量名输入`PUB_HOSTED_URL` 变量值输入 `https://pub.flutter-io.cn` 然后点击`确定`
![2020_10_07_input_pub](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_input_pub.png)
继续点击 `新建`
变量名输入`FLUTTER_STORAGE_BASE_URL` 变量值输入 `https://storage.flutter-io.cn` 然后点击`确定`
![2020_10_07_input_storage](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_input_storage.png)
到这里需要的环境变量就配置完成了

##### **开始安装Flutter**
- 下载安装文件并解压缩
[点击进入官网下载需要的版本](https://flutter.dev/docs/development/tools/sdk/releases)
如果不能打开该网站，[可去我的网盘去取版本是1.22.0](https://pan.baidu.com/s/1SgNz14eVc1SDlHlTH7Y0mA) 提取码: awjy
下载完成后在新建一个文件夹解压缩，我这里选的是`C:\src\flutter`
解压成功之后，我们需要将Flutter也配置到环境变量中，flutter文件夹下的`bin`目录路径(我这里是`C:\src\flutter\bin`)配置到环境变量中。打开配置环境变量的步骤参考 上面的步骤`配置环境变量`
双击`Path`来添加
![2020_10_07_find_pth](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_find_pth.png)
将`C:\src\flutter\bin`配置进去
![2020_10_07_flutter_path](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_flutter_path.png)

- 运行 flutter doctor
将路径配置之后我们打开 终端工具`PowerShell` 输入 `flutter doctor`查看还有哪些需要配置。`flutter doctor`是Flutter官方提供的用来检测当前Flutter配置环境的工具，可以快速的帮我们发现问题。
运行之后我们会看到输出如下:
![2020_10_07_flutter_doctor_1](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_flutter_doctor_1.png)

很明显我们还需要安装 `Android Studio`，Andriod Studio是Flutter官方支持的IDE工具。
[去Andriod Studio 官网下载](https://developer.android.com/studio)下载完成后，一路Next安装完成，然后启动Android Studio，第一次安装默认会安装很多依赖，这个等慢慢安装就可以了。
启动之后点击`File`->`Settings`
![2020_10_07_android_studio_settings](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_android_studio_settings.png)


找到`Plugins`在输入框内输入`Flutter`点击安装
![2020_10_07_andriod_studio_install_flutter](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_andriod_studio_install_flutter.png)
安装`Flutter`的时候默认会要求安装`Dart`
![2020_10_07_android_studio_install_dart](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_android_studio_install_dart.png)
安装后重启 `Andriod Studio`

然后我们把`Android SDK`路径配置到系统变量里面
我们先找到`File`->`Other Settings`->`Default Project Structure..`并点击
![2020_10_07_android_sdk](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_android_sdk.png)
找到SDK的路径
![2020_10_07_android_sdk_path](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_android_sdk_path.png)
进入到文件下找到SDK文件夹有一个`platform-tools`的文件夹，复制这个路径添加到系统`Path`中 
变量名是`ANDROID_HOME`
![2020_10_07_adroid_home](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_adroid_home.png)

这时候我们再执行一次 `flutter doctor`
![2020_10_07_doctor_error](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_doctor_error.png)
现在我们只需要再执行一次 `flutter doctor --android-licenses` 弹出的提示选择`y`或者是直接`回车`即可。
然后再运行一次`flutter doctor`已经没有错误提示了。
这样我们的Flutter的环境就配置完成了。

##### **安装Android 模拟器**
打开Android Studio 找到右上角的`AVD Manager`并点击
![2020_10_07_android_studio_avd_manager](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_android_studio_avd_manager.png)

点击`Create Virtual Device...` 选择一个我们需要需要安装的模拟器，然后点击`Next`
![2020_10_07_select_device](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_select_device.png)
在配置页面选择`Hardware - GLES 2.0`
![2020_10_07_hardware_gles](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_hardware_gles.png)


##### **新建Flutter项目并运行**

点击Android Studio 里面的 `File`->`New`->`New Flutter Project`
新建项目并打开
选择我们刚刚安装好的模拟器，并且点击运行 就可以看到效果啦！
![2020_10_07_runing](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_runing.png)





##### **可能会遇到的问题**
在执行 `flutter doctor --android-licenses`出现以下错误
![2020_10_07_fluuter_sdk_error](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_fluuter_sdk_error.png)
需要我们手动安装`Android SDK Platform-Tools`
打开Android Studio 点击`File`->`Settings`->`Android SDK`找到`Android SDK Platform-Tools`安装即可！
![2020_10_07_error_platform_tools](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_10_07_error_platform_tools.png)

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)