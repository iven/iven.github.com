---
title: "在 Arch 中安装 Arch"
date: 2013-06-30 23:48
categories:
- Linux
tags:
- gconf
- ubuntu
---

为了业界良心我又回来写博客了。

工作的原因接触虚机技术比较多，周末没事就搭了个 LXC
玩玩，当然也有很大部分因素是依云兄
[那篇文章](http://lilydjwg.is-programmer.com/2013/4/15/first-time-lxc.38857.html)
的鼓动。过程稍微有点麻烦，记录一下。（什么你不知道什么是 LXC？LXC
就是那个啥啊，算了懒得解释。）

参考资料
========

根据倒序原则，先上资料（排名不分先后 ;D）：

-   [Arch Wiki](https://wiki.archlinux.org/index.php/Linux_Containers)
-   [Funtoo Wiki](http://www.funtoo.org/Linux_Containers)
-   [Gentoo Wiki](http://wiki.gentoo.org/wiki/LXC)
-   [LXC Manual](http://lxc.sourceforge.net/man/lxc.html)
-   [LXC Howto](http://lxc.teegra.net/)

宿主机配置
==========

编译内核
--------

这里宿主机和客户机都是
Arch，宿主机上的配置主要是重新编译内核，之前下不定决心搞就是因为这个，不过其实花不了多长时间。所需内核参数见上面的参考资料。

安装工具
--------

重启后安装 LXC 相关工具：

{% highlight console %}
$ yaourt -S lxc bridge-utils
{% endhighlight %}

配置网络
--------

我用的无线网卡，不能桥接，只能 NAT 转发。用有线的话估计 NetworkManager
就能配置了。

这里说 NAT 转发的做法，抄自依云兄：

{% highlight console %}
# brctl addbr br0
# ip a change 192.168.10.1/24 dev br0
# ip l set br0 up

# echo 1 > /proc/sys/net/ipv4/ip_forward
# iptables -t nat -A POSTROUTING -s 192.168.10.0/24 -j MASQUERADE
{% endhighlight %}

OK，搞定。

安装客户机
==========

创建虚拟机
----------

首先保证你 `pacman.conf` 中所有 Repo 都能连上，然后执行：

{% highlight console %}
$ yaourt -S arch-install-scripts
# lxc-create -n arch -t archlinux -- -P vim,dhclient
{% endhighlight %}

这样就在 `/var/lib/lxc/arch/` 下面创建了一个 Arch Linux
模板的名叫“arch”的虚拟机，并且安装了 vim 和 dhclient 两个包。

对于 btrfs 系统，LXC 很贴心地自动创建了一个
subvolume，这意味着虚拟机的克隆和快照都可以用 btrfs
本身的特性来做到，酷得想舔。

修改配置
--------

修改 `/var/lib/lxc/arch/config` ，加入一行：

{% highlight javascript %}
lxc.network.ipv4=192.168.10.2/24
{% endhighlight %}

苦逼无线再次伤不起。

启动虚拟机
----------

OK 开机：

{% highlight console %}
# lxc-start -n arch
{% endhighlight %}

登陆后还是不能上网（三咒无线网卡），需要加个 route，虚拟机里执行：

{% highlight console %}
# ip route add default via 192.168.10.1 dev eth0
{% endhighlight %}

现在可以了欧烨。

关闭虚拟机
----------

差点忘了这事，不会关机就搞笑了：

{% highlight console %}
# lxc-shutdown -n arch
{% endhighlight %}

不过 systemd 跟 LXC 默认不太兼容，需要提前在虚拟机里修复一下：

{% highlight console %}
# ln -s /usr/lib/systemd/system/poweroff.target /etc/systemd/system/sigpwr.target
# systemctl daemon-reload
{% endhighlight %}

总结
====

LXC 作为 container 技术，相比 KVM、ESX
什么的优点太明显了，不仅性能高，资源占用低，文件交换也方便，管理起来应该也简单。不过听说
LXC 还不怎么成熟，隔离性貌似也不是很好，还有处理 /dev
什么的也很烦，还只能共用一个内核。谁知道呢。

印象很深的是开机速度，不知道是不是 Arch
启动速度本身违法也有关系，这虚拟机开机时间就跟 ls
一下一样啊你妹，一点儿没有实感和成就感……想想 KVM + CentOS
那启动速度，真是云泥之别啊。

听说 LXC 完全兼容 OpenVZ 的模板？改天试试。

好的观众朋友们，本期的的讲解就到这里，我们下回见。

