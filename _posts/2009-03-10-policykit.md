---
title: "使用 PolicyKit 进行身份认证（上）"
date: 2009-03-10 14:26
categories:
- Linux
- 编程
tags:
- c
- policykit
---

（为了说明方便，文中很多地方使用了 PolicyKit
官方文档中的图片。这篇文章并不是官方文档的翻译，想要获得更加全面的说明，请参见
[这里](http://hal.freedesktop.org/docs/PolicyKit/) 。）

什么是 PolicyKit
================

PolicyKit 是什么呢？之前发帖子的时候并没有弄清，以为是一个可以用来获得
Root 权限的东西，经过 TualatriX 兄的指点，才发现根本不是那么回事。

PolicyKit
是一种应用程序本身或者应用程序之间验证身份的机制，验证通过，你就可以执行所请求的操作，否则没门。这样说来对于没有什么安全隐患的功能是用不到它的，比如我的
CugbFreer，需要的只是调用 libpcap
进行流量统计，实在看不出什么危险，验证反而麻烦。不过既然之前已经说了要写一篇，那还是简单说说吧。

为什么要使用 PolicyKit
======================

这个看起来像是对大多数人没用的机制，但是事实并非这样，只要仔细想一下，就可以挖掘出它的用途。

比如说，nautilus
里挂载磁盘，不知道你是否留意过，第一次使用的时候，点击一个未挂载的磁盘，就会弹出
PolicyKit 验证的界面。

我们知道，磁盘的自动挂载是靠 HAL 控制的，在 HAL 上面还有
gnome-mount，当你点击 nautilus 里的未挂载磁盘时，就会调用
gnome-mount。可是 gnome-mount
只是一个用户程序，而非特权（privileged）程序，如何能够“请”得动 HAL 呢？

与其主动去请，还不如 HAL
给我们提供一个特权接口，只需要验证一下身份，就可以调用 HAL
的特权方法，来挂载和卸载设备，并且系统可以记住这种特权，这样下次你挂载的时候，就不需要验证了！是不是很方便？

![](http://lh3.ggpht.com/_6pI9N0iQzXE/SbZ_32IdqYI/AAAAAAAAADY/ONAnDE7MYPE/diagram-bus-model.png?imgmax=800)

当然，当很多程序都需要一种验证机制、又不想自己去实现的时候，一种统一的机制
PolicyKit 诞生了。

（小提示：PolicyKit 还有哪些应用呢？我们比较熟悉的有 Network Manager
、Gnome 面板的时间控件、Ubuntu-tweak
等等。通常是在界面上加一个“解锁”键，点击时就会触发验证，以执行特权功能。）

