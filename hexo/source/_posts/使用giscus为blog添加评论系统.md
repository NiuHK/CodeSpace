---
title: 使用giscus为blog添加评论系统
date: 2024-03-08 09:26:42
toc: true
tags: [Icarus,blog,hexo]
top: 0
---
> giscus指一个非常好用的由GitHub讨论支持的评论系统，它可以让你把仓库中的讨论整合到你的博客中。

<!-- more -->

## 如何使用 GitHub 讨论作为聊天系统

为了将GitHub讨论整合到你的博客，我们将使用 giscus。
![img](https://picstorage.danielniu.me/imgs/03e29360d5cc429ca6d7d4062f2c5f83.png)
giscus是一个由GitHub讨论支持的评论系统。它可以让你把仓库中的讨论整合到你的博客中。

你的读者可以在你的博客上留下评论，这些评论会同时出现在你的博客和你的代码库的讨论页面上。

### 使用讨论区作为你的博客聊天系统的优势

* 它是完全免费的
* 没有广告或跟踪
* 它超级强大
* 你对评论有完全的控制权和完全的修改权。
* 有很多主题
* 它是相当可自定义的
* 你可以在你自己的服务器上自行托管

请记住，此工具主要适用于开发者博客，因为大多数开发人员使用 GitHub。

### 如何在你的博客中整合giscus

#### 先决条件

* 一个博客（你必须能够获得源代码）
* 一个 GitHub 帐户
* 你选择的代码库必须是公开的

首先，你需要为你的代码库启用讨论功能。

转到代码库 `Settings`-> 在 `Features`部分下 -> 勾选 `Discussions`框。
![img](https://picstorage.danielniu.me/imgs/8b8814e3fa45476fb4d6568951fbdc40.png)
接下来，在你的代码库中安装giscus应用程序。
转到 [giscus主页](https://github.com/apps/giscus)，按照提示操作，并仅授予对选定代码库的访问权限。![img](https://picstorage.danielniu.me/imgs/f15fd586e4cd4f4b82dc7db826d12a48.png)
现在是重要的部分：我们需要配置giscus小部件。

首先，进入giscus主页，滚动到 `Configuration`部分。

选择您的小部件语言，这是您想要显示小部件的语言。
![img](https://picstorage.danielniu.me/imgs/3b9ff0ea2bef46558b9d364bb0642af5.png)
然后输入你的代码库名称和你的用户名，如用 `username/reponame`。![](https://picstorage.danielniu.me/imgs/4d4469acb1634b51a6b4633ec5454206.png)
对于页面↔️讨论映射，我建议选择 “讨论标题包含页面 `URL`”。但根据你的需要，选择最适合你的那一个。
![](https://picstorage.danielniu.me/imgs/cc13493061bd436b94e79b63e4279b6a.png)
接下来，在你的GitHub 代码库上的讨论页面创建一个类别——比如 “Comments（评论）”——或者选择现有的类别。
![](https://picstorage.danielniu.me/imgs/92d114d08dfb4e9b9594b17bb95d9702.png)
![](https://picstorage.danielniu.me/imgs/8797a751ea66497da47e68e1260c4b1a.png)然后根据需要启用可选功能。

接下来，选择主题。不要担心，你可以通过编程来切换不同的主题。

最后，复制并粘贴生成的代码。

Giscus将根据你的设置生成一个脚本标签，你可以将其粘贴到你的代码中。
