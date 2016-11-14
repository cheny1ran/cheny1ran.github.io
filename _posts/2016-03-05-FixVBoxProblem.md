---
layout: post
title: 解决 Kernel driver not installed (rc=-1908)
tags: [装机, 虚拟机]
---

两次碰到过这个问题，第一次是系统刚装的时候，运行‘/etc/init.d/vboxdrv setup’的时候提示vboxdrv不存在。

解决方法：

- sudo apt-get install dkms gcc
- sudo apt-get update
- sudo apt-get install kernel-headers kernel-devel
- su -C '/etc/init.d/vboxdrv setup'

> 参考：https://www.youtube.com/watch?v=6amaEW1XSFM

第二次是昨天update系统之后，同样提示没有安装驱动，提示运行 'modprobe vboxdrv'
但是输入此命令后提示 modprobe: FATAL: Module vboxdrv not found in directory /lib/modules/

解决方法：

- sudo apt-get install linux-headers-`uname -r`
- sudo dpkg-reconfigure virtualbox-dkms
- sudo modprobe vboxdrv

> 参考：http://askubuntu.com/questions/205154/virtualbox-etc-init-d-vboxdrv-setup-issue
