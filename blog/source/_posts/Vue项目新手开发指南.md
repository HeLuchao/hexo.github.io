---
title: Vue项目新手开发指南资源
date: 2019-01-30 18:34:19
tags: [Vue, VueCli, VueRouter,资源]
categories: Vue
---

### 1.用vue-cli2.0搭建项目框架
```
# 全局安装 vue-cli
$ npm install --global vue-cli
# 创建一个基于 webpack 模板的新项目
$ vue init webpack my-project
# 安装依赖，走你
$ cd my-project
$ npm run dev
```

### 2.按需引入安装需要的UI库（elementUI）
### 3.添加vue-router、vuex、axios
### 4.关于Vue跨域处理（proxy代理）
```
config===>index===>
后端：Allow-Origin-Acess-contrtol：*
设置 withCredentials = true 也是需要服务器支持的，这个选项的作用是跨域的情况接收服务器response的set-cookies，当启用这个选项的时候，服务器不能设置 Access-Control-Allow-Origin 为 *，如果是nginx可以使用$http_origin，否则写成你真实请求的origin地址
vue模板里直接使用 config 中的 proxyTable(proxyMiddleware) 里的 changeOrigin: true 来跨域
```

### 5.Vue2.0兼容IE以及其他浏览器
```
兼容IE：index.html中添加：
<meta http-equiv="X-UA-Compatible" content="IE=edge">
1.安装npm install babel-polyfill --save-g
2.main.js 中 引入 babel-polyfill 对象：
import 'babel-polyfill'
3.webpack.base.conf.js中配置
entry: {
  app: ['babel-polyfill','./src/main.js']
},
```

### 6.vue 代码部署到服务器上
第一步：npm run build
第二步：config==>index==>assetsPublicPath: '/dist/',//打包到服务器上的根路径
第三步：router==>index==>base: '/dist/'//服务器路径
第四步：为了避免一刷新就报400 或500 服务器需要配置相应路由
传送门：https://router.vuejs.org/zh-cn/essentials/history-mode.html
https://segmentfault.com/a/1190000012675012
部署到服务器上打开白屏处理https://blog.csdn.net/cuiji4724/article/details/81081027


### 7.解决服务器上一刷新就报404或500的错
参考：
https://router.vuejs.org/zh-cn/essentials/history-mode.html
https://segmentfault.com/a/1190000012675012

### 8.关于Vue解决安卓不兼容的问题
https://blog.csdn.net/lvlemo/article/details/79715696
### 9.vue项目打包后图片等静态资源路径错误问题
```
build==>utils==>publicPath:'../../',
```

### 10.vue解决移动端单位换算兼容处理
https://blog.csdn.net/yanzhi_2016/article/details/80461951
https://blog.csdn.net/qq_33485463/article/details/80454326
https://blog.csdn.net/z1712636234/article/details/77881685
https://blog.csdn.net/dodan/article/details/80033454

### 11.vue开发移动端不同机型的兼容性问题
https://juejin.im/post/5b6503dee51d45191e0d30d2?utm_source=gold_browser_extension

### 12.整体项目性能优化，三个方面：
```
npm run build --report		查看项目体积
1.路由懒加载
2.element-ui组件按需加载
3.使用 CDN 外部加载资源
4.开启Gzip
```
https://juejin.im/post/5ae2cb0ef265da0b767d32a0
https://www.cnblogs.com/fayin/p/7109690.html

### 13.vue好用的下拉刷新、上拉加载组件
better-scrollhttps://www.imooc.com/article/18232

### 14.vue实现骨架屏（首页加载延迟时的占位布局）
https://blog.csdn.net/u012878818/article/details/81216272（推荐）
https://github.com/ElemeFE/page-skeleton-webpack-plugin（推荐）
https://github.com/xunleif2e/vue-lazy-component（推荐）
https://blog.csdn.net/ly124100427/article/details/81168908
https://segmentfault.com/a/1190000014963269
https://segmentfault.com/a/1190000014832185
https://www.imooc.com/article/46327

### 15.vue移动端框架
https://didi.github.io/cube-ui/#/zh-CN
http://mint-ui.github.io/#!/zh-cn
https://youzan.github.io/vant/#/zh-CN/intro

