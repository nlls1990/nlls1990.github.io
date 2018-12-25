---
layout: post
title:  MAXHUB adb安装Mark工具
category: MAXHUB 
description: 全局批注小的二维码和大的二维码显示内容不一致.
---

## 背景介绍
广州海珠区某客户，在直播过程中使用二代机MAXHUB产品，在使用过程中使用全局批注进行截图备份， 但是通过批注生成的二维码，小的二维码和大的二维码扫出来的内容不是同一个。

## MAXHUB adb推送全局批注软件
[apk下载链接](https://drive.cvte.com/p/DVaUf4wQxA8Ym7ID)
**Step 1** 进入设置-关于，点击用户协议，狂点MAXHUB的图标，打开ADB
![d75a82591f673d895cb0859ec703a9ab.png](evernotecid://721934AE-46B8-4DCD-A3C6-A872FC7608A1/appyinxiangcom/9795879/ENResource/p2043)

**Step 2** 使用终端adb连接设备
```
adb connect MAXHUB_IP
```

**Step 3** 切换adb为root身份
```
adb root
```

**Step 4** 重新remount挂载磁盘，这样就可读写了
```
adb remount
```

**Step 5** 进入shell，删除MaxhubMark
```
adb shell
cd /system/app
rm -rf MaxhubMark
```

**Step 6** 重启安卓
```
reboot
```

**Step 7** 重新adb连接后，安装apk,提示Success后就可以了
```
adb connect MAXHUB_IP
adb install ~/Desktop/MaxhubMark_master_maxhub_hisi510_release_R.0.1.58

/Users/lucida/Desktop/MaxhubMark_master_maxhub_hi...file pushed. 0.4 MB/s (11269925 bytes in 28.210s)
	pkg: /data/local/tmp/MaxhubMark_master_maxhub_hisi510_release_R.0.1.58.apk
Success
```
**Step 8** 最后验证一下，全局批注的大二维码和小二维码是不是一致的，就可以了