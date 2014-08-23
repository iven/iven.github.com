---
title: Catalyst 9.7 for Linux 发布
date: 2009-07-23 16:50
categories:
- Linux
- 新闻
tags:
- catalyst
---

ATI/AMD Catalyst 9.7 for Windows 显卡驱动已经在昨天发布，最新版的
ATI/AMD Linux 版的显卡驱动也已经放出，Catalyst 9.7 For Linux
显卡驱动支持 x86 和 x86\_64 平台。

按照惯例，技术人员总是先把安装文件上传到服务器，然后在几小时后发布
Release Note，里面包含新特性和已知 Bug 的说明。截止目前为止，Release
Note 仍没有释出，可能正在撰写中。

建议大家不要使用此文件直接运行，而是使用与各发行版包管理系统相容的方式安装，以免出现问题。

下载地址： [Catalyst 9.7 for Linux
x86/x86\_64](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-7-x86.x86_64.run)

**Update：**

Release Note 已放出，主要更新：

**支持新操作系统：**

RedFlag DT 7.0

**已解决问题：**

-   X segmentation fault no longer occurs after applying reflections or
    rotations on some systems that support Xrandr 1.2 or higher
-   Catalyst Control Center hot plugging a secondary display no longer
    causes screen corruption in clone mode
-   Monitor are now disabled after removing the secondary display when
    system is in standby
-   Some systems now report CrossFire adapters available during driver
    re-install
-   On some multi-monitor configurations disabling one display no longer
    causes both displays to become disabled
-   X Server does not intermittently fail to start on some multi adapter
    configurations
-   Executing xrandr —prop no longer causes Ubuntu 9.04 X Server to stop
    responding
-   [Ubuntu 9.04] Segmentation fault no longer occurs with X server
    Xinerama is enabled

已知问题：

-   Toggling between terminals may cause the system to become
    unresponsive
-   Catalyst Control Center Display Manager may fail to display HDTV PAL
    modes
-   The mouse cursor may fail to switch between primary and secondary
    display in some dual-head configurations
-   “aticonfig -xinerama=o”n may result in different dimension and dpi
    settings between Ubuntu 8.10 and 9.04
-   RandR 1.2 specifying Rotate in xorg.conf may cause X startup to fail
-   The mouse cursor may show incorrect rotation and position on some
    systems with large desktop enabled
-   Removing secondary display may cause the login screen to appear on
    the ghost monitor
-   Moving the mouse cursor between two displays may show a the cursor
    on both displays simultaneously
-   System may stop responding when running Return to Castle Wolfenstein

PS：太晚了，不翻译了，又是双显示器和交火，有几个人用到啊……

