---
title: "两个新的 pacman 外壳：clyde 和 packer"
date: 2010-05-07 16:22
categories:
- Linux
tags:
- arch
- aur
- clyde
- packer
- pacman
---

Arch Linux 独特的 pacman
包管理器是其备受亲睐的原因之一，作为一款命令行包管理器，它深谙 K.I.S.S.
原则，在使用上甚至比很多图形界面的包管理器还要强大，还要方便、直观。

然而，Arch 的用户总是挑剔的，总是希望日常使用的包管理器更加的 Simple and
Stupid，于是有了 pacman-color、yaourt 等等，种种扩展、外壳更是把 pacman
武装成了神兵利器，再加上如我一般的用户更是用 alias
将各种命令简化，简简单单的 ysyu 命令就更新了整个系统，实在是把 Linux
下的包管理简化到了一个极点。

不过，总是有更加挑剔的用户，Linux
世界才有这么多的优秀软件，据我所知，今年又有两个 Arch 用户不满 yaourt
的缓慢、低效、丑陋（虽然我没感觉），开发出了两个新的 pacman
的外壳（wrapper）：
[clyde](http://bbs.archlinux.org/viewtopic.php?id=91860) 和
[packer](http://bbs.archlinux.org/viewtopic.php?id=88115) 。

Clyde
=====

Clyde 由 DigitalKiwi 和 Ghost1227 开发，主要是不满基于 Bash 的 yaourt
太过缓慢，和对 AUR 支持的低能。他们希望使用小巧快速的 Lua 语言重写一个
wrapper（底层用 C
编写），能够提供多线程下载的支持，并且容易在此基础上构建图形界面包管理器。

![](http://lh4.ggpht.com/_6pI9N0iQzXE/S-Q8qkndheI/AAAAAAAAAr0/UU-7w8_GCGM/Clyde.png?imgmax=800)

Clyde 保留了 pacman 和 yaourt
的选项用法，界面也很类似，使后两者的用户更加容易迁移，开发者表示，Clyde
已经足够稳定来应付日常使用，“不过如果它破坏了你的系统，烧坏你的主板，吃了你的孩子，可不要找开发者算帐，警告过你了哦！”

Clyde 可以通过 AUR 安装，软件包名 clyde-git。

packer
======

packer 的开发者是 bruenig，他开发 packer 的主要目的是整合 pacman和
AUR，看来也是对 yaourt 对两者分别处理，还在不必要的时候对 pacman
来回调用、拖慢速度十分不满。

作者认为 packer 主要实现四个 pacman 和 AUR
的整合功能就可以了：搜索(-Ss)、查看信息(-Si)、安装(-S)、升级(-Su)，在这四个功能上做到
pacman 和 AUR 一视同仁。

![](http://lh4.ggpht.com/_6pI9N0iQzXE/S-Q8q4a46YI/AAAAAAAAAr4/cnQOnxKUFlI/packer.png?imgmax=800)

如果你对 packer 感兴趣，可以从 AUR 里面安装 packer，或者 nightly
源里面也可以。

