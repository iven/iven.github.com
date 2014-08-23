---
title: "新一代的快速启动脚本——quick-init"
date: 2009-06-29 09:22
categories:
- Linux
tags:
- arch
- aur
- finit-arc
- quick-init
---

好吧，这又是一篇 Arch Linux 专用的文章，使用其他发行版的 TX
们请瞪眼看着吧……

还记得上次说的 Finit-ARC 么？quick-init 系列脚本就是 Finit-ARC
的延续，其实这不是什么新的东西，自从我发了那两篇文章，Finit-ARC
就停止了，据说是出于安全性考虑，不再开发使用 C 语言的
Finit-ARC，而是使用像 Arch Linux 原生的 init-scripts 一样的 Shell 脚本。

那么 quick-init 的原理是什么呢？

> The reimplementation of init-scripts consists in the modification of
> the inittab runlevels and the start of system and Xorg without udev.
> The first system level contains the creation of static devices
> necessary to boot system until fscheck. Then Xorg is started and in
> runlevel 3 it starts udev, swapon, all services etc…

大意说就是加载必要的设备和配置，然后在 udev 没有启动的情况下马上启动
Xorg，然后再启动 udev，swapon 和其他服务等等。

我们通常所说的启动时间都是进入 Xorg 的时间，这样启动速度就快了很多了～

quick-init 的安装很简单，直接 yaourt -S quick-init
即可，重启就可以看到效果，如果你对 init-scripts
比较熟悉，还可以自行修改，去掉一些用不到的设置，比如
lvm、raid、其他显卡的配置，你还可以通过参考《
[启动后自动进入X](http://wiki.archlinux.org/index.php/启动后自动进入X_(简体中文))
》这篇文章来绕过 GDM、KDM 等显示管理器，更加快速的启动电脑。

来看看我优化的效果吧～（这是启用了自动加载模块的效果，如果手动加载的话，可能会更快）

![](http://lh3.ggpht.com/_6pI9N0iQzXE/SkiHBHyGC7I/AAAAAAAAAZ0/7Iw2Rr-xOhM/bootchart.png?imgmax=800)

相关链接： [AUR 上的 quick-init
包](http://aur.archlinux.org/packages.php?ID=25563) ，
[论坛上的官方讨论帖](http://aur.archlinux.org/packages.php?ID=25563)

