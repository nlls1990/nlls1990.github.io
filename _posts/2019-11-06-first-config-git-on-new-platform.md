---
layout: post
title: 第一次配置git环境的操作步骤
category: 工具
description: 在一台新的电脑或新的服务器上配置git环境的操作步骤
---

### 背景
git的初次配置命令使用的频次非常低，但是每一次更换一个新的环境都要重新去做配置，为防止遗忘，特记录下在一个新的环境中进行配置的所有操作步骤

### 配置方法
#### 1

第一次在一台新的电脑或服务器上，需要先安装git工具，从git官网去下载对应的版本即可，不做展开

#### 2
安装完成后，首先需要先生成本地的公钥，需要填写配置的邮箱
```
$ ssh-keygen -t rsa -C "example@email.com"
```
生成完后，进入对应的home目录下，找到.ssh文件夹，将id_rsa.pub的内容加入到github的公钥区

#### 3
本地打开git的bash工具，然后配置本地提交代码的用户名和邮箱
```
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```
至此，初次配置的工作就完成了，可以开始上传或下载代码了
--------------------- 

### 参考原文：
[5 起步 - 初次运行 Git 前的配置](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE)
