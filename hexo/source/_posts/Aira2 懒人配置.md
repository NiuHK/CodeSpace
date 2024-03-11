---
title: Windows 万能下载器 Aira2 懒人配置：
date: 2024-03-07 19:39:12
toc: true
tags: S[aira2]
---

> Aria2 是一个命令行全功能下载器，同时支持磁力下载，没有原生界面但是可以使用aira2c以及airaNG的web界面

<!-- more -->

# 为什么选择 Aria2？
  Aria2 下载功能比较全面，支持 BT 和磁力链接，性能也相当不错，速度不比迅雷慢。

虽然没有原生应用界面，配置也比较麻烦，但这些可以通过懒人包轻松解决。

# 最快速的懒人配置：
1. 下载懒人包： [LINK](https://link.zhihu.com/?target=https%3A//www.seoipo.com/software/Aria2/)
2. 将懒人包解压到 想要的文件夹，根据路径配置aria2.conf
3. 官网下载 Aria2 程序[LINK](https://github.com/aria2/aria2/releases)，然后解压到快速设置包的存放文件夹中，整体替代其中的 aria2相关程序和文件。
5. 点击 `Aria2c启动器.exe`or`AriaNg启动器.exe`即可开始下载。两者都仅为前端界面，使用文件中的aria2.exe服务，可同时启动。包内均为开源绿色软件，不涉及任何隐私和安装，AutoHotkey 插件容易被误报。

Aria2c webui：`https://aria2c.com/`

AriaNg webui:`file:///D:/Program/aria2/AriaNg/index.html#!/downloading`

# 接管浏览器下载
如果想用 Aria2 接管浏览器的下载管理，需安装插件/扩展。

## Chrome：
安装 添加到 aria2 扩展。下载包可以用 国内搬运地址，或是懒人包内置文件。
如果浏览器无法直接安装 .crx 格式的扩展，可以将文件解压到新文件夹「xxx」，然后在浏览器的地址栏输入 chrome://extensions/ 开启开发者模式，点击加载已解压的扩展程序，选中刚才解压的文件夹「xxx」。

## Firefox：
安装 Aria2 Download Manager Integration 扩展，可参考下方的 Chrome 扩展设置进行配置。


安装完「添加到 aria2」扩展后，右键扩展图标，点击「选项」>「设置」，设置如下：

最小监视：10 M，低于该容量将由浏览器下载。如果 Aria2 要接手所有下载，可以将最小监视设为 0.001。
JSON-RPC 链接：http://localhost:6800/jsonrpc。
注意：「添加到 aria2」图标显示的 en 表示处于开启状态，dis 表示处于关闭状态，点击图标可以切换使用状态。