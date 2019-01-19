---
layout: post
title:  CentOS 设置对外服务端口 
category: Linux
description: CentOS 7.2 最小安装如何打开80端口
---

### 背景
CentOS 7默认安装完毕后， 一般只开放SSH 端口.
如果需要开发更多的对外服务端口，可以通过配置防火墙来实现。

### 解决方法
例如，打开Web服务80端口，相应的命令为：
```
firewall-cmd --zone=public --add-port=80/tcp --permanent
```
然后重启防火墙
```
systemctl restart firewalld.service
```
这样80端口就可以开放对外服务了。

删除端口配置可以用：
```
firewall-cmd --zone= public --remove-port=80/tcp --permanent
```
相应地也需要重启防火墙服务。

--------------------- 
[参考原文：CentOS 7 设置对外服务端口](https://blog.csdn.net/u013582800/article/details/79606597)
