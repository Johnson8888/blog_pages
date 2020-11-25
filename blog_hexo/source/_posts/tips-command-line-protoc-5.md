---
title: Protoc 同时编译多个.protoc文件
author: 弗拉德
avatar: 'https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/img/avatar.jpg'
authorLink: 'http://fulade.me'
authorAbout: '一生只有一个职业:学生'
authorDesc: 技术改变生活
toc: true
comments: true
date: 2020-11-25 15:04:57
cover:
thumbnail:
keywords: protoc同时编译多个，protoc
tags: 
    - Tips
categories: Tips
description:
photos:
fileName:
type:
---
##### 官方的示例
只是编译一个文件的命令行
``` bash
protoc --proto_path=IMPORT_PATH --cpp_out=DST_DIR --java_out=DST_DIR --python_out=DST_DIR --go_out=DST_DIR --ruby_out=DST_DIR --objc_out=DST_DIR --csharp_out=DST_DIR path/to/file.proto
```

我们想要编译同时编译多个文件
只需要把`path/to/file.proto`改为`path/to/*.proto` 即可。

##### 同时编译多个示例：
此示例只是编译了`objc`代码
``` bash
protoc --proto_path=/Users/Demo/Desktop/Demo/proto --objc_out=./out /Users/Demo/Desktop/Demo/proto/*.proto
```

***
![公众号](https://cdn.jsdelivr.net/gh/johnson8888/blog_pages/images/page_footer.jpg)