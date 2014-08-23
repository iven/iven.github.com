---
title: 'Live Android: 在电脑上使用 Android 系统'
date: 2009-07-08 18:49
categories:
- Linux
tags:
- android
- google
---

Google 推出 Android 系统已经很长时间了，不少网友已经购买了一款 Android
手机防身，怎么，你还在观望么？还在怀疑 Android
系统的实用性？放心吧，手机店里的手机是不会让你随便体验的！那么，电脑上？是的，
[从 Linuxtoy
得来的消息](http://linuxtoy.org/archives/liveandroid-android-livecd.html)
，已经有个叫做 Live Android 的项目，让你在自己的电脑上体验一番 Android
了，详细情况及下载地址可以去其
[项目主页](http://code.google.com/p/live-android/) 看看。

还没有尝过 Android 的鲜，我当然下载来试试啦，最新版本是
0.2，使用前先看说明，有安装方法和其他的说明，注意验证一下 MD5，0.2 版
LiveCD 的 MD5 为：

    liveandroidv0.2.iso MD5: 03852bce8cb26aba21d147153c1fb120

我第一次就是因为没有验证 MD5，结果卡在启动界面进不去，呵呵。

我是使用 Virtualbox 虚拟的
Android，过程就像普通的系统配置一样，甚至更加简单。

经过了 Linux 风格的 Kernel Panic 和 Splash
之后，初始的界面如图所示（默认是英文，当然我已经把语言改为简体中文了）：

![android\_desktop.png](http://lh4.ggpht.com/_6pI9N0iQzXE/SlTkRXxapOI/AAAAAAAAAaY/k7lR6Kg1fmQ/android_desktop.png?imgmax=800)

可以看到几个普通手机上很常见的快捷方式，还有一个特别显眼的 Google
搜索条，无视掉这两样，我们点击右边的抽屉按钮，什么？点击？是的，Live
Android
是支持鼠标的，看到屏幕上那个半透明的三角形了么？那是鼠标指针。点击后出现下图的应用程序列表：

![](http://lh4.ggpht.com/_6pI9N0iQzXE/SlTkRVkO0hI/AAAAAAAAAac/D6Jcyj7R2nY/android_apps.png?imgmax=800)

好吧，别指望在这里能够使用摄像头来照相和摄影，更不要幻想发短信和打电话，我们来试一下电子邮件吧～输入帐号和密码，轻松就可以设置好，当然非
GMail 用户可能要设置 POP3、SMTP、IMAP 之类的，GMail
用户直接跳过。接收邮件后，发现有些非 UTF–8
编码的中文标题会显示乱码，不过不要紧，正文会正常显示。

![](http://lh6.ggpht.com/_6pI9N0iQzXE/SlTkRmfDP2I/AAAAAAAAAag/jUpxTnCFlLQ/android_mail.png?imgmax=800)

邮件客户端的设置很强大，抵得上电脑上的邮件客户端了，而且还附带新邮件提醒功能。

![](http://lh6.ggpht.com/_6pI9N0iQzXE/SlTkRgTferI/AAAAAAAAAak/ZXgtVEUr_j4/android_mail_setting.png?imgmax=800)

接下来看一下浏览器，可以看到，Kissuki 的手机版在 Android
下显示完美，呵呵，主题也很配～对了，浏览器支持文本查找，很方便。

![](http://lh5.ggpht.com/_6pI9N0iQzXE/SlTkRwGxaUI/AAAAAAAAAao/7SJaoKEFfHk/android_web.png?imgmax=800)

当然，这款不知名的浏览器是多窗口的，这可比 Opera Mini
强多了～显示窗口缩略图的时候，有很美的滑动特效，事实上，Android
上面充满着各种滑动和渐进特效，让操作看起来很平滑。当然，你也看到了，它并不支持
Flash，想看在线视频，要另想办法了……不过，它支持 Gears，倒是很令人意外……

![](http://lh3.ggpht.com/_6pI9N0iQzXE/SlTm1WDN1PI/AAAAAAAAAas/qaTxYUndc2Y/android_web_windows.png?imgmax=800)

除此之外，Android
还隐藏着很多实用的小功能，比如我刚刚发现的多桌面功能、桌面小工具、隐藏在顶部的通知栏、开发工具中的虚拟终端等等，这恐怕需要长期使用才能完全挖掘出来了。

总体来说，Android 是一款集 Google 的严谨和 Apple
的动感于一身的操作系统，不得不说，我的 E680i 实在是落伍了。Android
给我的感觉，更适合于 Geeker
们，也只有他们才需要在手机上运行虚拟终端这种东西吧……也只有他们，才能把
Android 的真正实力发挥出来……既是用户，又是开发者，正如
Linux，当然，Android 本来就是 Linux。

最后，如果你准备体验 Android 了，一定要记住以下两个键子，Esc
和键盘上右键菜单那个键子，分别对应手机上的 C
键和菜单键。如果不知道这两个键子，使用时可能会不知所措哦～

