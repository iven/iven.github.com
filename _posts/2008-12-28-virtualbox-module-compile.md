---
title: Virtualbox 2.10模块编译方法
date: 2008-12-28 07:15
categories:
- Linux
tags:
- arch
- virtualbox
---

新版Virtualbox去掉了vboxdrv这个生成模块的程序，在更新内核后，却还是提示用这个命令生成，BUG呀。

解决方法是进入virtualbox的安装目录，比如/opt/virtualbox，进入其中的src目录。

以root权限执行：

{% highlight console %}
$ make clean
$ make
# make install
{% endhighlight %}

然后加载模块：

{% highlight console %}
# modprobe vboxdrv
{% endhighlight %}

即可，当然也是root权限。

感觉Virtualbox发布的有点仓促，很多文档还没有跟上。

