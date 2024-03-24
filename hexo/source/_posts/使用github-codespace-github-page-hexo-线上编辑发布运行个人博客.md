---
title: 使用github codespace + github page + hexo 无服务器发布运行个人博客
date: 2024-03-09 03:14:43
toc: true
tags: [Icarus,blog,codespace,hexo]
top: 1
---

> hexo是一个可以github page 托管的静态页面博客框架，需要node.js进行编译发布，鉴于windows配置node.js的不变性，使用github codespace托管运行环境以及博客源码，进行无服务器博客运营。

<!-- more -->

icarus 主题 整体颜色改变：
/node_modules/hexo-theme-icarus/include/style/base.styl
l15 $primary ?= hsl(30, 100%,  50%)


[更改两栏布局下文章宽度](http://zhaommmmomo.cn/2021/09/14/Icarus%E4%B8%BB%E9%A2%98%E7%9A%84%E4%B8%80%E4%BA%9B%E5%B8%B8%E7%94%A8%E9%85%8D%E7%BD%AE/)

[部分更改](https://hujiahao6.gitee.io/2020/04/02/hexo%E7%9A%84%E4%B8%80%E4%BA%9B%E9%85%8D%E7%BD%AE%E9%97%AE%E9%A2%98/)


调整背景透明度
themes\icarus\source\js\animation.js
L44

https://blog.mchook.cn/2021/07/22/icarus%E4%B8%BB%E9%A2%98%E8%87%AA%E5%AE%9A%E4%B9%89/
https://blog.pk5ls20.com/posts/111d57cd/#span-%E8%83%8C%E6%99%AF%E5%9B%BE%E5%85%A8%E5%B1%8F%E5%8C%96-%E6%AF%9B%E7%8E%BB%E7%92%83%E6%95%88%E6%9E%9C-span


我使用的布局：.is-3-colum


可以在Markdown文件中使用下面的语法来折叠单独的代码块：
```
{% codeblock "可选文件名" lang:代码语言 >folded %}
...代码块内容...
{% endcodeblock %}
```