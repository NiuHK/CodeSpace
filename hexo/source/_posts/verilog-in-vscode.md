---
title: Verilog running in vscode
date: 2023-10-18 20:34:39
tags: [verilog,vscode,环境配置]
toc: true
top: 0
---

> 尝试在vscode跑Verilog，记录一下。
很久之前设置的，想到多少写多少吧：


<!-- more -->


## 一·添加的扩展：
![image](https://picstorage.danielniu.me/imgs/bafkreifgtz7lwnpkumdxikltrrfhdwjyrxrjnflovh3k2d7ark62i5r43y.png)
Verilog HDL：添加一个运行按钮，添加控制台输出（大概）

Verilog Snippet：关键词高亮补全（大概）

Verilog_Testbench：自动生成测试文件，用处不大。

Verilog-HDL/SystemVe：主要的，综合各个模块

![image](https://picstorage.danielniu.me/imgs/bafkreidt2dhxhqj4ilximdpergiswfm6lo4nebos6xwdtw5gvkqatvj2ea.png)

WaveTrace：波形显示
## 二·部分设置：
`"verilog.linting.linter": "iverilog"`

![image](https://picstorage.danielniu.me/imgs/bafkreiax4bffeap77a4xrwtvlgycfrktw346uxvuc44xcjrf7womhqqboi.png)
## 三·报错：
1.include 报错：
\`include "./my.v"找不到文件，使用相对绝对路径都不行：设置为：
`"verilog.linting.iverilog.runAtFileLocation": true`
![1](https://picstorage.danielniu.me/imgs/bafkreia36fe5f3wrka2dctmhyzffrtlu7o4ormvjqmeqeavrn27q27pvr4.png)