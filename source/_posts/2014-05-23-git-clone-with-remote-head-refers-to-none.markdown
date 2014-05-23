---
layout: post
title: "git clone拉代码时提示warning: remote HEAD refers to none"
date: 2014-05-23 16:02:54 +0800
comments: true
categories: Android
---
今天git clone我自己的代码的时候，<!-- more -->在完成时提示`warning: remote HEAD refers to nonexistent ref, unable to checkout！`

百度了一下大意就是没有发现默认的HEAD文件，换言之没有找到可用分支。

于是我在最后同步命令加上了`"-b cm-10.1"`再次clone，错误消失了。

遇到这种错误可以尝试加上`"-b xxx"`xxx代表需要clone的分支，即可解决！
