---
title: "正在学习 PolicyKit ！"
date: 2009-03-04 14:09
categories:
- Linux
- 生活
tags:
- c
- libpcap
- policykit
---

正在学习 PolicyKit 。

PolicyKit 允许程序中的一部分使用 Root 权限，并且可以记住此权限，这对于
Cugb Freer 中的流量统计功能至关重要，毕竟，在 Linux 下使用 libpcap
是需要 Root 权限的，而 Cugb Freer 显然不能以 Root 权限运行。

想法是在其中添加一页，实现流量统计，此功能使用 PolicyKit 实现 Root
权限的 libpcap，同时让它记住权限，这样以后就不需要密码了。

国内关于 PolicyKit 的文章只有 TualatriX 那两篇残缺不全的……看 Ubuntu
Tweak 源码的话，那个又是 Python
写的……这次要是学明白了，一定要写篇解析出来，呵呵～看手册去～

