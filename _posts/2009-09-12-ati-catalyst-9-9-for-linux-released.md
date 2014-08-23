---
title: ATI Catalyst 9.9 for Linux 放出——仅仅是修正 BUG
date: 2009-09-12 03:33
categories:
- 新闻
tags:
- catalyst
---

在专门为 Ubuntu 9.10 定做的 Catalyst 9.10 泄漏出来之后，ATI
很快又发布了催化剂 9.9，从 Release Note 上面看，新版 Catalyst 仅仅是修复
BUG 而已，新特性里面也仅仅是支持新的操作系统。

这版催化剂仍然不支持 Kernel 2.6.31，的确，按照 ATI 的惯例，既然出了支持
2.6.31 的泄漏版 9.10，那肯定是到 9.10 正式发布才会给予正式支持。

想更新新版，又想用新内核的同学，可以使用 9.10 泄漏版，或者使用 AUR 中
[kozzi](http://aur.archlinux.org/account.php?Action=AccountInfo&ID=2324)
提供的 [patch](http://aur.archlinux.org/packages.php?ID=29111)
（未经测试）来使用 9.9，不过无论哪种，都没有提供 XvBA 的支持，可恶的
ATI……

根据消息，Kernel 2.6.32 将提供 R600/R700 的 KMS 以及 3D
支持，估计到时候会有一大批人换上开源驱动了……

下载地址： [Catalyst
9.9](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-9-x86.x86_64.run)

