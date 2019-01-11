---
layout: post
title:  CentOS 7.2 无法解析域名问题
category: Linux
description: 如题
---

### 背景
很傻很天真，自以为对虚拟机，宿主机的网络结构很熟悉，但是在真正用到时，还是ping不通目标IP。
本地部署集控配置的过程，需要从registry服务器上拉取最新的集控部署包，但是每次都遇到错误反馈的信息：
```
Error response from daemon: Get https://registry.xxxxxxx.cn/: dial tcp IP: getsockopt: no route to host
```
我开始以为是宿主机和虚拟机之间的网络有限制，但是虚拟机已经设置了桥接，虚拟机分配到的IP和外网的IP是相同网段的， 那么问题到底出在哪里呢？
原来，CentOS 7.2 安装过程是没有装域名解析服务的，如果遇到需要域名解析，就会识别不到IP。所以，如下介绍下CentOS 7.2如何安装域名服务。

### 操作步骤
```
yum install bind   #安装域名服务
chkconfig named on #打开域名服务
```

参考来源：[Centos不能解析域名](https://blog.csdn.net/program_anywhere/article/details/78731234)