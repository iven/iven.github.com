---
title: GNOME 2.29 的新改进
date: 2010-02-28 16:25
categories:
- Linux
tags:
- empathy
- gnome
- nautilus
- tomboy
---

这两天回到学校，有惊无险地把 Arch 更新了，到 Arch 官方源上一看，发现
gnome-unstable，也就是 GNOME 的开发版本 2.29 已经在里面了，而且这次有了
x86\_64 的包，作为一个更新狂，当然赶紧加上源更新。

有用 Arch 的同学可以在 /etc/pacman.conf 里面加上这两句话来开启
gnome-unstable 的仓库：

{% highlight ini %}
[gnome-unstable]
Include = /etc/pacman.d/mirrorlist
{% endhighlight %}

GNOME 2.29 带来了那些更新呢？我来说说对我来说比较有用的：

-   Nautilus 默认为 Browser 模式，增加双面板视图。
-   DeviceKit-disks 重命名为 udisks，带来大幅度改进。
-   Evince 支持反色，支持查看 PDF 文件的注解。
-   Gnome Terminal 支持无限回滚，可以设置粗体字的颜色。
-   Vinagre 支持修改色深，JPEG 有损压缩，通过 ssh 隧道连接 vnc。
-   Tomboy 支持后台自动同步和粘贴 HTML。
-   Empathy 多项改进。
-   users-admin（用户和组）界面重新设计，功能更加强大。
-   Devhelp 全屏模式。
-   Anjuta 增强了对 C, C++ 中 “.”, “-\>” 和 “::” 的自动补全支持。

当然更新不仅仅是这些，这些更新都会反应在将来面向普通用户的 GNOME 2.30
上面。

看一些截图，是在 Ubuntu 上截的：

![](http://lh3.ggpht.com/_6pI9N0iQzXE/S4qW0c8XkQI/AAAAAAAAAn8/BmhoG2FZfRY/gnome-2.29-1.png?imgmax=800)

![](http://lh3.ggpht.com/_6pI9N0iQzXE/S4qW0ehrlHI/AAAAAAAAAoA/GMY-SvPfNkE/gnome-2.29-2.png?imgmax=800)

![](http://lh3.ggpht.com/_6pI9N0iQzXE/S4qXkE8c0zI/AAAAAAAAAoE/TIiBNctQcOI/gnome-2.29-3.png?imgmax=800)

PS：在新蛋买了一个三星 N148
上网本，付了费才发现新蛋正在闹“发货门”，不知道会不会杯具……

