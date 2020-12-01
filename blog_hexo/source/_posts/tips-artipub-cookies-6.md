---
title: artipub点击"更新cookie状态"无任何反应
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-30 09:29:15
cover:
thumbnail:
keywords: artipub
tags: 
    - Tips
categories: Tips
description:
photos:
fileName:
type:
---

作者 | 弗拉德
来源 | 弗拉德（公众号：fulade_me)

### artipub
[ArtiPub](https://github.com/crawlab-team/artipub) (Article Publisher 的简称，意为 "文章发布者") 是一款开源的一文多发平台，可以帮助文章作者将编写好的文章自动发布到掘金、SegmentFault、CSDN、知乎、开源中国等技术媒体平台。
<!--more-->
点击"更新cookie状态"按钮之后错误如下:
``` bash
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 954)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 956)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 503
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 958)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 960)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 962)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 964)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 966)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 968)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 970)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 503
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 972)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 974)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 976)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 978)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 503
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 980)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 982)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 984)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 400
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 986)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 503
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 988)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 503
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 990)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 503
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 992)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 503
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 994)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 503
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 996)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 503
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 998)
(node:72715) UnhandledPromiseRejectionWarning: Error: Request failed with status code 503
    at createError (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/createError.js:16:15)
    at settle (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/core/settle.js:17:12)
    at IncomingMessage.handleStreamEnd (/Users/Joker/Desktop/artipub/artipub/node_modules/axios/lib/adapters/http.js:244:11)
    at IncomingMessage.emit (events.js:228:7)
    at endReadableNT (_stream_readable.js:1185:12)
    at processTicksAndRejections (internal/process/task_queues.js:81:21)
(node:72715) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 1000)
```

#### 运行环境：
- macOS 10.15.5
- 已安装mogodb并已启动
- 已启动`npm run start:frontend`
- 登录助手已安装正确
#### 原因
这是因为执行`npm run start:backend`命令时没有添加`sudo`权限的问题。
使用`sudo npm run start:backend`启动，然后再点击"更新cookies"状态就可以了。

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)