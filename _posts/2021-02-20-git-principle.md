---
layout: post
title: "git原理"
excerpt_separator: "<!--more-->"
categories:
  - Post Formats
tags:
  - Post Formats
  - readability
  - standard
last_modified_at: 2017-03-09T10:55:59-05:00
---



## git原理

### git基础

引用自：https://www.cnblogs.com/cb0327/p/5066685.html

本文背景，在实际项目中使用git已有一年，发现不少同事虽然会使用常用git指令，但并不理解每个指令对应的作用原理。今天静下心总结下git 的基本理解：代码的存在区域；本文以实际项目出发，理清使用git过程中，代码的迁徙流程。

<!--more-->

git跟传统的代码管理器（如:svn）不同， 主要区别在于git多了个**本地仓库**以及**缓存区**，所以即使无法联网也一样能提交代码。术语解释：

**工作区间:** 即我们创建的工程文件， 在编辑器可直观显示；

**缓存区:** 只能通过git GUI或git shell 窗口显示，提交代码、解决冲突的中转站；

**本地仓库:** 只能在git shell 窗口显示，连接本地代码跟远程代码的枢纽，不能联网时本地代码可先提交至该处；

**远程仓库:** 即保存我们代码的服务器，本文以公共版本控制系统：**github**为例，登录github账号后可直观显示；

<img alt="Mobile home page" src="../img/image-20210220144431394.png?raw=true" />

### 文件状态变化

<img alt="Mobile home page" src="../img/image-20210220150650310.png?raw=true" />

**说明：**

* Untracked：表示新增文件

* Unmodified：表示该文件没有变化，工作区与分支中的文件是一致的

* Modified：表示文件修改或删除

* Staged：表示对文件的操作信息添加到了暂存区

### git分支管理

#### master分支

默认情况下，master是一条线，git利用master指向最新的提交，在用“HEAD”指向”master”，就能确定当前分支以及当前分支的提交点

<img alt="Mobile home page" src="../img/image-20210220145059956.png?raw=true" />

#### 子分支

当用户创建一个新的分支（假设分支名称我“brh”）后，git会创建一个新的brh指针，此指针指向master相同的提交，在将HEAD执行brh，就表示当前分支在brh上

<img alt="Mobile home page" src="../img/image-20210220145201887.png?raw=true" />

在整个过程之中，发现HEAD的指针发生了变化，因为HEAD指向当前的分支brh（当前工作的分支），一旦创建了分支，那么一定需要针对代码进行新的修改并进行了提交，此时master分支不会改变，只有brh分支会发生改变

<img alt="Mobile home page" src="../img/image-20210220145227479.png?raw=true" />

那么此时master分支的版本就落后于子分支了，但是不管子分支在怎么开发，也不是最新的发布版本，所有发布版都来自于master分支，那么就必须将子分支与master分支进行合并

<img alt="Mobile home page" src="../img/image-20210220145244636.png?raw=true" />

当分支合并之后，实际上就相当于master分支的提交修改为了子分支的提交点，而这个合并应该在master分支上完成，所以HEAD需要修改指针，断开brh分支，指向master分支

 

​     如果已经将brh分支合并到了master分支，可以将brh分支删除掉

<img alt="Mobile home page" src="../img/image-20210220145303422.png?raw=true" />
