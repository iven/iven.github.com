---
title: "使用 Parcellite 管理你的剪贴板"
date: 2009-06-24 15:07
categories:
- Linux
tags:
- parcellite
---

众所周知，GNOME
桌面环境并没有提供默认的剪贴板管理器，也就是说，用户默认只有一个剪贴板，第二次复制或者剪切之后，之前剪贴板中的内容就会清空，这对于想用高级剪贴板功能的人来说是很不方便的。比如我在把追看的小说存入手机的时候，总是复制很多次，然后把每章连续粘贴在一个文本文件中，这样操作起来就很费时间。那么，GNOME
环境下有什么好的剪贴板管理软件呢？

这里推荐一款叫做 [Parcellite](http://parcellite.sourceforge.net/)
的软件，这是一款基于 GTK+ 的剪贴板管理器，最新版本为 0.9.1。

在 Arch Linux 下，你可以通过以下这条命令简单安装：

{% highlight console %}
$ pacman -S parcellite
{% endhighlight %}

软件并没有一个图形窗口界面，打开后发现托盘多了一个图标：

![](http://lh3.ggpht.com/_6pI9N0iQzXE/SkI_s1IN3WI/AAAAAAAAAY8/DoTV0-jl7As/parcellite-icon.png?imgmax=800)

至此，你的剪贴板已经由 Parcellite 进行托管，可以看到，默认最多保存 25
条剪贴板历史（虽然有些省略的中文会显示为乱码，但是粘贴的时候是正常的），当然你可以在设置里进行修改。

![](http://lh3.ggpht.com/_6pI9N0iQzXE/SkI_s7jVGjI/AAAAAAAAAZA/UxzPY1Xo5Ag/parcellite-menu.png?imgmax=800)

Parcellite 同样支持 Linux
独有的“选择”复制方式，鼠标选择的文字可以自动成为剪贴板的内容，这项功能默认不开启。同样的，它还支持只采集超链接，这在某些情况下很有用。

![](http://lh3.ggpht.com/_6pI9N0iQzXE/SkI_tJ3srlI/AAAAAAAAAZE/15ql83pLBns/parcellite-setting.png?imgmax=800)

Parcellite
的一个特色功能是支持对剪贴板中的文字进行特殊操作，也就是执行一条含有它的命令，比如图中所示的命令可以把剪贴板中的内容追加到 `~/1.txt` 这个文件。

![](http://lh3.ggpht.com/_6pI9N0iQzXE/SkI_tMbYUyI/AAAAAAAAAZI/HZbnNO3gUWQ/parcellite-actions.png?imgmax=800)

如图，按住 Ctrl 键单击托盘图标，或者使用全局快捷键 Ctrl + Alt + A
即可调出菜单，全局快捷键是可以自定义的。

![](http://lh3.ggpht.com/_6pI9N0iQzXE/SkI_tGhwOFI/AAAAAAAAAZM/czr6FIpOX6M/parcellite-action-menu.png?imgmax=800)

好了，就是这么多了，如果你挖掘出更多的用法，别忘了告诉我哦～另外，大家都在用什么剪贴板管理软件呢？

PS：Picasa
总算恢复了，赶紧上传图片把文章发了，继续关注今天的事件（#chinablockedgoogle）。

