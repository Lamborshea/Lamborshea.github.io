---
title: 中文网站增强阅读体验如何选择中文字体以及如何写 font-family
date: 2017-08-16 19:14:08
tags:
  - 字体
  - font-family
categories: CSS
keywords:
  - font
  - font-family
  - 中文网页字体
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
选择合适且美观的字体能很好地增强用户阅读体验，网页中的字体有西文，中文，以及在展示代码的时候会用到等宽字体。而且，不同的操作系统，默认的中文，英文字体都不一样。所以本文简要总结了前端开发中在CSS 的font-family 属性中如何进行字体的选择和顺序排列。
<!-- more -->
## 概述

西文字体分类两类，即"衬线体"（serif）与"非衬线体"（sans-serif）。衬线体在笔划上有过多的点缀（笔划末端的小三角,笔锋）很容易造成视觉疲劳（尤其是显示在屏幕上时），所以在中文网页中更倾向于使用无衬线字体（sans-serif）。

## CSS 的font-family 属性

```CSS
body{
  font-family: "Helvetica Neue",Verdana,PingFang SC, Microsoft Yahei, Hiragino Sans GB, Microsoft Sans Serif, WenQuanYi Micro Hei, sans-serif;
}
```

对于CSS 中字体的 Fallback 机制，font-family 的属性规范：
  1. 优先使用排在前面的字体。
  1. 如果找不到该种字体，或者该种字体不包括所要渲染的文字，则使用下一种字体
  1. 如果所列出的字体，都无法满足需要，则让操作系统自行决定使用哪种字体


因此在写CSS 样式属性的时候应注意：
  1. 中文字体包含了英文字母，当大多数并不美观。因此 font-family 应该优先指定英文字体，然后再指定中文字体。
  1. 使用逗号分割每个值，并始终提供一个类族名称作为最后的选择。
  1. 多个单词组成的英文名称，应该放在双引号内

## 不同平台上支持的字体

首先，好看的英文字体非常多，所以网页中的英文字体有很大的选择空间。
### mac OS
#### 英文

- Helvetica：小写字母比较大，被评为设计师最爱的字体,  被大量使用于企业 Logo 上。
- Helvetica Neue： 为 Helvetica 的改善版本，且增加了更多不同粗细与宽度的字形，公拥有51种字体版本。
- Lucida Grande：Lucida Grande 是一种西文无衬线字体，是苹果公司操作系统 Mac OS X 9 以及之前版本的系统默认西文字体

#### 中文

- 苹方（PingFang SC）：OS X 10.11 El Capitan 默认字体开始改为威锋数位制作的「苹方-简」
- 冬青黑/苹果丽黑（Hiragino Sans GB）：OS X 10.6 开始，系统自带了冬青黑体简体中文。目前 OS X 上最好的简体中文字体。
- 华文黑体（ST Heiti）：截至 OS X 10.5 Leopard 的字体是常州华文制作的「华文细黑」
- 华文细黑：STHeiti Light （又名STXihei）
- 华文黑体：STHeiti
- 华文楷体：STKaiti
- 华文宋体：STSong
- 华文仿宋：STFangsong

#### 等宽字体 monospace

- Courier
- Lucida Console
## Windows

只列举一些在网页显示起来好看的字体。
### 中文

- 微软雅黑（Microsoft YaHei）：Windows 默认中文字体。开了clearType 之后挺好看的。它在Mac平台的对应字体是华文细黑（STXihei）
- 宋体／中易宋体（SimSun）：宋体在中文网页中还不算难看。
- 黑体（SimHei）：黑体有点粗，谨慎使用吧。
- 新宋体（NSimSun）：还挺不错的的一款字体。
- 仿宋：FangSong
- 楷体：KaiTi
- 仿宋GB2312：FangSongGB2312
- 楷体GB2312：KaiTiGB2312
### 英文

- Tahoma
- Lucida Sans Unicode

## 等宽字体 monospace

- Courier New
- Lucida Console
## 互联网安全字体

