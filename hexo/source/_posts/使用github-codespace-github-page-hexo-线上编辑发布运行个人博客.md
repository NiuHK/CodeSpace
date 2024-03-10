---
title: 使用github codespace + github page + hexo 无服务器发布运行个人博客
date: 2024-03-09 03:14:43
toc: true
tags:
---

hexo是一个可以github page 托管的静态页面博客框架，需要node.js进行编译发布，鉴于windows配置node.js的不变性，使用github codespace托管运行环境以及博客源码，进行无服务器博客运营。

<!-- more -->

icarus 主题 整体颜色改变：
/node_modules/hexo-theme-icarus/include/style/base.styl
l15 $primary ?= hsl(30, 100%,  50%)
