---
title: "解决Arch Linux下A卡开compiz假死的问题（转贴）"
date: 2008-12-18 12:19
categories:
- Linux
tags:
- arch
- catalyst
- compiz
- grub
---

开compiz,偶尔会出现两三秒的假死，严重影响使用。

[linuxsir里也有人说这个问题](http://www.linuxsir.org/bbs/thread339681.html)
，其实解决办法很简单：

编辑/boot/grub/menu.lst，kernel那行后面加参数 “nopat”,如：

    kernel    /boot/vmlinuz26 root=/dev/sda10 ro nopat

如果是用GRUB2，则编辑/boot/grub/grub.cfg,linux行后加“nopat”,如：

    linux    /boot/vmlinuz26 root=/dev/sda10 ro nopat

原来问题如此简单，我一直以为是AMD显卡驱动的问题，试过好几个版本，闭源开源的都失败,害我都放弃compiz了

BBS上给出办法的ref159实在是太帅啦！

PS: 这个问题似乎不只A卡会遇到.N卡也有.

[文章来源](http://xxb.is-programmer.com/2008/12/1/nopat.6498.html)

PS：其实那个提问的人就是我。

