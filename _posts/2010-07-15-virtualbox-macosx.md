---
title: "在 Virtualbox 中安装 Mac OS X"
date: 2010-07-15 12:06
categories:
- Linux
tags:
- macosx
- virtualbox
---

关注 Virtualbox 的同学可能已经知道，Virtualbox 3.2 版本中已经加入了 Mac
OS X Guest 系统的支持，也就是说，我们可以在其他系统上通过 Virtualbox
虚拟它、体验它了！

我个人以前也在真机上折腾过所谓的“黑苹果”，不过由于我的台式机 CPU 都是
AMD
的，折腾来折腾去一直没有成功安装运行起来过，不过单单是它的安装界面，就不枉众人对它的美誉了。感谢郭嘉以及
Virtualbox 给了我这次宝贵的体验机会，我当然要好好珍惜啦。在 Lifehacker
这篇《 [How to Run Mac OS X in VirtualBox on
Windows](http://lifehacker.com/5583650/run-mac-os-x-in-virtualbox-on-windows)
》的指引下，安装过程很是顺利。

这里简单说说要点：

首先，确定你的 CPU 支持虚拟化《 [How To Find Out If Your CPU Supports
Hardware Virtualization (Intel VTx /
AMD-v)](http://www.webupd8.org/2010/07/how-to-find-out-if-your-cpu-supports.html)
》

然后，下载一款黑苹果的 ISO，我用的是 Hazard 的 [OSX86 Snow
Leopard](http://thepiratebay.org/torrent/5203531/Snow_Leopard_10.6.1-10.6.2_Intel_AMD_made_by_Hazard)
。

接着，在 Virtualbox 3.2.6 或以上版本里面，创建一个虚拟机，目前
Virtualbox 3.2.6 中 CPU 只能选单核，内存自己定（我用 1G），不要选 EFI
选项，网卡要选 Intel PRO/1000 MT Desktop，声卡驱动见《 [Mac OS X guest
sound support
driver](http://forums.virtualbox.org/viewtopic.php?f=4&t=30843) 》。

插入光盘，启动虚拟机，开始时要按回车或者按
F8，不然会启动不了。格式化好磁盘，然后在安装时选自定义，注意选中最上面的所有更新，选中
Kernels 里面的 Legacy kernel，以及最下面的附加字体。对于 AMD
用户，要选中下面的“AMD”，对于 Intel 用户，则需要在 bootloaders
里面选中最新版本的
Chameleon。最好不要选其他的了，否则不保证能安装成功，经验之谈。

最后，就是漫长的安装过程了，大概要一小时或者更长（我用的是动态扩展的磁盘空间）。

安装过程到此为止，重启后经过简单的设置，就可以进入桌面了。

![](http://lh4.ggpht.com/_6pI9N0iQzXE/TD73kp-H92I/AAAAAAAAAtU/Wz6Spgi_H5I/MacOSX_Virtualbox.png?imgmax=800)

在 Virtualbox 中虚拟的 Mac OS X 还没有虚拟 XP 那么流畅，CPU
占用率也一直很高，不过还差强人意，各种特效能够运行起来，足以让人体验一下传说中苹果系统的风采了。

也许是习惯了各种仿苹果系统的 Dock、动画之类的，Mac OS X
并没有十分的惊艳的感觉。不过通过简单的试用，我还是能够体验到 Mac OS X
背后那种深厚的文化底蕴，虽然动画效果没有 Compiz
绚丽多姿、功能强大，不过整体的协调感、界面的一致性，这都是 GNOME 乃至
KDE、Windows 7 都模仿不来的，这或许就是传说中的“简约不简单”吧。

