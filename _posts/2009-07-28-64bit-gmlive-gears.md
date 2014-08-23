---
title: 64 位系统安装 GMLive 网络电视和 Google Gears
date: 2009-07-28 13:31
categories:
- Linux
tags:
- 64bit
- aur
- gmlive
- google
---

GMlive 想来关注 Linux 软件的同学应该很熟悉了，
[lerosua](http://www.lerosua.org/) 兄的大作，至少在中国，是 Linux
上最好的网络电视图形端了。它支持 sopcast、nslive 等后端，还支持 mms
流媒体，资源很是丰富。

然而由于 sopcast 是闭源软件，并且只提供了 32 位二进制程序，GMLive
也因此被很多发行版认为只支持 32 位系统。

其实，对于 64 位系统，只需要安装 lib32-libstdc++5 这个 32
位库即可完美运行 sopcast。

在 Arch Linux 下，可以通过安装 bin32-sopcast 这个软件包直接安装 32 位版
sopcast，不过，由于软件包维护者的疏忽，你需要在 PKGBUILD 中
depends=(lib32-libstdc++5)
这一行的下面加入一行：provides=(‘sopcast’)，来表示它已经提供并可以取代
sopcast 这个软件包。

然后安装 gmlive 这个软件包，这里也需要将 arch=(‘i686’) 改为 arch=(‘i686’
‘x86\_64’) 来填加 64 位支持。

初次运行会提示没有 nslive，无视即可，因为 nslive
已经挂了。打开视频的样子如图所示（我调用了外部播放器），可以看到，GMLive
频道齐全，还具有频道书签，录制视频等功能，一点也不比 Windows
下同类软件差。

![](http://lh5.ggpht.com/_6pI9N0iQzXE/Sm78XneQYRI/AAAAAAAAAiM/C9slowO7638/gmlive.png?imgmax=800)

如果你常看体育新闻，或者是电视剧集的发烧友，这个软件绝对不容错过。

PS：本来还想写 64 位下的 Google Gears 呢，结果 svn 好不容易弄下来 400M
的东西，第一步打补丁的时候就不过去……郁闷了……

Update:

安装 Google Gears 已成功，用的是别人编译好的扩展，具体见
[这里](http://www.jiangmiao.org/blog/450.html) 。

