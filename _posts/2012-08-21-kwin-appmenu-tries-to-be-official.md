---
title: KWin 可能官方支持 Appmenu
date: 2012-08-21 02:05
categories:
- Linux
- 新闻
tags:
- kwin
- appmenu
---

Appmenu 是什么？看视频：

<http://youtu.be/x1bm7Q6_SH4>

简单来说，就是通过 DBusMenu
将原本的菜单栏，变成标题栏中的一个按钮，以节省空间。视频中还支持另外一种类似全局菜单的布局，适合不同需要的人。

目前这种支持是非官方的，需要通过补丁才能够使用， Arch 用户可以安装 AUR
中的 kde-workspace-appmenu 包，当然只对 KDE 用户有用……

现在，作者正在努力将代码提交到主线，快的话，可能 KDE 4.10 的时候， KWin
就有这个功能啦（当然是可选的）！个人觉得这种支持对于大屏幕来说，比全局菜单更实用，大家觉得呢？

如果你关注代码审核动态，可以关注 [KDE 的
ReviewBoard](https://git.reviewboard.kde.org/r/104344/)
，另外，项目的代码在
[Gitorious](http://gitorious.org/~megabigbug/kde-workspace-appmenu/megabigbugs-kde-workspace-appmenu)
，有兴趣的话可以研究一下。

PS: 这年头更新技术博客的都是业界良心～ ^\_^

