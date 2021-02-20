---
layout: post
title: "IDEA的output窗口中文乱码解决"
excerpt_separator: "<!--more-->"
categories:
  - Post Formats
tags:
  - Post Formats
  - readability
  - standard
last_modified_at: 2017-03-09T10:55:59-05:00
---



## IDEA的output窗口中文乱码解决

### 第一步：

找到intellij idea安装目录，bin文件夹下面idea64.exe.vmoptions和idea.exe.vmoptions这两个文件，分别在这两个文件末尾添加：**-Dfile.encoding=UTF-8**

<!--more-->

### 第二步：

找到intellij idea的file—settings—Editor—FileEncodings的GlobalEncoding和ProjectEncoding和Default encoding for properties都配置成UTF-8

### 第三步：

在部署Tomcat的VM options（edit configrations）项中添加：-Dfile.encoding=UTF-8

### 第四步：

重启IDEA