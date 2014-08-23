---
title: Arch Linux 中 Xorg 1.6 将转移到 extra 源
date: 2009-04-11 15:05
categories:
- Linux
- 新闻
tags:
- arch
- xorg
---

Xorg-server 1.6.0 及其相关驱动将被移往 extra 源。

这一版本带来了输入设备属性（input device properties），DRI2 和
内核模式设置（KMS）的特性。注意目前只有 Intel 驱动实现了 DRI2 和 KMS
的支持。

这一版本也带来了一个新的驱动：
xf86-video-intel-legacy。这是一个添加了补丁以支持新版 xorg-server 的旧版
Intel 驱动。此驱动适用于使用新的 xf86-video-intel 驱动遇到问题的用户。

仍在使用 xorg-server 1.4.2 的用户建议升级一下，并使用 legacy 驱动来代替
intel 和 i810 驱动。

> Xorg-server 1.6.0 and its related drivers will make their move to
> extra.
>
> This new release features input device properties, DRI2 and kernel
>
> modesetting (KMS). Note that DRI2 and KMS are only implemented by the
>
> Intel driver at this moment.
>
> This release also comes with a new driver: xf86-video-intel-legacy.
> This
>
> driver is an old intel driver version, patched to support recent
>
> xorg-server versions. This driver should be used by people having
>
> problems with the newer xf86-video-intel driver.
>
> People still using xorg-server 1.4.2 are advised to upgrade and
> replace intel or i810 drivers with the legacy driver.

via:
[<http://www.archlinux.org/news/443/>](http://www.archlinux.org/news/443/)