互联网安全字体，就是大多数系统都安装了的字体。中文的安全字体不多，而且存在很多不确定因素，比如，在 mac OS 系统上安装了 Microsoft office 软件，office 会在 mac OS 系统安装一些 Windows 常见的中文字体，例如，微软雅黑，黑体，宋体等等。所以下面列举西文的互联网安全字体。

- verdana
> 无衬线字体，优点在于它在小字上仍结构清晰端整、阅读辨识容易。几乎在所有平台上都预装了，所以是 sans-serif 字体的第一选择。它的特点就是字母间距比较宽，字母本身的宽度也比较大，所以比较容易阅读。

- Arial
> 无衬线字体，Helvetica 的「克隆」，和 Helvetica 非常像，细节上比如R和G有小小差别。如果字号太小，文字太多，看起来会有些累眼。Win和 Mac 显示都正常，也是 humanist 风格，字体和 Verdana 有点像，但是略窄一些，counter 略小，曾经是 Windows 的标准字体，Mac 10.5 之后默认也有安装。有一个不好地方在于小写的L和大写的i不容易分清。

- Arial Black
- Comic Sans MS
- Courier New
> 等宽字体，常用来显示代码

- Georgia
> 基本上适合正文屏显的衬线字体，非 Georgia 莫属了。笔画粗重，衬线明线，轮廓较大，小字体显示也很清晰，同时细节还算OK。

- Impact
- Times New Roman
> 在字体设计上属于过渡型衬线，迄今仍广泛使用在图书、杂志、报告、公文、广告、荧幕显示。

- Trebuchet MS
>为微软设计的一个 humanist 风格字体，个人觉得个性太过突出，用得不好会不搭。


## 引入外部 Web 字体文件(EOT, TTF/OTF, WOFF, WOFF2, SVG)

中文字体的网页开发有着极大的局限性。因为，一套中文字体最少也要有几千个字符，体积为几个 MB；所以，从技术，用户体验，性能优化的角度权衡，不建议加载外部 Web 字体文件。

## 常用 font-family 写法
### 英文与简体中文的 font-family 无衬线字体 CSS 写法(sans-serif)：

```CSS
body {
  font-family: -apple-system, BlinkMacSystemFont,Verdana, "Helvetica Neue", Helvetica,"PingFang SC","Lantinghei SC", "Microsoft Yahei","Hiragino Sans GB", "Microsoft Sans Serif", "WenQuanYi Micro Hei", sans-serif;
}
```
### 英文与简体中文的 font-family 衬线字体 CSS 写法(serif)：
```CSS
body {
  font-family: Palatino, Optima, Georgia,serif;
}
```

### 等宽字体 CSS 写法

```CSS
pre,
code,
kbd,
samp,
tt {
  font-family: Courier, 'Courier New','Lucida Console', monospace;
}
```

## 常见字体的中文名和英文名对照

|   中文名     |   英文名     |
|   :-------:   |   :------:    |   
|    苹方       |  PingFang SC     |
|    冬青黑/苹果丽黑         |   Hiragino Sans GB    |
|    思源黑体         |    Source Han Sans CN     |
|    华文黑体         |     ST Heiti          |
|    华文细黑        |     STHeiti Light [STXihei]  |
|    宋体            |       SimSun          |
|    新宋体          |     NSimSun          |
|    仿宋            |      FangSong        |
|    楷体            |     KaiTi            |
|    微软雅黑        |   Microsoft YaHei    |
|    文泉驿微米黑    |    Wenquanyi Micro Hei  |
|   文泉驿正黑       |   WenQuanYi Zen Hei   |
|   文泉驿点阵正黑   |   文泉驿点阵正黑      |

## 参考链接

1. [MacOS字体列表](https://www.wikiwand.com/zh-hans/MacOS%E5%AD%97%E4%BD%93%E5%88%97%E8%A1%A8)
1. [Microsoft_Windows字體列表](https://www.wikiwand.com/zh/Microsoft_Windows%E5%AD%97%E9%AB%94%E5%88%97%E8%A1%A8)
1. [如何保证网页的字体在各平台都尽量显示为最高质量的黑体？](https://www.zhihu.com/question/19911793)
1. [中文网页用什么字体最合适？](https://www.zhihu.com/question/20404847)
