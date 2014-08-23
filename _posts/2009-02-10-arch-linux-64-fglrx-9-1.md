---
title: Arch Linux 64位安装Catalyst(fglrx) 9.1的方法
date: 2009-02-10 12:21
categories:
- Linux
tags:
- 64bit
- arch
- catalyst
---

官方一直不更新，烦死了。

偶然发现原来32位已经更新了，经过对比发现除了PKGBUILD是新的之外，其他文件都和64位下8.11的一样。

当然是把这些文件下载下来makepkg啦！

<http://www.archlinux.org/packages/extra/i686/catalyst/>

<http://www.archlinux.org/packages/extra/i686/catalyst-utils/>

到这两个地方，点右边的View SVN Entries，下载就可以了。

重启后发现Compiz打不开，可以做一个到/usr/lib的链接/usr/lib64就可以了。

用Xv看视频真的不闪咧！侍魂还是会卡……

