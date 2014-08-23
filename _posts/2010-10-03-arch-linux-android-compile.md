---
title: Arch Linux 下 Android 源码下载与编译
date: 2010-10-03 10:47
categories:
- Linux
tags:
- android
- arch
- git
---

最近工程实践的老师让我把 Android
环境搭建起来，并且将界面换成黑白的，算是一个考验，这里就记录一下具体的做法。

Android 源码以前没有注意过，一直以为是 git 管理，看了一下文档，才知道
Google 在 git 上面又加了一个叫做 repo 的工具，用来管理大量的 git 仓库。

repo 这个工具在 AUR 里面有，叫做“repo-git”，首先要把这个工具安好。

按照 [官网的下载说明](http://source.android.com/source/download.html)
，安装下面几个包：gperf sdl esound wxgtk valgrind，当然 base-devel 这个
group 也肯定都要装的了。64 位系统还要装 lib32-readline 和一些其他 32
位包，不过因为我装了 wine，所以所有依赖包都已经装好了。

官网说只能用 jdk5，不过我克服万难从 AUR 上安装好老掉牙没人管的 jdk5
之后，编译时提示我 jdk 版本不对，请使用 jdk6
……同学们引以为戒，官网说明已经过时了。安装好 jdk
后重启一下系统更新环境变量，当然你也可以：

{% highlight console %}
$ source /etc/profile
{% endhighlight %}

然后随便建个目录，比如我是 `~/Workspace/mydroid`，进入这个目录后：

{% highlight console %}
$ repo init -u git://android.git.kernel.org/platform/manifest.git
{% endhighlight %}

这是获得最新的 git stable 源码，或者你仅仅想要 Android 2.2.1,那么：

{% highlight console %}
$ repo init -u git://android.git.kernel.org/platform/manifest.git -b android-2.2.1_r1
{% endhighlight %}

其实就是 git branch 的封装，manifest 是一个 git 的仓库目录，里面就一个
xml 文件，记录了各个仓库的信息，repo 根据这些信息来 clone 源码。

这条命令会问你的名字和 E-mail，其实就是 `~/.gitconfig`
中的信息，如果你以前常用 git，直接回车即可。

下面就是同步源代码了：

{% highlight console %}
$ repo sync
{% endhighlight %}

Android 的源代码大约有 2G，在我令人发指的网络环境下，同步了 2
天才完事，所以速度在 200K 以下的同学就不要凑热闹了，找个地方画圈圈吧……

这个过程中就是一堆的 git clone、git
rebase，如果中断了，会从第一个开始慢慢扫描，直到之前中断的那个仓库，按照
git clone 不支持断点续传的习性，这个被中断的项目会被重新
clone。要知道，Google 这个脑残最恶名昭彰的一点就是把二进制文件往 git
里面放了，第 252 个仓库 prebuild
就是这么个地方，700M，我就在这里中断过……

闲话少说，下面是两个针对 Arch Linux 的 Fix，一个是 Make，目前 testing
中的 make 是 3.82 版本，这个版本在编译 Android 的时候开始会出错，见
[这个帖子](http://osdir.com/ml/android-porting/2010-08/msg00302.html)
，所以要降级成 core/make，也就是 3.81。

另外，如果用的是 64 位系统，那么要安装 multilib 源中的
gcc-multilib，否则会出现 libgcc.a 不兼容的错误。

全部完成之后，直接执行 make 就可以编译源代码了，当然 Makefile
有很多规则，比如只想编译计算器这个程序，make Calculator 即可。

最后就是用模拟器执行啦，建个脚本执行即可：

{% highlight bash %}
#!/bin/bash
export ANDROID_PRODUCT_OUT=~/Workspace/mydroid/out/target/product/generic
# PATH for Android emulator
export PATH=$PATH:~/Workspace/mydroid/out/host/linux-x86/bin
export ANDROID_JAVA_HOME=$JAVA_HOME
# start the emulator with debug info
emulator -debug-init
{% endhighlight %}

最后是几张模拟器的图片，是我改成黑白之后的：

![](http://lh4.ggpht.com/_6pI9N0iQzXE/TKhKNzxsg8I/AAAAAAAAAuk/tr0BDRNQOjk/android-locked.png?imgmax=800)

![](http://lh4.ggpht.com/_6pI9N0iQzXE/TKhKOMyX3mI/AAAAAAAAAuo/6ycBuskRynA/android-main.png?imgmax=800)

![](http://lh5.ggpht.com/_6pI9N0iQzXE/TKhKNgVapwI/AAAAAAAAAuc/0MmOlmPar5w/android-browser.png?imgmax=800)

![](http://lh6.ggpht.com/_6pI9N0iQzXE/TKhKN9PWEoI/AAAAAAAAAug/Fj64VvOH5tI/android-calculator.png?imgmax=800)

