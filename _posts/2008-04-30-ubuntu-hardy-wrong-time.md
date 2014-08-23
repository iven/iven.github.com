---
title: Ubuntu Hardy 时间不正确的解决办法
date: 2008-04-30 10:12
categories:
- Linux
tags:
- gconf
- ubuntu
---

刚刚装了 Ubuntu Hardy ，发现系统的时间不正确。
安装的时候是选的哈尔滨（+8时区）的，但是显示怎么就不对呢？
虽然时间设置里面显示正确，可是时间 applet 就不正确了。

查了查，发现是UTC时间的问题，关闭即可。
打开配置编辑器（gconf-editor），找到
`/apps/panel/applets/clock_screen0/prefs/gmt_time`，把复选框去掉即可。

