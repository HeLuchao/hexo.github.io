---
title: uni-app框架开发h5以及移动端APP
toc: true
mathjax: true
comments: true
date: 2019-02-27 15:41:58
updated: 2019-02-27 15:41:58
photos:
tags: [移动端,APP,uni-app]
categories: [移动端,APP,uni-app]
---

# uni-app框架开发h5以及移动端APP

## 1.简介
```
uni-app框架是集合了vue.js以及微信小程序等语法的一款跨平台框架，编写一套代码，可编译到的iOS，安卓，H5，小程序等多个平台。
```
[uni-app官网](https://uniapp.dcloud.io/README)
## 2.uni-app对于npm是支持的，也就是说可以通过npm集成使用第三方的库
```
npm install packageName --save
```
## 3.uni-app 打包APP莫名找不到manifest.json文件解决办法：
```
1.查看报错信息（一般没有什么有用信息）
2.下载手机模拟器、安装Android Studio 模拟器
3.打开HbuilderX代码运行到手机模拟器，中途会出现报错信息，一个个解决掉，直至运行成功
4.大部分原因是敲代码过程中不符合jslint、eslint语法的问题
```
## 4.微信小程序转uni-app
```
通过小程序代码转uni-app非常方便，直接复制粘贴改成uni-app语法代码，即可成功运行，中途多看报错信息一步步改正即可，如果遇到复杂的问题请去uni-app官网或者官方论坛寻找答案
```
## 5.安装

1. git clone https://git.dev.tencent.com/chaochao940215/h5_PrimaryDoctor.git
2. 下载开发工具HbuilderX，打开代码，运行至浏览器

## 6.使用

[帮助文档](https://uniapp.dcloud.io/README)

[开发者社区](https://ask.dcloud.net.cn/explore/)

## 7.开发、运行
```
通过HbuilderX可运行到浏览器、手机模拟器、打包成移动APP等
```
打开 [HbuilderX](https://www.dcloud.io/hbuilderx.html)。