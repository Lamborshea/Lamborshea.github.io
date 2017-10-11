---
title: hexo常用命令整理
date: 2017-07-29 10:36:03
tags: 命令
categories: hexo 博客
keywords: hexo 常用命令
comments: true
meta: true
actions: true
thumbnailImage: http://ono38scfe.bkt.clouddn.com/Image.jpg
thumbnailImagePosition: right
metaAlignment: center
coverImage: http://ono38scfe.bkt.clouddn.com/ridge.jpg
coverCaption: "A beautiful mountain ridge"
coverMeta: in
coverSize: full
gallery:
    - http://ono38scfe.bkt.clouddn.com/jump.jpg "New York jump"
    - http://ono38scfe.bkt.clouddn.com/stayhungrystayfoolish.jpg "fool"
    - http://ono38scfe.bkt.clouddn.com/chicago.jpg "chicago"
    - http://ono38scfe.bkt.clouddn.com/Image.jpg "sea and city"
---
<!-- toc -->

用了hexo博客有一段时间，想把常用的命令整理下来，这样以后写博客就会流程化一点，避免在查命令，查文档上花费太多时间。当然，用多了，自然就会记住的。
<!-- more -->
## 撰写
### 新建博客

```bash
hexo new "new post name"
```
## 部署提交
### 清除缓存

```bash
hexo clean
```
### 索引 algolia

```bash
hexo algolia
```
### 生成静态文件

```bash
hexo generate
该命令可以简写为：
hexo g
选项：
hexo g -d,--deploy  文件生成后立即部署网站
hexo g -w,--watch   监视文件变动
```
### 启动本地服务器

此时可以打开浏览器，输入 localhost:4000 进行本地预览
```bash
hexo server
该命令可以简写为：
hexo s
选项：
hexo s -p,--port    重设端口
hexo s -s,--static  只使用静态文件
hexo s -l,--log     启动日记记录，使用覆盖记录格式

```
### 部署到远程 Git 仓库

```bash
hexo deploy
该命令可以简写为：
hexo d
选项：
hexo d -g,--gernerate   部署之前预先生成静态文件
```

### Version
```bash
hexo version
```