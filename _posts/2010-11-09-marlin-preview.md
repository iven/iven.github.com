---
title: Marlin —— GNOME 下新文件管理器启动！
date: 2010-11-09 06:32
categories:
- Linux
- 新闻
tags:
- gnome
- gtk
- marlin
- nautilus
---

首先得说明，这个不是 GNOME 官方的计划，而是 Elementary 项目的一部分。

相信 nautilus-elementary 大家都很熟悉了，这个 Nautilus 的修改版，为
GNOME 用户提供了一个更加美观易用的文件管理器。不过， Elementary 小组为
Nautilus 做的一些修改被上游认为是 Hacks
而迟迟不被接受，现在，他们终于开始研究自己的文件管理器了！

Marlin 采用 Vala 编写界面，而 C 用来编写底层函数。在界面的编写上，使用了
GTK+ 3 和其他的 GNOME3 的时髦技术；而在底层上，Marlin 则从 Nautilus 和
Thunar 里面“偷”了些代码。加上 Elementary 自己本身特长的发挥，相信 Marlin
相较于 Nautilus 会在多个方面有所突破！

当然，Marlin 的代码刚刚推送上 launchpad
还不到一天，不要期待能够马上用到稳定版本，不过 bzr
版本已经可以看出它的一些特色了：

![](http://lh4.ggpht.com/_6pI9N0iQzXE/TNjkCS12FqI/AAAAAAAAAvM/iFX09pf8s_8/marlin_preview.png?imgmax=800)

电脑上没有装 GTK+ 3 的主题引擎，所以看起来丑了点。可以看出，Marlin
现在默认是这种小栏模式，嵌套进入目录，有点像 Ranger
的样子，操作起来很方便。当然那三个五角星预示着 Marlin
肯定会有各种传统的视图模式，另外，隐藏菜单栏之类的原有功能也是少不了的。

虽然，Marlin 还处于早期开发阶段，不过 Elementary
小组的品质一向很有保证，让我们见证这一文件管理器闪耀出奇迹的光吧！

Marlin 的源代码目前 [托管在 launchpad 上](https://launchpad.net/marlin)
，可以通过下面的命令获得源代码：

{% highlight console %}
$ bzr branch lp:marlin
{% endhighlight %}
