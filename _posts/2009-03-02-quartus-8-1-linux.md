---
title: Quartus 8.1在Linux上的安装破解方法
date: 2009-03-02 04:39
categories:
- Linux
tags:
- arch
- csh
- eda
- quartus
- ubuntu
---

学习SOPC，自然会用到Quartus
II和NIOS，这两个软件似乎是java编写的，所以都有linux版。

首先，到
[官方网站](https://www.altera.com/support/software/download/altera_design/quartus_sub/dnl-quartus_sub.jsp)
下载 Quartus II Subscription Edition Software v8.1(Includes MegaCore IP
Library) 和 Nios II Embedded Design Suite
这两个软件，下载时需要注册，也可以选择 Get One-Time Access
取得一次下载权限。

然后，解压两个tar包，分别以root权限运行install脚本，注意运行此脚本需要
csh 。

最后，运行 安装目录/quartus/bin/quartus 即可。

我在 Arch Linux 64bit 下运行会出现段错误，在 Ubuntu 8.10 32bit
下运行正常，可能是64位问题，也可能是 csh 问题，不过总算是能用了。

注册时，licence.dat可以用windows下的，对于没有licence的同学，可以参照这个：
:

    How to crack Quartus for linux:
    ===============================

    $ cd /linux

    $ cp libsys_cpt.so libsys_cpt.so.bak

    then run gdb:

    gdb> file libsys_cpt.so

    gdb> info function l_pubkey_verify

    Note the resulting address (for Quartus 7.2 it was 0x000c617b)

    quit gdb, then open libsys_cpt.so using a hex editor, then go to the address that you got from gdb and replace the 3 bytes starting at that address with those bytes: 31 C0 C3

    Alternatively one can get the address of ‘l_pubkey_verify’ function using the command:

    $ nm libsys_cpt.so | grep l_pubkey_verify

    Now regular quartus tool flow can work, except for the Design Space Explorer, to get the Design Space Explorer working do the following:

    * Note the first few bytes (8 or more) in the ‘l_pubkey_verify’ function of the original libsys\_cpt.so, and search for those bytes in quartus\_sh (using a hex editor). I found that the number of bytes to search for (which were 8 for Quartus 8.0) are the minimum number of bytes which will match only once in quartus_sh.

    * Replace the first 3 bytes with those bytes: 31 C0 C3
