---
layout: post
title:  CentOS 7.2 YUM 安装 Chrome浏览器
category: Linux
description: 如题
---

### 背景
最近在学习搭建MAXHUB集控系统，使用的Linux系统版本为CentOS 7.2，这个版本的Linux默认是没有安装浏览器应用的，因此边学边应用，今天就记录下如何在命令行安装Chrome浏览器的方法。

### 安装步骤
#### Step 1 创建yum源文件
```
cd /etc/yum.repo.d
sudo touch google-chrome.repos
```

#### Step 2 输入yum源信息
将如下信息写入google-chrome.repos文件中。
```
[google-chrome]
name=google-chrome
baseurl=http://dl.google.com/linux/chrome/rpm/stable/$basearch
enabled=1
gpgcheck=1
gpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub
```

#### Step 3 安装google chrome
```
yum -y install google-chrome-stable --nogpgcheck
```

参考来源：[Centos7 yum安装Chrome浏览器](https://www.cnblogs.com/ianduin/p/8727333.html)