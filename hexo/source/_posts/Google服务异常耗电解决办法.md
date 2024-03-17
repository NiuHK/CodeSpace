---
title: Google服务异常耗电解决办法
toc: true
date: 2023-06-30 08:46:00
tags: [刷机]
top: 0
---

>推荐root+gms doze.
gms doze 卸载删不干净，还需要更改install.sh才能删除干净。
gms doze 不工作则可能是系统或模块版本过低

<!-- more -->



## 原因：

国内网状态下ping google服务器疯狂404并重试，导致占用率极大，手机温度达到温控阈值。
## 解决：

1.gms doze（推荐）
https://github.com/Magisk-Modules-Alt-Repo/GMSDoze 
>如果设备系统相同（lmi a13 pixel experience plus-2023-5-12），推荐使用，刷好后续航大幅度提升，配合scene的应用偏见功能完全可以将功耗发热降低至优于国内rom的水平

2.黑域动态gms:
>有弹窗无法取消，并且root开机无法自启动，开发者给的答复是
>1.屏蔽弹窗消息不会支持。
2.root不是主要支持，所以不会修。

3.universal gms doze：
https://github.com/gloeyisk/universal-gms-doze 
>在我的设备（lmi a13 pixel experience plus-2023-5-12）不起作用



## warning！
模块由magisk刷入，所以能否卸载干净以及对设备的危害暂不知道！！！（底下的有人提出过相关issue，但是作者并未作答）