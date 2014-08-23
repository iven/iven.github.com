---
title: "我的GNOME会话登录也完美了！"
date: 2009-04-05 12:45
categories:
- Linux
tags:
- compiz
- gnome
---

为什么要加个“也”字呢？因为 TX 兄写过一个
[《我的GNOME会话登录完美了！》](http://imtx.cn/archives/1175.html) 。

照着上面的方法设置，启动确实快了很多！但是发现跟我的需求还有些偏差，因为我要时不时的禁用特效，因为开着特效玩侍魂还是有些卡。可是如果按照这样设置的话，就会出现
compiz 重复载入的问题，因为 fusion-icon 会自动重新载入 compiz 一次。

有没有办法既享受超快的启动速度，又保持方便的切换呢？

看了一下 fusion-icon 的启动参数：

    Usage: fusion-icon [options|action]
    Options:
    --version             show program's version number and exit
    -h, --help            show this help message and exit
    --reset               remove configuration file and exit
    -s SECONDS, --sleep=SECONDS          Sleep before launching
    -v, --verbose         Print extra output
    Interface Options:
    -i INTERFACE, --interface=INTERFACE  Try a certain interface first
    -u, --no-interface  Do not use any interface
    Startup Options:
    -f, --force-compiz  Start compiz regardless of environment or configuration
    -n, --no-start      Run, but do not start a window manager

注意看最后一条，也就是说，只要在 fusion-icon
的启动参数中加上 -n，就不会重复启动窗口管理器了。

