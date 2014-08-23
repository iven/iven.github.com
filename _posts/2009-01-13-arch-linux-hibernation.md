---
title: Arch Linux无法休眠的解决
date: 2009-01-13 05:42
categories:
- Linux
tags:
- arch
- grub
---

用了好久 Arch
Linux，一个美中不足就是无法休眠。点了休眠按钮，看到它在休眠，可是重启后还是正常启动。

网上查了查，找到解决办法。

添加自己到 `power` 组：

{% highlight console %}
# gpasswd -a username power
{% endhighlight %}

修改 `/boot/grub/menu.lst` ，加上 `resume=<你的swap分区>` ，例如：

    kernel /boot/vmlinuz26 root=/dev/sda4 resume=/dev/sda5 ro

OK，享受超快的开机速度吧。

