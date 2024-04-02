---
title: 基于quatrus的verilog学习
toc: true
top: 0
date: 2024-03-28 13:42:53
tags: [环境配置,vscode,破解软件,verilog,quartus,modelsim]
---

> quartus是一个配置麻烦的硬件编程平台，本文包括安装配置到常见问题解答，环境优化。

<!-- more -->

# quatrus安装以及modelsim配置

1. quatrus 不操作
2. `modism.exe `的文件夹加入到path
3. `modism`文件夹下，`win64`下 `LISCENSE.TXT` 加入到 `path（user）`

`tools->options->general->eda tools` 中设置`modelsim`路径`D:\Program\modeltech64_10.4\win64`（exe路径文件夹）

# 常见问题解决以及优化

## 设置编译器件库位置（新项目都需要）

同时也解决了  Quartus Prime18.0 中解决仿真报错` Error: (vsim-19) Failed to access library` 的问题

1. 点击`Tools->Launch Simulation Library Compile`;
2. 设置`“Output directory"`为：`{项目文件夹}/simulation/qsim`，在进行编译,如此设置以后，波形图`simulation->simulation settings`中的路径直接默认就行

> （主要是这里编译的器件库路径要匹配波形图`simulation->simulation settings`中的路径）

## 联合vscode开发

点击`tools`中的`options`，点击其中的 `preferred text editor`，在 `textx editor`栏中选择`custom`，在`command-line`中添加如下的信息`"E:\Microsoft VS Code\Code.exe" -r -g %f:%l`
