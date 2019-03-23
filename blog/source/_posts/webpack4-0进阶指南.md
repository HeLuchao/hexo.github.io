---
title: webpack4.0进阶指南
toc: true
mathjax: true
comments: true
date: 2019-03-21 14:51:01
updated: 2019-03-21 14:51:01
photos:
tags: [wabpack,模块打包工具,前端开发工具]
categories: [webpack,前端]
---

# webpack4.0进阶指南

### 配置使用webpack
初始化package.json
npm init -y

-全局安装(不推荐)
```
 npm install webpack -g
```

-本地安装

```
 npm install webpack webpack-cli -D
```

-直接运行
```
npx webpack
```

## 配置webpack
—新建webpack.config.js
```
//遵循common.js
let path =require('path');

module.exports = {
    entry:'./src/index.js',//入口
    output:{
        filename:'build.js',
        path:path.resolve(__dirname,'build')
    },//出口
    devServer:{},//开发服务器
    module:{},//模块配置
    plugins:[],//插件配置
    mode:'development',//模式可更改
    resolve:{},//配置解析
}
```

### 配置开发服务器
```
npm install webpack-dev-server -D
```