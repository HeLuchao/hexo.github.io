---
title: 通用的Webpack多页面脚手架
toc: true
mathjax: true
comments: true
date: 2019-02-01 15:22:35
updated: 2019-02-01 15:22:35
photos:
tags: [打包工具,webpack,脚手架]
categories: webpack
---

# 通用的Webpack多页面脚手架

### 1.需要NodeJS环境、git环境
```
打开build/config.js文件根据自身要求进行自定义设置
const config = {
  projectPath,                                                      // 项目根目录
  srcPath: path.join(projectPath, './src/'),                        // 源文件目录
  node_modulesPath: path.join(projectPath, './node_modules/'),      // node_modules目录
  htmlPath: path.join(projectPath, './src/'),                       // HTML目录
  jsPath: './src/js/',                                              // JS目录
  ignoreJs: ['test'],                                               // 没有入口js文件的html名
  assetsSubDirectory: path.join(projectPath, './src/static'),       // 静态资源目录(不处理的第三方代码)

  dev: {
    host: 'localhost',
    port: '3002',
    devSourceMap: false, // 是否开启SourceMap
    devtool: 'eval-source-map',
    assetsPublicPath: '/',// 相对于服务器根目录的路径，用于加载资源。
    proxyTable: { // proxy代理
      "/api": "http://localhost:3000"
    },
  },
  build: {
    prodSourceMap: false, // 是否开启SourcMap
    devtool: 'source-map',
    assetsRoot: path.resolve(__dirname, '../dist'),  // 构建根目录
    assetsPublicPath: '/',  // 相对于服务器根目录的路径，用于加载资源。
  },
};

```

### 2.npm run build 构建dist生产目录
### 3.npm run dev 构建热更新服务
### 4.开始进行开发
