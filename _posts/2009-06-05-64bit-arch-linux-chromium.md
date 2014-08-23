---
title: "在 64 位 Arch Linux 下安装 Chromium 并启用中文输入法"
date: 2009-06-05 10:04
categories:
- Linux
tags:
- 64bit
- arch
- chromium
---

虽然今天 Chromium 浏览器 For Linux 的 Dev 版才正式“发布”，不过此前
Google 一直提供了 Chromium 的 snapshots。

当然，目前的 Chromium 功能还很不完善，Flash
等功能都不能使用，项目处于有条不紊的开发中。

尤其对于 64 位 Linux 用户来说，更是这样。因为 snapshots 都是 32
位的，看了官方的 DEB 包，也是依赖
ia32-libs，也就是说，现在没有官方编译的 64 位 Chromium For Linux。这在
64 位 Linux 下会引发输入法不能正常使用等问题。

先说说安装方法吧。在 Arch Linux 安装很简单，AUR 里早已经有了 snapshots
的包，安装即可。这个包的维护者很勤奋，每天都会更新一两次。

{% highlight console %}
$ yaourt -S chromium-snapshot
{% endhighlight %}

其他发行版的可以到
[这里](http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/)
自行下载安装。

![](http://lh3.ggpht.com/_6pI9N0iQzXE/SikJqBQ5mWI/AAAAAAAAAW8/LH2VuXzLoog/chromium.png?imgmax=800)

安装后会发现 ibus 输入法不能使用（据说 fcitx 也不行），联想到 QQ
也是这样，所以直接把 coderoar 兄那个 qq
脚本照搬过来，果然，输入法也能用了～脚本如下：

{% highlight bash %}
#!/bin/sh
GTK_IM_MODULE="xim"
QT_IM_MODULE="xim"
XIM_PROGRAM="/usr/bin/ibus-daemon"
XIM="ibus"
XMODIFIERS="@im=ibus"
export GTK_IM_MODULE QT_IM_MODULE XIM_PROGRAM XIM XMODIFIERSGCONV_PATH=/opt/lib32/usr/lib/gconv/
GDK_PIXBUF_MODULE_FILE=/opt/lib32/config/gdk/gdk-pixbuf.loaders
GTK_IM_MODULE_FILE=/etc/gtk-2.0/gtk.immodules.32
GTK_PATH=/opt/lib32/usr/lib/gtk-2.0/
LD_LIBRARY_PATH="/opt/lib32/usr/lib/:/opt/lib32/lib/:$LD_LIBRARY_PATH"
PANGO_RC_FILE=/opt/lib32/config/pango/pangorc
export GCONV_PATH GDK_PIXBUF_MODULE_FILE GTK_IM_MODULE_FILE GTK_PATH LD_LIBRARY_PATH PANGO_RC_FILEchromium-browser
{% endhighlight %}

这个是针对 ibus 的，其他输入法可能要做相应修改。

