---
title: Empathy + Clutter = 联系人地图
date: 2009-06-26 19:09
categories:
- Linux
tags:
- clutter
- empathy
---

我们知道，将要大面积应用到 GNOME 乃至整个 Linux 桌面应用程序中的
Clutter，将会为 Linux 图形界面带来
[大革命](http://linuxdesktop.cn/2009/02/11/the-road-to-gnome-3-01.html)
。然而，除了游戏之外，Clutter 还能为我们带来什么呢？事实上，传说中的
GNOME Shell 使用的就是基于 Clutter 的 Mutter，有兴趣可以去 GNOME
官网进行了解。

今天我们说的不是这个，而是我无意间发现的 Clutter
的一个应用。Empathy，我们的老朋友了。

话说自从 [昨天把 Arch 整个误删除了]({% post_url 2009-06-25-data-lost %})，重建工作就在紧锣密鼓的进行中，首先要装的当然是聊天工具，Gtalk
已经是我最常用的 IM，而 Empathy 是我见过最完美的客户端。

熟练的执行命令：

{% highlight console %}
[iven@~] $ yaourt empathy
1 community/empathy 2.26.2-3
     A GNOME instant messaging client using the Telepathy framework.
2 aur/empathy 2.26.2-3 (224)
    A GNOME instant messaging client using the Telepathy framework.
3 aur/empathy-devel 2.27.3-1 (13)
    A GNOME instant messaging client using the Telepathy framework.
4 aur/empathy-git 20090624-1  (3)
    A GNOME instant messaging client using the Telepathy framework.
{% endhighlight %}

当然安装最新的 empathy-git，于是发现了一个依赖 Clutter 的库
libchamplain：

{% highlight console %}
1 aur/libchamplain 0.3.3-2 (5)
    C library aimed to provide a Gtk+ widget to display rasterized maps
{% endhighlight %}

原来是个用来显示地图的库，Empathy 用这个干什么呢？安装好了之后发现 View
菜单里多了这么一个菜单项 Contacts on a Map，点击后出现：

![](http://lh3.ggpht.com/_6pI9N0iQzXE/SkUcAXucspI/AAAAAAAAAZo/MYbNwucxchk/empathy-map.jpeg?imgmax=800)

果然是个地图，这个可以显示好友位置么？

点击“放大”按钮，加载地图时有渐进效果，Clutter 果然很强大，放大后：

![](http://lh5.ggpht.com/_6pI9N0iQzXE/SkUcAWxyPqI/AAAAAAAAAZs/0a1R2NnogS0/empathy-map-zoom.jpeg?imgmax=800)

还是没有一个人……又是一番查找，在首选项中找到：

![](http://lh5.ggpht.com/_6pI9N0iQzXE/SkUcAhExCGI/AAAAAAAAAZw/vVL_48Rt_0M/empathy-map-preferences.jpeg?imgmax=800)

“显示我的位置”这项功能默认并没有启用，加上是 Git
版才有的功能，难怪地图上没有人了……

如图所示，Empathy 还有降低精确度的功能，大概是处于保护隐私的角度考虑。

有了这项功能，大家就能更加直观的看到联系人们都在哪里了，这可比 QQ
的地理位置先进多了，呵呵～

在可以预见的未来里，相信 Linux 图形界面应用在 Clutter
的帮助下会有更大的进步。

对了，想体验一下要趁现在啊，看看谁是出现在我的联系人地图上的第一人～

