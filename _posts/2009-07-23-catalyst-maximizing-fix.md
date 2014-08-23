---
title: "解决 Catalyst 最大、最小化窗口缓慢的问题"
date: 2009-07-23 15:14
categories:
- Linux
tags:
- aur
- catalyst
- compiz
- xorg
---

使用 Catalyst 的用户都知道，开启 Compiz
的时候，无论最大化、最小化窗口都会有半秒左右的延时，即使不开相关的动画特效也是如此，这使得原本流畅的窗口操作变得让人郁闷无比，有些网友甚至因此不得不改用开源驱动……不过，这样的黑暗时代已经过去啦！

来自 Arch AUR 的消息，Arch Linux 可以通过安装打了 Fedora patch 的
xorg-server 解决此问题，原来这是 Catalyst 与 xorg-server 的一个冲突。

假设你已经安装了 yaourt 和 catalyst 这两个包，你可以运行如下命令安装此版
xorg-server：

{% highlight console %}
$ yaourt -Rd catalyst catalyst-utils
$ yaourt -S xorg-server-catalyst-maximize-fix
$ yaourt -Rd libgl
$ yaourt -S catalyst-utils catalyst
{% endhighlight %}

接下来重启就可以看到效果啦！

通过安装这个包，不但最大、最小化窗口缓慢的问题解决了，而且感觉打开窗口也流畅了不少，特效有种脱胎换骨的感觉～而且安全无风险，很值得一试！

PS：Catalyst 9.7 for windows 已经出了，相信 for linux
也会很快出来，希望到时候能有更大的提升！

