---
layout: post
title:  修改Windows网卡的MAC地址的方法
category: Windows 
description: 因为主板厂商漏烧MAC引出的一系列联想.
---

### 背景介绍
海外客户在开箱一个PC模块后，插入网线总是无法联网，进入cmd命令行后，发现MAC地址为空。
![MAC地址为0](https://api.superbed.cn/pic/5c3462209dc6d651dda7daa6)



### 解决方法
设备在海外，而且事情紧急，只能通过软件去烧写MAC的方法。通过搜索引擎查询， Windows系统是可以手动修改MAC地址的。操作步骤如下：
![手动烧写MAC地址的方法](https://api.superbed.cn/pic/5c3462859dc6d6521665fb65)


### 操作方法
计算机右键-管理-设备管理-网络适配器-Realtek XXXX-属性-高级-属性-网络地址-将不存在改为值，填上MAC保存即可。

### 思考 修改MAC地址的用途？

1. 一般的对于一些单位或者是学校来说，他们的局域网里都有这样的一个情况，那就是通过代理上Internet的时候，大多数的情况下是利用MAC-IP绑定方式来进行验证的。通过修改MAC-IP来获得一些上网的权限。

2. 通过修改MAC地址，我们就可以实现IP欺骗目的，利用这样的手段可以截获一些数据包来进行操作。

3. 有的时候我们买了不正规厂家所生产的网卡，使用的时候发现两块地址一模一样，因此需要更改其中之一，当然这样的事情很少发生。

参考：
[修改mac地址有什么用？](https://product.pconline.com.cn/itbk/software/dnyw/1707/9669898.html)
