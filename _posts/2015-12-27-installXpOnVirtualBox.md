---
layout: post
title: 在VirtualBox上安装xp虚拟机
tags: [装机, 虚拟机]
---


之前一直尝试安装xp虚拟机，安装msdn上面的xp镜像，试用期过了以后就要输序列号来激活，网上找了一圈一个个序列号试过来也是蛮蛋痛的。

后来尝试过深度或者ghost xp，不知道我这电脑什么毛病，反正一直没法安装。

今天找到了微软官方放出的福利，原本为了前端IE调试做出的windows全系列虚拟机镜像。

> 传送门
[https://dev.windows.com/en-us/microsoft-edge/tools/vms/windows/](https://dev.windows.com/en-us/microsoft-edge/tools/vms/windows/)

![](/media/pic/15/12-27-1.jpg)

选择系统版本及虚拟机版本后就可以下载压缩包了。

本次安装选择的是IE8 on XP+Virtual Box，安装包大概1个G，安装完解压后是一个ova格式的文件。

![](/media/pic/15/12-27-3.jpg)

打开VirtualBox控制台，选择 **管理->导入虚拟电脑**，选择下载好的ova文件，等待完成。

![](/media/pic/15/12-27-4.jpg)

![](/media/pic/15/12-27-5.jpg)

这样整个过程就完成啦:-)

![](/media/pic/15/12-27-2.jpg)

默认的桌面会教你各种系统下的激活方法，英语渣就不翻译了。截一下本机会用到的：
```
Win8.1系统在联网激活后可以用免费使用三个月，之后可以运行“slmgr.vbs /rearm”命令重新激活继续延长使用期限。[参考][1]
````


[1]: http://www.52microsoft.com/virtual-machine-windows-virtual-pc-browserstack/
