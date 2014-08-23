---
title: Arch Linux 将抛弃 i686 架构支持
date: 2009-04-01 01:27
categories:
- Linux
- 新闻
tags:
- 64bit
- arch
---

via： <http://www.archlinux.org/news/440/>

最近开发者们讨论了通过增加优化来提升 i686
架构多媒体性能的可能性，这可能意味着意味着降低对旧架构的兼容性。就像大家可能听说的那样，讨论的结果是专注于
x86\_64 架构的支持。总的来说，开发者们认为 x86\_64
架构已经足够成熟，完全可以保证这个决定的正确性，并且，这也与 Arch
支持当前主流硬件的哲学相符。x86\_64 起源于 2002 年（相对的，i686 起源于
1995 年），我们相信我们大多数 i686 用户已经拥有了兼容于 x86\_64 的硬件。

官方的抛弃 i686
架构支持的时间线（time-line）还没有建立，但是官方的公告有必要建立，就像已经泄漏到
ArchLinux-BR 社区的决定一样。然而，看起来 i686 的主要更新（GNOME, KDE,
Xorg 等等）很快就要停止 Build 了（译：这些原本是 Arch
官方编译打包的），用户仍然可以通过 ABS 建立 i686
架构的软件包。由于大多数特定架构补丁都是给 x86\_64
架构用的，因此这相对来说比较无痛。

相关链接： 
[http://groups.google.com/group/archlinux-br/browse_thread/thread/d1b6075adf9eba2d](http://groups.google.com/group/archlinux-br/browse_thread/thread/d1b6075adf9eba2d)

Update: 这则新闻被证实为愚人节笑话，请勿当真。

