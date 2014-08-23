---
title: "让 Arch Linux 也使用 Ubuntu 9.04 的新通知机制"
date: 2009-04-29 14:50
categories:
- Linux
tags:
- arch
- lrcdis
- notify-osd
- ubuntu
---

看到 [TualatriX 兄在 Gentoo 下使用 Ubuntu 的新通知机制
notify-osd](http://imtx.cn/archives/1217.html) ，心里很痒啊，在 Arch
下能不能用呢？

首先想到的是看看 TX 兄是怎么改的，不过没用过 Gentoo，Ebuild
也看不出所以然来，想自己改是不可能了。

Google 一下吧，“arch linux notify-osd”，晕，发现 AUR
里面已经有了，还不止一个……

{% highlight console %}
$ yaourt  notify-osd
1 aur/banshee- notify-osd  1.4.3-3 (15)
    Patched banshee version for  notify-osd
2 aur/gajim- notify-osd  0.12.1-1 (2)
    Jabber client written in PyGTK
3 aur/gnome-mount- notify-osd  0.8-2 (11)
    GNOME mount program
4 aur/gnome-power-manager- notify-osd  2.24.4-5 (Out of Date) (18)
    Session daemon that makes it easy to manage your laptop or desktop system.
5 aur/libnetworkmanager- notify-osd  0.7.1-1 (5)
    The Network Manager Library
6 aur/networkmanager- notify-osd  0.7.1-1 (5)
    Network Management daemon
7 aur/nm-applet- notify-osd  0.7.1-1 (3)
    GNOME frontends to NetWorkmanager
8 aur/ notify-osd  0.9.12-1 (25)
    daemon that displays passive pop-up notifications
9 aur/ notify-osd -bzr 311-1 [312-1 installed] (45)
    Canonical's on-screen notification display agent, implementing the FreeDesktop.org notification specification with semi-transparent click-through bubbles.
10 aur/pidgin-libnotify- notify-osd  0.14-2 (25)
    Patched pidgin-libnotify version for  notify-osd
{% endhighlight %}

可以看到，不但有 notify-osd，还有 bzr 版的，还有针对 pidgin 各种应用的
hack 版。

我不用 pidgin，所以直接安 notify-osd-bzr，这个包与 notification-daemon
和 notify-osd 冲突，我没有安 notify-osd，所以应该先：

{% highlight console %}
$ yaourt -Rd notification-daemon
{% endhighlight %}

然后：

{% highlight console %}
$ yaourt -S notify-osd-bzr
{% endhighlight %}

最后注销一下即可。

下面是 [骨头兄](http://li2z.cn/) 的 lrcdis 的效果（Arch 里面没有
gnome-osd，怨念……）：

![](http://lh3.ggpht.com/_6pI9N0iQzXE/Sfhxwilw0QI/AAAAAAAAAN8/WB_334SpPcA/screenshot_002.png?imgmax=800)

呵呵，Arch 还是群众力量大啊，AUR 这个平台简直神了！

