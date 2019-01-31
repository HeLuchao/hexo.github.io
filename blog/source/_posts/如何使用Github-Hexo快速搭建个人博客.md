---
title: 如何使用Github+Hexo快速搭建个人博客
date: 2019-01-28 15:29:32
comments: true
tags: [npm, hexo, github]
categories: 搭建博客
---
### 第一步：使用 npm 安装 Hexo
```
npm install -g hexo-cli
```

### 第二步：指定一个空目录初始化hexo所需文件
```
hexo init 目录名(要求是空目录)
新建完成后，生成如下目录文件：
node_modules
package-lock.json
package.json
scaffolds
source
themes
_config.yml
```

### 第三步：进入hexo项目目录中，使用如下命令开启博客服务：
```
hexo s
进入浏览器访问http://localhost:4000/

```

### 使用Hexo写文章

```
在项目目录下使用如下命令可以创建新的文章
hexo new [layout] <title>
Hexo 有三种默认布局：post、page 和 draft
Hexo 默认以标题做为文件名称
```

### 新建草稿
```
刚刚提到了 Hexo 的一种特殊布局：draft，这种布局在建立时会被保存到 source/_drafts 文件夹，您可通过 publish 命令将草稿移动到 source/_posts 文件夹，该命令的使用方式与 new 十分类似，您也可在命令中指定 layout 来指定布局。
hexo publish [layout] <title>
草稿默认不会显示在页面中，您可在执行时加上 --draft 参数，或是把 render_drafts 参数设为 true 来预览草稿。
我们把配置参数设置一下: render_drafts.
#render_drafts: false
render_drafts: true

```

### 新建模板
```
在新建文章时，Hexo 会根据 scaffolds 文件夹内相对应的文件来建立文件
hexo new photo "My Gallery"

```

### 导入文章
```
您可以将已写好的 .md 导入到 _posts 目录里，完成文章的导入。
```


### 部署到服务器

```
Hexo 提供了快速方便的一键部署功能
hexo deploy

1.在开始之前，您必须先在 _config.yml 中修改参数，一个正确的部署配置中至少要有 type 参数
deploy:
  type: git

您可同时使用多个 deployer，Hexo 会依照顺序执行每个 deployer:
deploy:
- type: git
  repo:
- type: heroku
  repo:

  deploy:
  type: git
  repo: <repository url> #https://bitbucket.org/JohnSmith/johnsmith.bitbucket.io
  branch: [branch] #published
  message: [message]

2.安装 hexo-deployer-git
npm install hexo-deployer-git --save

3.修改配置。

deploy:
  type: git
  repo: git@github.com:HeLuchao/hexo.github.io.git
  branch: master
  
4.生成站点文件并推送至远程库。
执行hexo clean 、hexo deploy命令。前者清除站点文件，后者重新生成站点文件并将之推送到指定的库分支。（如果您的Hexo是局部安装，则需要执行./node_modules/.bin/hexo clean && ./node_modules/.bin/hexo deploy。）

登入 Github/BitBucket/Gitlab，请在库设置（Repository Settings）中将默认分支设置为_config.yml配置中的分支名称。稍等片刻，您的站点就会显示在您的Github Pages中。
```

### Hexo 主题
```
您可以在 https://hexo.io/themes/index.html 进行主题的挑选更换。
下载好后放在themes文件夹内，同时在 _config.yml 中进行配置变更就好了。
```

### Linux作为后台服务启动
```
安装 pm2
npm  install -g pm2
博客根目录下面创建一个hexo_run.js：
const { exec } = require('child_process')
exec('hexo server',(error, stdout, stderr) => {
        if(error){
                console.log('exec error: ${error}')
                return
        }
        console.log('stdout: ${stdout}');
        console.log('stderr: ${stderr}');
})

根目录下执行：
pm2 start hexo_run.js
启动后台服务。
```

