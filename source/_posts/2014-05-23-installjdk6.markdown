---
layout: post
title: " Android开发环境搭建之sun-java6-jdk"
date: 2014-05-23 15:07:16 +0800
comments: true
categories: Android
---
* 现在的Ubuntu源默认已经没有sun-java6的安装包了
* 所以需要手动下载来安装

<!-- more -->
* 方法如下：
* 适用于64位Linux

1、下载`jdk-6u45-linux-x64.bin`：

[点我下载](http://pan.baidu.com/s/11MLHE)

2、将下载下来的文件放在任意位置，然后输入：
```
sudo chmod 777 jdk-6u45-linux-x64.bin
./jdk-6u45-linux-x64.bin
```
   只要下载的jdk安装包没有损坏就能正常解压，最后会有`Done!`的提示

3、接下来进入`jdk-6u45-linux-x64`目录，将里面的`bin`目录加入环境变量即可

4、执行`java -version`查看是否安装成功