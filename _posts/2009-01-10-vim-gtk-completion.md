---
title: Vim 对Gtk+ API 函数自动补全（转载）
date: 2009-01-10 19:12
categories:
- Linux
tags:
- ctags
- gtk
- vim
---

转自：
[http://www.91linux.com/html/article/linux\\\_soft/20090103/15308.html](http://www.91linux.com/html/article/linux\_soft/20090103/15308.html)

Gtk的API有很多，如何在使用时让VIM自动补全呢？

其实VIM已经有此功能了，这就是VIM的自动补全功能。包括ctrl-N,ctrl-P以及Ommi
补全功能。

当然了，还有对包含的头文件的自动搜索。但是编写gtk程序有一点不方便的是，它包的是gtk.h，而gtk.h中是一大堆的\*.h文件，显然是不可能在gtk.h中找到什么有用的东西的。

是不是有别的什么办法呢？

linux的使用在于小巧组合，vim配合ctags即可完成此任务。步骤如下：

1.  首先进入/usr/include/gtk–2.0/gtk目录，下面有很多头文件，我们要在此目录下生成一个tags文件供使用。
2.  执行ctags -R
3.  将生成的tags文件copy到你的工作目录，即你写程序的地方。
4.  再执行ctags -a //将你写的程序的函数appended 到此文件上。

OK，大功告成。这下你写程序时，即可ctrl-N/P来自动补全gtk的API了。

不过使用时列表中的函数是有点多了，选择起来反而有点麻烦，但总比没有要好。

