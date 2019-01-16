---
layout: post
title:  CentOS 7.2 开启网卡功能
category: Linux
description: 如题
---

### 背景
![背景](https://api.superbed.cn/pic/5c3ee1689dc6d6264b5e2d28)

安装CentOS 7.2系统，安装成功后，网卡默认是关闭的，未配置ip地址。需要配置为开机自动打开网卡。

### 解决方法
1. 进入网络配置目录
```
cd /etc/sysconfig/network-scripts/
```
2. 查看关闭的网卡
```
ls
```
![开网卡1](https://api.superbed.cn/pic/5c3ee16a9dc6d6264b5e2d29)
3. 修改该文件,将ONBOOT=no改为yes。
```
vim ifcfg-enp0s3
```
![开网卡2](https://api.superbed.cn/pic/5c3ee16c9dc6d6264c4a7f74)

4. 重启网络服务,就OK了
```
service network restart
```

参考来源：[Cent OS 开启网卡](https://blog.csdn.net/nkd50000/article/details/78903479)