---
title: 是时候来薅京东的羊毛了，自动化签到脚本！
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-13 17:14:49
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_jd_sigh.png
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_conver_jd_sigh.png
tags: 
    - Tips
categories: Tips
keywords: 京东自动签到，签到脚本，京东双11，京东618
description: 双十一刚刚过，相信很多小伙伴也都剁手了。今年电商平台同样给出了很多优惠。有些优惠，比如红包，是靠运气来获得的，但是还有一些优惠是靠长期坚持才能获得。比如：签到、东东萌宠。每天都能坚持签到固然很棒，但是如果有脚本可以自动签到，那岂不是更美？
photos:
fileName:
type:
---
作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)
[文章首发地址](http://fulade.me/tips-jd-auto-sigh-2.html)
>双十一刚刚过，相信很多小伙伴也都剁手了。今年电商平台同样给出了很多优惠。有些优惠，比如红包，是靠运气来获得的，但是还有一些优惠是靠长期坚持才能获得。比如：签到、东东萌宠。每天都能坚持签到固然很棒，但是如果有脚本可以自动签到，那岂不是更美？
<!--more-->
[自动签到脚本](https://github.com/Johnson8888/jd_sign_bot)此脚本涵盖了目前京90%以上的签到任务，我们只需要简单配置，每天定时触发，就可以签到，领奖品了。而且都是**免费的**。
##### 运行环境
- node.js
- Server酱(可选)

##### 获取京东Cookie
这里以`Chrome`浏览器为例，`Edge`、`360浏览器`、`QQ浏览器`同样支持。
- 打开Chrome浏览的隐私模式，输入[https://m.jd.com/](https://m.jd.com/)。
- 按下键盘上的`F12`进入调试模式，选择手机模式。
![2020_11_13_auto_sign_device](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_auto_sign_device.jpg)
如果没有登录就使用`手机验证码`方式登录(已登录，可忽略)，使用验证码登录获取的`cookie`有效时长30天左右，存活时间更长。
- 登录成功后，点击`Network`
![2020_11_13_auto_sign_network](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_auto_sign_network.png)

然后点击箭头所指的这个按钮清理一下，因为网络请求太多了，不方便查看。
![2020_11_13_auto_sign_clear](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_auto_sign_clear.png)
清理完了之后，点击一下`我的`。

![2020_11_13_auto_sign_gif](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_auto_sign_gif.png)
这个时候我们找到一个`log.gif?`开头的请求，点击它，就可以看到`cookie`字段了。
![2020_11_13_auto_sign_cookie](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_auto_sign_cookie.png)

- 这样复制出来的cookie比较长，我们只需要`pt_pin=xxxx;`和 `pt_key=xxxx;`部分的内容即可(注:英文引号`;`是必要的)。
可以用下面的脚本，直接在`console`里面输入下面脚本按`enter`回车键。
``` js
var CV = '单引号里面放上面拿到的cookie';
var CookieValue = CV.match(/pt_pin=.+?;/) + CV.match(/pt_key=.+?;/);
copy(CookieValue);
```
这样子整理出关键的的cookie已经在你的剪贴板上，可直接粘贴。
我们先把它保存好，下面的步骤要用到。

##### 配置 Server酱
[Server酱](http://sc.ftqq.com/3.version)是一个免费的，可以推送消息到我们微信的服务。
推送服务可以帮助我们每天观察签到的情况，如果出错了，可以及时调整。如果有的小伙伴不需要，可忽略这个步骤，直接进入下一步。
- 打开主页 [http://sc.ftqq.com/3.version](http://sc.ftqq.com/3.version)，点击右上角`登入`
![2020_11_13_server_jiang_main_page](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_server_jiang_main_page.jpg)
- 使用Github 授权，登录。
![2020_11_13_server_jiang_login](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_server_jiang_login.jpg)
输入账号密码即可。
- 登录成功后点击`微信推送`并扫描二维码绑定微信
![2020_11_13_server_jiang_wechat](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_server_jiang_wechat.jpg)
使用手机打开微信，扫描屏幕上的二维码，如果未关注，先关注，然后再绑定即可。
![2020_11_13_server_jiang_qrcode](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_server_jiang_qrcode.jpg)
- 绑定成功后，点击右上方的`发送消息`链接，就可以看到你自己的 `key`值，保存下来，后面会用到。
![2020_11_13_server_jiang_test](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_server_jiang_test.jpg)
当然你也可以在下面的`在线发送工具`测试推送是否生效。

##### 配置本地代码
- 使用`git clone`命令将[https://github.com/Johnson8888/jd_sign_bot](https://github.com/Johnson8888/jd_sign_bot)代码下载下来。
- 下载完成后，我们需要安装项目所需要的依赖。使用命令行工具(Mac下使用`Termainal`,Windows下使用`PowerShell`)进入到`jd_sign_bot`文件内。在命令行内输入 `npm install --dependencies`，等待运行完成。
![2020_11_13_npm_install](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_npm_install.png)
此时，项目文件夹内会多出一个 `node_modules`文件夹。

- 配置Cookies
打开文件内的`JD_DailyBonus.js`文件，修改`Key`参数为刚刚获取到的cookies
![2020_11_13_input_server_jiang](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_input_server_jiang.png)

- 配置Server酱
打开文件内的`app.js`文件，修改`serverJ`参数为刚刚获取到的Server酱的key
![2020_11_13_input_cookies](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_input_cookies.png)

##### 执行签到
进入到`jd_sign_hot`文件夹下，执行 `node app.js`即可签到！
![2020_11_13_auto_sign_exec](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_auto_sign_exec.jpg)
此时我们的脚本在本地就已经部署好了，如果你想更编辑，可以把代码部署到云服务器上，这样就不需要每天点击触发了。
或者你也可以部署在自己的服务器上，每天定时执行。



#### 你也可以 将脚本部署在腾讯云 · 云函数 上
去到[腾讯云函数地址](https://console.cloud.tencent.com/scf/index)，如果没有开通此服务的顺手开一下就可以了。
- 单击左侧导航栏函数服务，进入**函数服务**页面。 在页面上方选择一个地域，最好选择离你常用地区近点的，不至于导致账号异常。单击**新建**。如下图所示：
![2020_11_13_tengxun_clound](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_tengxun_clound.jpg)

- 在**新建函数**页面填写函数基础信息，单击下一步。如下图所示：
![2020_11_13_tengxunyun_input](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_tengxunyun_input.png)

- 函数名称：可以自定义，比如为`jd_sign`。 运行环境：选择 `Nodejs 12.16`。 创建方式：选择 `空白函数`。
确保环境为`Nodejs 12.16`，执行方法改为：`index.main_handler`，提交方式建议选本地文件夹。
- 然后将刚才下载并配置好的文件夹`jd_sign_bot`上传上来。（记得node_modules文件夹一并上传），完了后点击下面的高级设置。
![2020_11_13_tengxunyun_input_1](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_tengxunyun_input_1.png)

- 内存用不了太大，64MB就够了（64M内存，免费时长6,400,000秒，内存与免费时长大致关系可以参看云函数官方说明），超时时间改为最大的900秒，然后点击最下面的完成。


![2020_11_13_tengxunyun_input_3](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_tengxunyun_input_2.png)

- 点击刚创建的函数

![2020_11_13_tengxunyun_input_3](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_tengxunyun_input_3.png)

点击`创建触发器`

![2020_11_13_tengxunyun_input_4](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_tengxunyun_input_4.png)

比如我填写的是 `0 45 8 * * * *`，每天上午8点45触发一次。
腾讯云提供了相关配置[Cron的文档](https://cloud.tencent.com/document/product/583/9708#cron-.E8.A1.A8.E8.BE.BE.E5.BC.8F)，也有第三方[测试工具](https://tool.lu/crontab/)。



##### 测试一下
我们打开刚才创建的云函数，点击`保存并测试`，等过1分钟左右手机上收到推送，那我们的配置就是成功的。
如果没有收到推送，可以点击`日志查看`排查问题。
![2020_11_13_tengxun_cloud_test](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2020_11_13_tengxun_cloud_test.png)

如果你不喜欢腾讯云的服务
我们可以参考[ruicky大神的博客](https://ruicky.me/2020/06/05/jd-sign/)，将脚本部署在Github Actions上面也是也可以的。

***  
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)