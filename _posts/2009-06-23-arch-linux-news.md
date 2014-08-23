---
title: Arch Linux 消息三则
date: 2009-06-23 17:22
categories:
- Linux
- 新闻
tags:
- arch
---

2.6.30 版内核移往 [core] 仓库
=============================

来自上游（Upstream）的修改：

[<http://kernelnewbies.org/LinuxChanges>](http://kernelnewbies.org/LinuxChanges)

来自 Arch Linux 的修改:

-   移除了
    acpi-dsdt-initramfs.patch，目前没有能够起作用的补丁，如果你需要一个自定义的
    DSDT，请自行编译进你自定义的内核。
-   移除了 snd-pcspkr 模块 \#14958
-   增加了 dccp \#15071
-   增加了 SCHED\_DEBUG=y
-   修改为 lzma 内核压缩算法
-   移除了 rt2500 模块，它已被内核驱动支持

portmap 被 rpcbind 所替代
=========================

[core] 仓库中的 portmap 已经被 rpcbind 所替代，rpcbind
有更多的特性，例如 ipv6 和 nfs4 的支持，请相应地修改你的 /etc/rc.conf
文件。

nfs-utils 重要更新
==================

NFS4 支持现在已被应用。

这是一个相当重要的更新，你将不得不手动修改配置文件。

/etc/rc.conf 守护进程（daemons）修改：

1. 修改 portmap 为 rpcbind
2. 修改 nfslock 为 nfs-common
3. 修改 nfsd 为 nfs-server

NFS（客户端和服务器端）扩展配置在：

    /etc/conf.d/nfs-common

    /etc/conf.d/nfs-server

请根据需要自行修改。

