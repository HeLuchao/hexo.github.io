---
title: VuePress+GitHubPages构建技术博客
toc: true
mathjax: true
comments: true
date: 2019-02-01 13:44:20
updated: 2019-02-01 13:44:20
photos:
tags: [npm, VuePress, github]
categories: 搭建博客
---
# 使用VuePress+GitHubPages构建技术博客大致分为以下几个步骤：

## 1.安装依赖
```
npm install -g vuepress
```
### 创建一个 markdown 文件
```
echo '# Hello VuePress' > README.md
```
### 开始编写文档
```
vuepress dev
```
### 构建
```
vuepress build
```
## 2.在已有项目中安装
### 安装为本地依赖项
```
npm install -D vuepress
```
### 创建一个 docs 目录
```
mkdir docs
```
### 创建一个 markdown 文件
```
echo '# Hello VuePress' > docs/README.md
```
### 开始编写文档
```
npx vuepress dev docs
```
## 3.新建GitHub仓库，可随意命名，添加READYME文件
## 4.git clone 远程仓库
## 5.新建git 分支gh-pages,命令行依次输入以下命令：
```
git branch gh-pages  //创建本地分支
git checkout gh-pages	//切换本地分支
git push origin gh-pages  //本地分支push到服务器上
```

## 6.npm init 内容设置随意

## 7.给 package.json 添加一些 scripts 脚本：
```
{
  "scripts": {
    "docs:dev": "vuepress dev docs",
    "docs:build": "vuepress build docs"
  }
}
```

## 8.配置
```
首先需要在文档目录中创建一个.vuepress目录。
VuePress站点的基本文件是.vuepress/config.js
```

## 9.部署到GitHub的页面
```
1）将.vuepress/config.js中的base设置为你的仓库名称。
例如，如果你的仓库是https://github.com/foo/bar，部署则已页面的将在https://foo.github.io/bar上可用。在这种情况下，应该你将base设置为"/bar/"。
2）创建一键部署命令行文件deploy.sh
/usr/bin/env sh

确保脚本抛出遇到的错误
set -e

生成静态文件
npm run docs:build

进入生成的文件夹
cd docs/.vuepress/dist

如果是发布到自定义域名
echo 'www.example.com' > CNAME

git init
git add -A
git commit -m 'deploy'

如果发布到 https://username.github.io  USERNAME=你的用户名
git push -f git@github.com:/username/blog.git master:master

如果发布到 https://github.com/username/blog  REPO=github上的项目
git push -f git@github.com:username/blog.git master:gh-pages

cd -
```
## 10.可能会碰到的git 问题：permission denied
https://blog.csdn.net/xxzhangx/article/details/52951592


