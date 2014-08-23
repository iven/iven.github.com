---
title: Arch Linux - 自定义 CFlags 榨干计算机的油水
date: 2009-03-28 15:35
categories:
- Linux
tags:
- abs
- arch
- aur
- c
- gentoo
---

提到榨干计算机的油水，人们想到的往往是 Gentoo。

会这样想，一个重要的原因就是，Gentoo
完全由源码编译，在编译的过程中，可以自定义每个包的
CFlags。我们知道，很多 CFlags 可以对本机的 CPU
进行专门的优化，去除程序的一些调试信息等等，使程序在速度、体积等方面大幅度的提升（相对于没有优化来说，事实上，大多数发行版已经设定了
CFlags ，达到一定程度的性能提升），还可以设置 MAKEFLAGS 。

那么，我们的 Arch Linux 是否也可以像 Gentoo 一样自定义 CFlags
呢？当然可以。

呃，方法当然不是 export ……

用你喜欢的编辑器打开 /etc/makepkg.conf，其他不懂的不要改，看这一段：

{% highlight ini %}
#-- Exclusive: will only run on -march=x86-64
# -march (or -mcpu) builds exclusively for an architecture
# -mtune optimizes for an architecture, but builds for whole processor family
CFLAGS="-march=native -O2 -pipe -fomit-frame-pointer"
CXXFLAGS="-march=native -O2 -pipe -fomit-frame-pointer"
#-- Make Flags: change this for DistCC/SMP systems
MAKEFLAGS="-j3"
{% endhighlight %}

这是我修改过的，其中 MAKEFLAGS
原来是被注释掉的，你可以根据自己的需要修改。

当然，这些 FLAGS 只对 AUR 中需要编译的软件包或者用 makepkg
编译的软件包（其实是一个意思）才有用，如果想要全部使用这些 FLAGS
编译，你可以使用 ABS 哦，要知道源里的软件包也都是 makepkg
起来的，呵呵，编译狂人动起来吧～

