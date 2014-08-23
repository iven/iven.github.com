---
title: "在 Arch Linux 下启用 RGBA 透明窗口"
date: 2009-05-26 05:46
categories:
- Linux
tags:
- arch
- gtk
- rgba
---

看了 Ubuntu 9.04 那么炫，突然感觉自己的 Arch
好像缺了什么，哎？窗口怎么不是透明的啊……

这个东西是由 RGBA 控制的，大家知道 RGB 是通常所说的三原色：红绿蓝，那么
A 是什么呢？不错，就是 Alpha，透明。

Arch 里面默认没有启用透明的引擎，所以窗口都是 RGB 的，看起来当然不如
Ubuntu 那么炫啦～

那么怎么在 Arch 里面启用透明呢？

先来看一下效果图：

![](http://lh3.ggpht.com/_6pI9N0iQzXE/ShuIm4Tw-ZI/AAAAAAAAAUs/7Y7UTIce6cQ/screenshot_001.png?imgmax=800)

其实启用方法很简单，只要从 AUR 里安装 librgba-gtk-module
这个包就可以了：

{% highlight console %}
$ yaourt -S librgba-gtk-module
{% endhighlight %}

然后按照提示，运行：

{% highlight console %}
$ gnome-color-chooser
{% endhighlight %}

在弹出的窗口里选择“引擎”-“全局”-“Murrine”-“首选项”，勾上 Enable/Disable
RGBA support 的两个勾就行了。

![](http://lh4.ggpht.com/_6pI9N0iQzXE/ShuKwehfm8I/AAAAAAAAAUw/3PZ3NN-azHQ/rgba_setting.png?imgmax=800)

应用的时候，可能会等待一会儿，之后就可以看到透明窗口和控件啦！

值得一提的是，并非所有窗口都支持透明效果，这要看软件的源代码启没启用支持哦～

以上方法在 Arch Linux、Gnome 2.26.2 下验证通过。

