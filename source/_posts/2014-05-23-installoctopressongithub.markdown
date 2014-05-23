---
layout: post
title: "在Github中搭建Octopress博客"
date: 2014-05-23 11:10:42 +0800
comments: true
categories: Github
---
# 在Windows操作系统下搭建Octopress博客

## 准备工作
* 安装好Git环境
* Git Clone一份Octopress项目
`git clone git://github.com/imathis/octopress.git octopress`
* rubyinstaller和DevKit安装[点我下载](http://pan.baidu.com/s/1kT80UW3)
<!-- more -->

## 开始安装
### 1. 搭建本地博客

1. 安装rubyinstaller，然后将Devkit解压到C盘根目录
2. 打开Ruby命令行窗口`Start Command Prompt with Ruby`，进入DevKit解压缩的目录，然后执行
```
ruby dk.rb init
ruby dk.rb install
gem install rdiscount --platform=ruby
```
3. 接下来进入Octopress目录，执行如下命令
```
gem sources -a http://ruby.taobao.org #添加淘宝源
gem sources -r http://rubygems.org    #移除官方源
gem souces -l
gem install bundler
bundle install #安装所需工具
rake install   #安装默认的Octopress模版
rake generate  #从源码生成静态页面
rake preview   #预览博客(http://localhost:4000/)
```
4. 现在你的博客应该已经在本地搭建完成了

### 2. 上传至Github
* 以下操作都要在Git Bash下进行
* 你的Github应该有一个`yourname.github.io`的仓库名，用来存储博客

1.在Git Bash中输入如下代码
```
rake setup_github_pages #配置Github pages地址
rake generate #生成博客页面
rake deploy #提交资源库
```

2.按照上面操作后，你的博客就已经成功上传至Github提供的静态页面了

3.接下来需要将源码也上传至Github，这一步大家可以自行百度如何上传源码。


### 3. Octopress常用命令
```
rake generate               #生成静态页面
rake preview                #本地预览博客(http://localhost:4000/)
rake install['ThemeName']   #安装新主题
rake new_post["PostName"]   #生成新的文章
rake deploy                 #提交资源库
```