---
title: Arch 中抢先体验 Compiz++
date: 2010-07-15 16:00
categories:
- Linux
tags:
- arch
- aur
- compiz
---

LDCN 曾经介绍过 Compiz 将用 C++ 重写，不过之后 GNOME-Shell
的大热几乎让我们忘记了 Compiz++ 这么回事，再加上 Compiz
开发者匮乏，开发进度缓慢的一贯印象，除了少数如我一般的 Compiz
死忠，似乎很少有人关心 Compiz 怎么样了。

无论如何，Compiz
的开发者们还是在默默地为了理想中的窗口管理器努力着，如今 Compiz++
已经接近可用状态， Arch 论坛上也有人放出了 Compiz++ 系列的
PKGBUILD，如果你也是 Compiz 的粉丝之一的话，不妨抢先体验一下吧。

这几个包的名称和地址是：

[compiz-core++](http://aur.archlinux.org/packages.php?ID=35680)

[compiz-plugins-main++](http://aur.archlinux.org/packages.php?ID=35910)

[compiz-plugins-extra++](http://aur.archlinux.org/packages.php?ID=35911)

[compiz-plugins-unsupported++](http://aur.archlinux.org/packages.php?ID=35912)

[libcompizconfig++](http://aur.archlinux.org/packages.php?ID=35683)

[compizconfig-python++](http://aur.archlinux.org/packages.php?ID=35684)

[ccsm++](http://aur.archlinux.org/packages.php?ID=35685)

[emerald++ (可选)](http://aur.archlinux.org/packages.php?ID=35959)

[emerald-themes++
(可选)](http://aur.archlinux.org/packages.php?ID=35960)

安装 Compiz++ 完全不会影响现有的 Compiz，因为它是安装在 /opt
下面的，配置文件的名字也会不同。安装完成上面的包，可以运行如下命令来配置
Compiz++：

{% highlight console %}
$ /opt/compiz++/bin/ccsm++
{% endhighlight %}

开启 Compiz++（建议预先开启
fusion-icon，这样遇到什么问题，可以方便切换为原来的 metacity 或者
compiz）：

{% highlight console %}
$ /opt/compiz++/bin/compiz --replace ccp
{% endhighlight %}

如果遇到问题，试试：

{% highlight console %}
$ /opt/compiz++/bin/compiz --replace move decor composite resize place opengl
{% endhighlight %}

还不行的话，把 opengl 去掉试试。

当然这只是一次 C++
语言的重写，不要期望有大的功能上或者性能上的变化，也不要指望开发版的稳定性有多么好就是了。不过相信通过
C++ 的重写和重新架构，以后的 Compiz
开发会更加容易、更加顺畅，给我们带来更好的体验。

Arch 论坛上的讨论帖：
[<http://bbs.archlinux.org/viewtopic.php?id=93786>](http://bbs.archlinux.org/viewtopic.php?id=93786)

