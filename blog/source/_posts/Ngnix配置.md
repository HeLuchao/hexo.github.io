---
title: Nginx配置
toc: true
mathjax: true
comments: true
date: 2019-01-31 14:41:07
updated: 2019-01-31 14:41:07
photos:
tags: [Ngnix, 后端]
categories: 后端
---
# Nginx 配置大概分为以下几个步骤

###  一、在这里我前端vue项目使用vue cli脚手架进行搭建的，后台使用Nginx，首先是前端配置：

```　　
1.前端配置,在这里假如后端访问的时候要访问my-app文件夹下的打包好的dist文件夹，所以我们要在前端做一些配置
① 在vue.config.js文件中添加如下配置(在这里我们手动在src文件夹下面创建vue.config.js文件，相当于给webpack添加了新的配置)：
baseUrl:'/my-app/'
② router路由的配置(相信你知道这个配置应该放到哪吧，毕竟都已经到了发布的操作了)：
const router = new VueRouter({
    mode:"history",
    base:'/my-app/',
    routes
})
2.接下来就是我们前端的打包
① 因为在这里我使用的vue cli搭的项目，所以直接执行yarn build进行打包，你会发现多了个dist文件夹，这里面就是打包过后生成的文件
② 在这里简单解释下打包后js和css文件自动加了版本号的基本作用：可以进行版本回退，唯一标识。
③ 在这里我们模拟把打包好的文件夹交给后端，所以我将打包好的dist文件夹放到一个我创建好的文件夹nginx-root文件夹里面，并且放到my-app文件夹
```

### 二、接下来就是我们后端服务器Nginx的操作

```
1.第一步我们要先下载一个Nginx服务器，完全手把手，彻底手把手，不要九块九，更不要九十九，别太感动
① 去nginx.org下载一个Nginx，在右侧找到download点进去，在这里我们可以下载Stable version下面的nginx/Windows-1.14.1这个版本，
链接地址：http://nginx.org/en/download.html
②  然后将下载好的压缩包解压后放到你的本地磁盘里
③  给Nginx配置环境变量，相信大家应该都知道怎么配环境变量把，不知道怎么配环境变量可以私聊我，在这里就不做过多解释了，直接讲解下一步操作
2.开始Nginx的配置
① 在你的nginx(应该是nginx-1.14.1)文件夹中打开命令行，执行命令：start nginx
//开启nginx服务器，执行完该命令后，如果你的命令控制工具闪了一下，并且光标悬停一闪一闪放光芒，此时你就可以在你的浏览器上输入localhost，按下回车，如果出现了Welcome to nginx！，恭喜你，你已经成功开启nginx服务器的封印了
② 在编译器中，将你的nginx文件夹下找到conf文件夹，然后进入到nginx.conf文件，找到server，将server和括号里面的内容用#注释掉(注释的时候要小心，不能注释多也不能注释少，一定要精准，精准你懂吧)
③ 在conf文件夹下创建一个conf.d文件夹(该名字随意起)，在这里我们可以在conf.d文件夹下创建一个test.conf文件，在后期你可以创建多个.conf文件，来配置你的多个项目的server
④ 在nginx.conf文件中把这行代码在http括号里面找个地方放下，include后面跟的是你conf.d文件夹的绝对路径，这句代码的意思就是匹配下面所有的conf文件，这是我的，你把后面的路径改成你的就可以，注意要把斜杠改成反斜杠/
include D:/nginx-1.14.1/conf/conf.d/*.conf　　//这是我的，你把路径改成你的conf.d的绝对路径就可以，注意斜杠是'/'不是'\'
⑤ 在你的test.conf文件中添加配置信息，这是配置信息的解释，大家可以根据我的配置信息demo来配置你的

server { 
    listen 80;      ------端口号
    server_name localhost;      ------域名
    root 你的dist文件夹的绝对路径;     ------根       
    autoindex on;       ------将你匹配的文件自动匹配到index.html
    expires 1s;         ------缓存(只是为了演示才写的)
    charset utf-8;

    location /匹配路径{ 
        proxy_pass 接口反向代理的目标target;        ------在这里配置你的反向代理，若要配置多个代理路径，将此代码复制多个修改即可
    }       

    location / {
　　　　　　try_files $uri $uri/ /index.html;　　 ------这是从vue官网抄过来的配置，意义在于保证一旦我们的路由刷新的时候一旦后端找不到对应的路由，将自动跳转到index.html文件
    }   
}

- 我贴出来一个配置信息demo，大家可以根据这个demo来修改你的

server { 
    listen 80;      
    server_name localhost;      
    root E:/nginx-root/dist;          
    autoindex on;       
    charset utf-8;

    location /index/hotsShowList { 
        proxy_pass http://www.baidu.com;        
    }         

    location / {
        try_files $uri $uri/ /index.html;
    }   
}
6.最后，准备享受成功的喜悦
重启Nginx服务器，浏览器访问localhost:你的端口号，在这里我设置的是默认值80，你的可以随意
```

### 三、最后给大家做个小结，总结一下本地部署用到的一些命令
```
start nginx　　　　    //开启nginx服务
nginx -s stop　　　　//关闭nginx服务，(你可以关闭服务再重新开启服务来达到重启nginx服务的效果)
yarn build　　　　　//打包vue项目到dist文件夹下
```