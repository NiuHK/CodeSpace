---
title: MS_Office精简下载安装激活
toc: true
top: 0
date: 2024-03-24 11:20:49
tags: [环境配置]
---

>基于VL版本office的MS_Office精简下载安装激活

<!-- more -->

[YouTube视频](https://www.youtube.com/watch?v=VSjRx7Hoa60)
# 下载官方部署器
访问官方部署器地址：
https://www.microsoft.com/en-us/download/details.aspx?id=49117

![](https://picstorage.danielniu.me/imgs/202403241859813.png)

直接点击download，下载，并运行。

选择一空文件夹，完成程序。

![](https://picstorage.danielniu.me/imgs/202403241901381.png)

# 下载部署自定义文件

访问自定义网址：
https://config.office.com/deploymentsettings

![](https://picstorage.danielniu.me/imgs/202403241902791.png)

选择: 64位 批量许可证版本的office套件，对应的visio、project（这俩还看起来挺有用的，不用的话选择无）其他产品选择 语言包

应用->选择需要的项目

语言->选择中文

剩下的全部默认

导出->保留当前设置，命名为config

下载该文件，并导入当刚刚的文件夹中

# 下载、安装
管理员cmd，cd到刚刚的文件夹

运行 setup /download config.xml

等待命令运行完毕（没有提示，等待弹出下一个输入框）

运行 setup /configure config.xml

等待安装完成，重启，看是否激活

未激活就管理员cmd格式下cd C:\Program Files\Microsoft Office\Office16 重启并查看激活状态

还不行直接使用网上搜的kms激活VL版本office方法。
