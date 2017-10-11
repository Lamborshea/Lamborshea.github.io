---
disqusIdentifier: coivuouux
title: vue-cli的安装和使用
date: 2017-04-15 09:44:26
tags:
  - Vue.js
  - Vue-cli
  - webpack
  - 开发工具
categories:
  - 前端
  - 开发工具
keywords:
- javascript
- hexo
comments: false
meta: true
actions: true
thumbnailImage: http://ono38scfe.bkt.clouddn.com/chicago.jpg
thumbnailImagePosition: right
coverImage: http://ono38scfe.bkt.clouddn.com/ridge.jpg
coverCaption: "A beautiful mountain ridge"
coverMeta: out
coverSize: partial
---
<!-- toc -->

vue-cli 是 Vue.js 官方提供的一个`命令行工具`,能够让开发者快速搭建大型单页项目，vue-cli 中提供了包括 browserify 和 webpack 的官方模板，只需要几分钟依赖包的下载时间便可以开始启动项目，通过配置，项目还能添加带热重载，保存时静态检查，能用于开发环境和生产环境。
<!-- more -->
##### 使用 [淘宝NPM镜像](https://npm.taobao.org/)
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
##### 全局安装 vue-cli
```
cnpm install -g vue-cli
```
##### 全局安装 webpack
```
cnpm install -g webpack
```
##### 通过查看 vue-cli 的版本号检查是否安装成功
```bash
vue -V    或者    vue --version
```

##### 初始化基于 Webpack 构建的 vue 项目
```bash
vue init webpack my-project    //执行完毕后，会有一些命令行交互，初始化一些信息。
```
![初始化后的界面](http://ono38scfe.bkt.clouddn.com/vue-cli-2.jpg)
##### 进入项目，安装项目的依赖
```bash
cd my-project
npm install    
```
目录会增加一个叫 node_modules 的 node 工具包目录
##### 本地启动项目
```bash
npm run dev   
```
成功之后就可以在浏览器中打开 <kbd>http://localhost:8080</kbd>  端口看到运行中的vue项目了
##### 编译生成用于生产环境的项目 dist 包
```bash
npm run build
```

![生成后Vue的默认页面](http://ono38scfe.bkt.clouddn.com/vue-cli-1.png)
