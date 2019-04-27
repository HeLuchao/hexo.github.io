---
title: 关于多人开发项目以及CI、CD的一点感想
toc: true
mathjax: true
comments: true
date: 2019-04-27 16:13:32
updated: 2019-04-27 16:13:32
photos:
tags: [项目开发,CI,CD]
categories: [项目开发,CI,CD]
---

# 关于多人协作开发一个项目的思考：

```
从最开始接手一个项目到需求上线之间一定要有以下几步:
1.一个项目工程新建远程仓库之后会有个默认分支master作为测试环境
2.需要新建分支release分支作为生产环境
3.项目组成员之间的开发配合需要基于release分支新建自己的开发分支
4.功能开发完成之后需要自测通过后合并分支到master测试分支
5.测试QA通过后再合并至release分支提交上线
6.大公司可能还会有一个预发布的环境分支存在staging，视公司情况而定

多人项目（包含前后端不分离项目以及前后分离项目）本地开发调试流程
首先必须保证跟后端处于同一开发分支，处于同一开发环境才能进行联调
接到新需求拉完项目代码首先创建自己的开发分支(基于release分支)
需求提交上线之前，需要先把线上代码合到需要上线的分支保持代码为最新，提交合并线上环境代码请求，通知测试盖章，合并通过上线。

```


# 关于CI、CD：

```
CI/CD 为持续集成、持续交付的情况，可以基于GitLab、Jenkins等代码仓库构建自动部署工具。
快速合并分支打包上线之后一键部署到线上生产环境，完全不影响用户使用，做到平滑过渡的效果，实现应用开发的持续自动化和持续监控。

参考下面的链接:
````
什么是 CI/CD?
https://juejin.im/post/5cb134b96fb9a0688777c54c

基于GitLab自动部署:
https://juejin.im/post/5cb9204be51d456e541b4ccd?utm_source=gold_browser_extension

使用 Jenkins + Ansible 实现自动化部署 Nginx:
https://juejin.im/post/5cc2356cf265da037b61169d?utm_source=gold_browser_extension





