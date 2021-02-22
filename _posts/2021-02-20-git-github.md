---
layout: post
title: "git工作流"
excerpt_separator: "<!--more-->"
categories:
  - Post Formats
tags:
  - Post Formats
  - readability
  - standard
last_modified_at: 2017-03-09T10:55:59-05:00
---



## git工作流

### git本地与github交互步骤：

1. 生成SSH-key，并添加到中央仓库

2. 克隆远程仓库 ： `git clone 远程仓库地址`（此时down下来的是main分支）

3. 直接拉取远程分支（`git fetch origin brh:brh`）并切换到子分支（`git checkout brh`）

   <!--more-->

4. 在本地分支开发（修改、删除、新增均需经历2步： `git add 文件`和 `git commit -m "注释"`）

5. 拉取远程仓库最新代码（git fetch origin）

6. 合并远程分支，解决冲突（origin/brh -> brh: 远程分支合并到本地）

7. 将本地分支推送到远程仓库

8. 负责任负责将origin/brh合并到origin/main

![image-20210220142026127](/img/image-20210220142026127.png)
