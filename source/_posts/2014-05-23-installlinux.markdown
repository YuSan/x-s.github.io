---
layout: post
title: "Linux 硬盘安装指南"
date: 2014-05-23 15:08:13 +0800
comments: true
categories: Liunx
---
* 本文将教会你如何在Windows环境下直接安装Linux操作系统
* 无需其他任何工具

<!-- more -->

# 分区建议
==========
```
/ 建议15G以上，如果/home不单独分区，则建议30G以上
/home 建议30G以上，尽量单独分区
swap 建议2G
/boot 可以不单独分区，如果单独分区，建议300M以上
```
*以上步骤建议在Linux安装过程中分区，而不要用Windows工具*


# 以下是用grub4dos，在windows xp环境中引导iso文件实现硬盘安装(Windows Vista && 7 在下面)

* 下载最新版本的Grub4DOS

下载地址： http://download.gna.org/grub4dos （请自己找最新的zip包）

下载并解压缩后，将目录中的grldr （非grldr.mbr），grub.exe两个文件复制到C盘根目录下

在下载好的iso文件中，casper文件夹目录下，找到vmlinuz、initrd.lz（文件名也可能是initrd.gz）解压，并复制到C盘根目录下

* C盘根目录下建立menu.lst文件，内容为：

title Install Ubuntu 

root (hd0,0)

kernel (hd0,0)/vmlinuz boot=casper iso-scan/filename=/`ubuntu-13.10-desktop-i386.iso` ro quiet splash locale=zh_CN.UTF-8

initrd (hd0,0)/initrd.lz


注：圈出字体部分就是需要安装的ISO映像文件的文件名，根据实际情况作调整，initrd.lz也可能是initrd.gz，请确保文件名正确，注意大小写一致。

* 接着，在我的电脑–>工具–>文件夹选项–> 的查看标签下去掉“隐藏受保护的操作系统文件”之前的勾，并勾选“显示所有文件和文件夹”。

取消C盘根目录下的boot.ini文件的“只读”属性，然后用记事本打开boot.ini文件，做如下更改：timeout=0 改成 timeout=5 或者更大的数字，在boot.ini 文件内容末尾加上一行 C:\grldr="GRUB"

* 将`ubuntu-13.10-desktop-i386.iso`复制到某个分区的盘根目录下

* 重启电脑，开机选择“GRUB”，进入live CD模式

* 安装前，首先打开终端输入：
```
sudo umount -l /isodevice
```

*（此命令一定要运行，否则会出现不能对磁盘操作的情况！）*

* 双击桌面的图标“安装”开始安装，下面就直接下一步，下一步，安装时“分配磁盘空间”这一步，记得选择第三项“其他”

![](/media/2014-05-23-installlinux/other.png)

* 之后按照自己的意愿手动编辑分区信息即可

* 待一切安装完成以后重启即可

# 以下是用Easybcd，在windows Vista && 7环境中引导iso文件实现硬盘安装

* 下载iso文件，casper文件夹目录下，找到vmlinuz、initrd.lz（文件名也可能是initrd.gz）解压，并复制到C盘根目录下

* 下载Easybcd安装并运行

* 启动 EasyBCD 选择Add new entry—>NeoGrub—>Install，然后在新出现的界面点：configure，出现menu.lst，添加以下内容：
```
title Install Ubuntu
root (hd0,0)
kernel (hd0,0)/vmlinuz boot=casper iso-scan/filename=/ubuntu-13.10-desktop-i386.iso ro quiet splash locale=zh_CN.UTF-8
initrd (hd0,0)/initrd.lz
```

![](/media/2014-05-23-installlinux/easybcd.png)

重启，选“NeoGrub Bootloader”进入live cd

安装前，首先打开终端输入：`sudo umount -l /isodevice`

剩下的步骤按照上面的最后两步执行即可