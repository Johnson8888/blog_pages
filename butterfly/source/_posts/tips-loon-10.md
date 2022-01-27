---
title: 薅羊毛利器——Loon Cookie放在本地一点也不担心
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: ''
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2021-03-29 17:10:30
cover: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2022_01_27_jd_loon_index.png
thumbnail: https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2022_01_27_jd_loon_index.png
tags: 
    - Tips
categories: Tips
keywords: Loon、京东、羊毛
description:
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)


#### Loon
[Loon](https://apps.apple.com/us/app/loon/id1373567447)是一款在iOS系统下的代理工具(**目前还没有Android版本**)，它支持在本地执行js脚本，只需简单配置即可成为薅羊毛利器
#### 下载
- 可以去美区AppStore下载，价格$4.99，需要有一个美区的AppleId账号，并且充值美元
- 可以去某宝或拼夕夕搜索并购买，价格大概在￥9.99

#### 配置
![2022_01_27_jd_loon_1](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2022_01_27_jd_loon_1.jpg)
然后将下面 框里面的配置赋值粘贴进去，点击保存

``` bash
[General]
# IPv6 支持
ipv6 = false
## skip-proxy和bypass-tun 一般不需要做改动,除非你自己知道自己在做什么
# 需要跳过代理的IP段及其域名,其中的域名和IP段将不会在通过规则匹配
skip-proxy = 127.0.0.1,192.168.0.0/16,10.0.0.0/8,172.16.0.0/12,100.64.0.0/10,localhost,*.local,passenger.t3go.cn,passenger.t3go.cn
# 设置不通过tun的域名和IP,同上所在内容将不会走规则匹配
bypass-tun = 10.0.0.0/8,100.64.0.0/10,127.0.0.0/8,169.254.0.0/16,172.16.0.0/12,192.0.0.0/24,192.0.2.0/24,192.88.99.0/24,192.168.0.0/16,198.18.0.0/15,198.51.100.0/24,203.0.113.0/24,224.0.0.0/4,255.255.255.255/32
# DNS 服务器
# Loon将并行查询所有dns,使用最快返回的IP进行网络访问和分流判断
# 配置DNS服务器IP,不推荐8.8.8.8和1.1.1.1等国外dns提供商,这些并不会提高国外访问稳定性,并且会导致国内域名的dns查询变慢
# 需要使用WIFI和运营商分配的dns可以添加[system],例如dns-server=system,119.29.29.29
# system和公共IP必须二选一填写
dns-server = 119.29.29.29,223.5.5.5
# 允许UDP代理
# 实际需要节点支持,和在节点中开启UDP
allow-udp-proxy = true
# 局域网共享
# 为局域网设备共享HTTP和SOCKS代理
allow-wifi-access = false
wifi-access-http-port = 7890
wifi-access-socket5-port = 7891
# 代理测速 URL
# 用于节点的可用性检测
proxy-test-url = http://www.gstatic.com/generate_204
# 检测超时时间
test-timeout = 5
# 返回真实IP
# 对一下域名不再返回FakeIP 一般不需要添加和修改
real-ip = msftconnecttest.com, msftncsi.com, *.msftconnecttest.com, *.msftncsi.com, *.srv.nintendo.net, *.stun.playstation.net, xbox.*.microsoft.com, *.xboxlive.com, *.battlenet.com.cn, *.battlenet.com, *.blzstatic.cn, *.battle.net
# 解析器
# 用于订阅 规则 复写等的解析
# 必须在配置中填写解析器URL,否则在UI不会出现解析器选项
# 现在Loon解析器功能暂时功能较弱,非必要条件下无需使用
resource-parser = https://raw.githubusercontent.com/Peng-YM/Sub-Store/master/scripts/sub-store-parser.js
# 运行模式SSID
# 用于在不同网络环境下切换Loon的运行模式,全局直连(direct)、自动分流(rule)和全局代理(proxy)
# 通过ssid(WIFI名)进行判断
# ssid-trigger参数,用于指定SSID下流量模式切换,（default表示默认,cellular表示蜂窝,目前支持三种值：,, 
# 以下表示蜂窝数据(cellular)使用自动分流模式(rule),当链接WIFI名为ASUS的WIFI时使用直连模式(direct)
# 链接WIFI名为TPLINK的WIFI时使用自动分流模式(rule),其他情况(default)使用全局代理模式(proxy)

# ssid-trigger="proxy":rule,"cellular":rule,"ASUS":direct,"TPLINK":rule

# 本地节点
[Proxy]
# 用于书写自己的节点,节点格式参考https://raw.githubusercontent.com/Loon0x00/LoonExampleConfig/master/Nodes/ExampleNodes.list
# 可以直接从Loon的节点列表中通过信息,复制出对应节点的Loon格式

# 机场订阅
# Loon订阅支持ss,ssr,trojan,vmess(v2ray)的原始订阅格式,可不使用转换器直接订阅
# 也可以使用Loon格式的专属订阅,节点格式参考[本地节点]
[Remote Proxy]
app = https://iwxf.netlify.app,udp=false,fast-open=false,img-url=app

# 节点过滤,为策略组过滤是需要的节点,比如过滤订阅的所有的新加坡节点、香港节点、美国节点等
[Remote Filter]
机场节点 = NameRegex, FilterKey = "(.*)"
[Proxy Group]
All = select,app,机场节点
# img-url为策略组图标,可选项

## 规则,用于自动分流 
# 本地规则
# 通常优先于订阅规则
# 规则优先级,从上往下依次匹配
# 格式: 类型,域名或IP,策略组
# 具体可参考https://raw.githubusercontent.com/Loon0x00/LoonExampleConfig/master/Rule/ExampleRule.list
[Rule]
DOMAIN,qq.com,DIRECT
DOMAIN-SUFFIX,baidu.com,DIRECT

# 以下两个规则将在最后匹配,优先级最低
# 若之前规则没匹配上,则通过查geoip数据库,如果请求是CN(中国)则走直连
GEOIP,CN,DIRECT
# 最后匹配的规则,之前没有匹配上的规则的请求将会触发这条规则
# 将走Global策略组所选节点
FINAL,Global

# 远程规则订阅
# 优先级从上往下
# 优先于GEOIP和FINAL本地规则
[Remote Rule]
https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/China/China.list, policy=direct, tag=国内域名, enabled=true
# 使用Global策略组,匹配上国外域名规则的请求将会走Global所选节点
https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Proxy/Proxy_Domain.list, policy=Global, tag=国外域名, enabled=true


# 本地脚本
[Script]
enable = false
# 远程脚本订阅
[Remote Script]
https://raw.githubusercontent.com/Tartarus2014/Loon-Script/master/JD.conf, tag=jd, enabled=true
https://raw.githubusercontent.com/Tartarus2014/Loon-Script/master/Script.conf, tag=Script, enabled=true
# 复写,需要配合MITM才能,否则无法针对HTTPS网站
# 主要用于重定向和广告的精准屏蔽(reject)
[URL Rewrite]
enable = false
^https?:\/\/(www.)?(g|google)\.com\.hk 302 https://www.google.com
^https?:\/\/(www.)?(g|google)\.cn 302 https://www.google.com

enable = false
# 京东比价Fix
^https?:\/\/api\.m\.jd.com\/client\.action\?functionId=start reject-200

# Loon插件
[Plugin]
# 需要配置并开启MITM后才能使用
https://raw.subloon.cf/AccelerateRaw.plugin, tag=Github加速, enabled=false

# 为域名指定解析的DNS服务器或者直接为域名指定IP
[Host]

[MITM]
```
该配置文件包含jd的脚本
**Loon的使用和配置方法还有很多，这里就先以配置文件的方式来操作**

#### 安装证书
在`配置`——>`证书管理`安装证书，安装后记得在手机`设置`——>`通用`——>`关于本机`——>`证书信任设置`里面找到以`LOON CA`开头的证书，开启信任


#### 启动
![2022_01_27_jd_loon_2](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2022_01_27_jd_loon_2.jpg)
选择`自动分流`并点击`启动`,第一次启动会弹出对话框，都点确定就行

#### 更新脚本
找到`配置`——>`订阅脚本`点击刷新按钮
![2022_01_27_jd_loon_3](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2022_01_27_jd_loon_3.jpg)
可以点击第一行的jd,进去看一下，确保每个脚本都更新完成，如果更新失败可以多试几次。
**所有脚本更新成功后，找到获取京东cookie的脚本并启用 (这一步很关键)**
![2022_01_27_jd_loon_5](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2022_01_27_jd_loon_5.jpg)

#### 获取 京东Cookie
然后打开 Safari浏览器，输入`jd.com`，找到登录页面并登录(如果已经登录了，点击刷新即可，切记不要登出，否则cookie会失效)
登录成功后一定点一下 这里的 `我的`
![2022_01_27_jd_loon_6](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2022_01_27_jd_loon_6.jpg)
如果有多个账号，可继续点击  Safari 的`无痕浏览`登录其他账号即可
#### 测试
打开`Loon`，找到首页`脚本`
![2022_01_27_jd_loon_7](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2022_01_27_jd_loon_7.jpeg)
点击`jd`找到第一个脚本，左滑并点击`运行`，看到输出有京豆变化可以了~
![2022_01_27_jd_loon_8](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/2022_01_27_jd_loon_8.jpeg)


### 缺点

1. 开启loon之后，手机所有的流量都会通过loon来转发，在使用AppStore下载App的时候，会比较慢。只要关掉loon下载等完成后再开启就可以了


***  
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)