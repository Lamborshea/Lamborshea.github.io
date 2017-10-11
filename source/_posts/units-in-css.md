---
title: 深入浅出CSS 中的单位：em,rem,px,vh,ex
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
date: 2017-08-09 14:27:19
tags:
  - 单位
categories:
  - 前端
  - CSS
keywords:
comments: true
meta: true
actions: true
---
<!-- toc -->

在网页设计当中，在给字体，或者元素赋予大小，长度，宽度的时候，我们经常需要考虑到使用哪种单位（px,em,rem,pt,vh）最合适。
在不同的布局方式，不同的组件设计中，可能会采用不止一种单位。
<!-- more -->
## px
```css
p {
  font-size: 14px;
}
```
px 像素，是一个虚拟长度单位，是计算机系统的数字化长度单位，如果px要换算成物理长度，需要制定精度 DPI（Dots Per Inch，每英寸像素数），在扫描打印时一般都有 DPI 可选。Windows 系统默认是9 6dpi，Apple 系统默认是 72dpi。

但是在 CSS 中，px 其实并不是实际意义上的像素单位，也就是说，并不是屏幕上 1920*1080 那每一个像素排列出来的像素。我更倾向于叫像素点，在手机端浏览器的网页设计中最容易看出来，现在的大多数手机的分辨率都可以达到1920x1080，苹果手机的 retina 屏更是一个物理像素点，有两个色彩像素。

所以，浏览器的 window 对象有一个设备物理像素和设备独立像素的比例，叫做 devicePixelRatio = 物理像素/独立像素。不管是安卓，苹果还是 PC 端的高清屏幕，devicePixelRatio 都不一定相同。

参考链接：[移动前端开发之viewport的深入理解](https://www.cnblogs.com/2050/p/3877280.html)
## em
em 指字体高，是相对单位，相对于父级的字体单位。

任意浏览器的默认字体高都是16px，也就是：1em=16px,0.75em=12px,0.625em=10px;

为了简化font-size的换算，需要在css中的body选择器忠声明Font-size=62.5%，这就使em的值变为16px*62.5%=10px，这样12px=1.2em，10px=1em，也就是说只需要将你的原来的px数值除以10，然后换上em作为单位就行了。
e.g.
```html
<div>
  <p></p>
</div>
```
```css
div {
  font-size: 1.2em; //19.2px;
}

p {
  font-size: 1.2em; //19.2*1.2=23.04px;
}
```

## rem
'r' 代表 'root'，等同于`font-size` 基于根元素（大多数情况下，根元素为 html 元素）设置的。

rem 对比 em 的好处就是，子元素的节点都是相对于根元素（html）的，不必担心相对单位的多重乘积的问题：
```html
<div>
  <p></p>
</div>
```
```css
div {
  font-size: 1.2rem; //16*1.2=19.2px;
}

p {
  font-size: 1.2rem; //16*1.2=19.2px;
}
```

rem 不是只对定义字体大小有用。比如，你可以使用 rem 把整个网格系统或者UI样式库基于 HTML 根元素的字体大小上,然后在特定的地方使用 em 比例缩放。这将带给你更加可预测的字体大小和比例缩放。

## vh 和 vw
vh 等于viewport高度的 1/100.例如，如果浏览器的高是900px,1vh求得的值为9px。同理，如果显示窗口宽度为 750px,1vw求得的值为7.5px。

做一个占满高度的或者接近占满高度的幻灯片，可以用一个非常简单的方法实现，只要用一行CSS：
```css
.slide {
    height: 100vh;
}
```
vh和vw总是与视口的高度和宽度有关，与之不同的，vmin和vmax是与这次宽度和高度的最大值或最小值有关，取决于哪个更大和更小。例如，如果浏览器设置为1100px宽、700px高，1vmin会是7px,1vmax为11px。然而，如果宽度设置为800px，高度设置为1080px，1vmin将会等于8px而1vmax将会是10.8px。

所以你什么时候可能用到这些值？

设想你需要一个总是在屏幕上可见的元素。使用高度和宽度设置为低于100的vmin值将可以实现这个效果。例如，一个正方形的元素总是至少接触屏幕的两条边可能是这样定义的：
```css
.box {
    height: 100vmin;
    width: 100vmin;
}
```
## ex 和 ch
ex 和 ch 单位，与 em 和 rem 相似，依赖于当前字体和字体大小。然而，与 em 和 rem 不同的是，这两个单位只也依赖于 font-family，因为它们被定为基于特殊字体的法案。

ch单位，或者字符单位被定义为0字符的宽度的“先进的尺寸”。在“Eric Meyer’s的博客”中可以找到一些非常有趣的讨论关于这意味着什么，但是基本的概念是，给定一个等宽字体的字体，一个N个字符单位宽的盒子，比如 width：40ch;,可以一直容纳一个有40个字符的应用那个特定字体的字符串。虽然这个特殊规则的传统用途与列出盲文有关，但是这里创造性的可行性一定会超越这些简单的用途。

ex单位被定义为”当前字体的x-height或者一个em的一半”。给定的字体的x-height是指那个字体的小写x的高度。通常，这是这个字体的中间的标志。

x-height:小写字母x的高度
e.g. 可以用到上标下标的标签中。
```css
sup {
  position: relative;
  top: -1ex;
}
```

参考链接：
1. [css中的px，em，rem](http://www.jianshu.com/p/75f7cbfd1c71)
2. [移动前端开发之viewport的深入理解](https://www.cnblogs.com/2050/p/3877280.html)
3. [七个你可能不了解的CSS单位](https://www.w3cplus.com/css/7-css-units-you-might-not-know-about.html)
