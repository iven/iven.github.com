---
title: Virtualbox 2.10桥接设置方法（Archlinux)
date: 2008-12-26 05:54
categories:
- Linux
tags:
- arch
- virtualbox
---

新版 Virtualbox 改变了桥接实现方法，再也不需要以前繁复的设置了。

只需要在客户机设置里，选择 host interface 和一个网络接口即可。

如果出现如下错误：

    Failed to open/create the internal network 'HostInterfaceNetworking-br0' (VERR_SUPDRV_COMPONENT_NOT_FOUND).Unknown error creating VM (VERR_SUPDRV_COMPONENT_NOT_FOUND).Result Code:NS_ERROR_FAILURE (0x80004005)Component:ConsoleInterface:IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

是因为你没有加载 `vboxnetflt` 这个模块，这个模块是 host interface 必需的。

在 `/etc/rc.conf` 里的 `MODULES` 加入它即可。

