---
layout: post
title: "ZIP刷机包加密和解密"
date: 2014-05-23 15:47:18 +0800
comments: true
categories: Android
---
最近下了一个ZIP刷机包发现居然不能解压缩，可是正常刷入却没有任何问题

<!-- more -->

研究了一下发现原来是采用了`ZipCenOp.jar`这个东西来加密和解密ZIP包的，而且只是一种伪加密方式


于是编写了一个脚本来快速加密和解密这种伪ZIP包


文件提供在这里,[点我下载](http://pan.baidu.com/s/1jGhyzIY)



![](/media/2014-05-23-cryptionzip/1.jpg)