### 16.Vue搜索关键词高亮
https://blog.csdn.net/qq_25403957/article/details/81111437

### 17.Vue吸顶导航
https://juejin.im/post/5b7a9deff265da43635d8067

### 18.vue 动态路由
https://refined-x.com/2017/09/01/%E7%94%A8addRoutes%E5%AE%9E%E7%8E%B0%E5%8A%A8%E6%80%81%E8%B7%AF%E7%94%B1/

### 19.vue后台权限控制
http://www.cnblogs.com/ssh-007/p/10295575.html?utm_source=gold_browser_extension
https://refined-x.com/2017/11/28/Vue2.0%E7%94%A8%E6%88%B7%E6%9D%83%E9%99%90%E6%8E%A7%E5%88%B6%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88/
https://refined-
x.com/2017/08/29/%E5%9F%BA%E4%BA%8EVue%E5%AE%9E%E7%8E%B0%E5%90%8E%E5%8F%B0%E7%B3%BB%E7%BB%9F%E6%9D%83%E9%99%90%E6%8E%A7%E5%88%B6/

### 20.Vue工程打包优化
https://juejin.im/post/5a291092518825293b50366d
https://juejin.im/post/5b49b8cce51d4519575a08e6
https://juejin.im/post/5b35f7d36fb9a00e6a621fc6
https://juejin.im/post/5a337a1f6fb9a0452b4949e0
https://github.com/kaola-fed/blog/issues/204
https://juejin.im/post/5b7f7d886fb9a01a1e0203cb?utm_source=gold_browser_extension
https://juejin.im/post/5a3251ee6fb9a0450f21f6ac
Vue SPA 项目webpack打包优化指南
https://juejin.im/post/5bd2b60e6fb9a05d27794c5e?utm_source=gold_browser_extension

### 21.Vue中的视频播放组件
https://github.com/surmon-china/vue-video-player

### 22.Vue组件资源汇总
https://juejin.im/entry/58bf745fa22b9d0058895a58
https://github.com/opendigg/awesome-github-vue

### 23.vue2.0做移动端开发用到的相关插件和经验总结
https://juejin.im/post/5b80f4e36fb9a019ce148fe9?utm_source=gold_browser_extension

### 24.Vue相关的技术资料
《Vue技术内幕》、《Vue.js 技术揭秘》《剖析 Vue.js 内部运行机制》

### 25.vue单页 使用keep-alive页面返回不刷新
https://blog.csdn.net/leileibrother/article/details/79376502

### 26.Vue 项目里戳中你痛点的问题及解决办法
https://juejin.im/post/5b174de8f265da6e410e0b4e

### 27.vue-vantUI-axios 移动端项目，rem做适配
https://javascript.ctolib.com/wqb2017-vue-vant-axios.html

### 28.Vue打包报错:Cannot read property 'thisCompilation' of undefined
https://blog.csdn.net/qq_34672907/article/details/80137609
https://segmentfault.com/q/1010000016321028
### 29.Vue移动端
http://yokiming.com/2017/10/19/Vue%E7%A7%BB%E5%8A%A8%E7%AB%AF%E5%BC%80%E5%8F%91%E7%9A%84%E9%82%A3%E4%BA%9B%E5%9D%91/

### 30.vue中使用第三方UI库的移动端rem适配方案
https://segmentfault.com/a/1190000015238394

### 31.Vue项目 ios 页面留白解决方案（尤其是webView）
https://blog.csdn.net/baozisss/article/details/81118386

### 32.Vue报错Cannot find module 'compression-webpack-plugin'
```
首先npm install --save compression-webpack-plugin
然后可能还会报错：vue Compression Plugin Invalid Options 
再然后去build->webpack.prod.conf->将asset改为filename
```

### 33.vue打包之后生成一个配置文件修改请求接口
https://www.cnblogs.com/adoctors/p/8472802.html
http://www.cnblogs.com/caimuqing/p/7094364.html

### 34.关于Vue开发移动端APP项目
https://www.jianshu.com/p/83f45d238630

### 35.用vue-cli3.x搭建项目框架
https://juejin.im/post/5c4a83e36fb9a049b13e91ba?utm_source=gold_browser_extension
https://juejin.im/post/5c4a6fcd518825469414e062?utm_source=gold_browser_extension
