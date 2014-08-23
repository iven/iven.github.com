---
title: "编译最新 Git 版本 GNOME Shell（附视频）"
date: 2011-01-22 12:02
categories:
- Linux
tags:
- git
- gnome
- gnome-shell
---

相信很多人都知道，GNOME 3 最早今年 4 月份就会正式发布了，甚至 [GNOME 3
的官方网站](http://gnome3.org/) 都已经上线，那么 GNOME 3 的重头戏，GNOME
Shell，现在已经发展到什么程度了呢？

如果你注意 GNOME 3 官网的最下面，可能已经发现官方提供的方法了，那就是
jhbuild！之前也曾经试用 jhbuild 编译过 GNOME
Shell，不过最后都不能启动，这次克服了点小困难，终于成功了，简单说一下：

-   首先你要有至少 1.9.2 版本的
    xulrunner，这个根据各个发行版自己解决吧～Arch Linux 下直接安装
    xulrunner 这个包即可。
-   依次运行下面的命令：

{% highlight console %}
$ sudo rm -rf /usr/lib*/*.la
$ curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
$ /bin/bash gnome-shell-build-setup.sh
$ ~/bin/jhbuild build
{% endhighlight %}

-   如果是在 Arch 下，由于 python 3 为默认，编译 gjs
    的时候，可能要修改一下一个脚本，将 python 改为 python2。
-   编译成功后，使用下面的命令运行：

{% highlight console %}
$ cd ~/gnome-shell/source/gnome-shell/src
$ ./gnome-shell --replace
{% endhighlight %}

-   如果出现下面的错误：

<!-- -->

    mutter: symbol lookup error: /home/iven/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so: undefined symbol: gtk_quit_ad

可能是 API 变动导致的，删除那个文件即可，毫无危险：

{% highlight console %}
$ rm /home/iven/gnome-shell/install/lib64/gtk-3.0/modules/libcanberra-gtk-module.so/pre>
{% endhighlight %}

基本上这样就可以执行了，这里录制了一段 [GNOME Shell
的演示视频](http://www.youtube.com/embed/u86Oi4Bo6LI?rel=0&amp;hd=1)
，不妨边编译边看（请自备犯罪工具）。

