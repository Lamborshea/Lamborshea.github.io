---
disqusIdentifier: dfjosdjfsdjf
title: 添加系统变量，让 Git Bash 能够运行 PHP 和 Composer 命令
date: 2017-04-15 12:17:25
tags:
  - composer
  - gitbash
  - 开发工具
clearReading: true
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
categories:
  - PHP
  - 开发工具
keywords:
  - composer安装
  - composer全局变量
  - PHP
comments: true
meta: true
actions: true
---
<!-- toc -->

  假设你已经安装了 [ Git Bash ]( https://git-for-windows.github.io/  ) , 并想使用Git Bash 来运行 PHP 和 Composer 指令，而不是Windows 自带的 CMD
<!-- more -->


### 下载 [ Composer ]( https://getcomposer.org/download/  ) 和 [ PHP ]( http://php.net/downloads.php ) 或者 [WAMP]( http://www.wampserver.com/en/  )

安装 Composer 的时候可能会遇到网络请求无法完成的情形，一直卡在安装那里，可以尝试重新运行安装程序，并在其中一个步骤中添加代理
> 比如我的番茄代理是： ` http://127.0.0.1:1080 `

### 找到并拷贝 Composer 和 PHP 运行程序所在的文件目录
> 比如我的是： ` C:\wamp64\bin\php\php5.6.25 ` 和 `C:\ProgramData\ComposerSetup\bin `

### 修改系统变量的路径
> 我的电脑 --》 系统属性 --》 系统信息 --》 高级系统设置 --》环境变量 --》 系统变量
> 修改变量名为 ` PATH `，值为 ` C:\wamp64\bin\php\php5.6.25;C:\ProgramData\ComposerSetup\bin `
> 注意有分号 ` ; `

### 在 Git Bash 中测试是否成功
> ` php -v `
> ` composer -V `


### 使用 [ Packagist ]( http://www.phpcomposer.com/  ) 中国全量镜像
