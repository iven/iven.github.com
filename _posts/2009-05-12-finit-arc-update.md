---
title: Finit-ARC 多项更新：我的快速启动终于完美了～
date: 2009-05-12 15:12
categories:
- Linux
tags:
- arch
- boot
- finit-arc
---

上次说的 [Finit-ARC 快速启动方案]({% post_url 2009-05-09-finit-arc %})，就像文中所说，其实在我这里根本用不了。

这是当时论坛上已经确认的 Finit-ARC 的 BUG，好在作者 adriano
更新很是勤奋，一天内在 github 上提交了十多次更新，不但解决了 hald
段错误的问题，还有很多的改进。

主要的改进有：

-   增加新的静态设备
-   支持 LVM
-   启动顺序调整（udev 和 hal 可以用了）
-   修复时钟 BUG
-   增加 swap 挂载功能
-   为 Xorg 热插拔支持自动开启 HAL 和 DBUS

现在作者似乎想放弃 Finit-ARC，开始一个新的、与 Arch Linux 完美兼容的
init 项目，拭目以待吧。

另外，如果你关注 Finit-ARC，或者想要帮忙，可以去
[这里](https://github.com/obliquo/finit-arc/tree) 看看。

下面是我现在的启动图，虽然比不好使的时候长了一秒钟。

![](http://lh5.ggpht.com/_6pI9N0iQzXE/SgmUxb2uCFI/AAAAAAAAASE/mjYbYcM6dYg/bootchart_1.png?imgmax=800)

