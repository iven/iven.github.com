---
title: Blogspot 绑定域名的方法
date: 2009-05-08 04:29
categories:
- 新闻
tags:
- blog
- domain
- wall
---

昨天[购买了域名 kissuki.com]({% post_url 2009-05-07-kissuki-com %})，但是怎么跟 Blogspot 绑定起来却是个问题。

开始的想法是 301 重定向，由于 Godaddy
的重定向在国内不能用（不知道为啥，用代理也不能用），于是用了 Godaddy
的虚拟主机进行了重定向，然而费了半天劲，重定向的效果并不理想。

主要就是重定向之后，地址栏的域名还是 Blogspot 的域名，那域名不是白换了？

查了半天资料，总算找到 Blogspot 绑定域名的方法（以下内容参考
[自定义域发布Google Blogger](http://www.sinoblog.org/2007/10/78.html)
）：

1.登录Blogger后台，点击“设置”-\>“发布”

![](http://lh6.google.com/wuzhisong2008/RygumbEkYNI/AAAAAAAAAOc/u8fj2Xf3IBo/s400/2007103101.PNG.jpg)

2.点击“自定义域”-\>“高级设置”，输入绑定的域，比如我输入的是:
www.kissuki.com

![](http://lh4.google.com/wuzhisong2008/Rygum7EkYOI/AAAAAAAAAOk/SGKuokTgzrU/s400/2007103102.PNG.jpg)

3.进入域名管理后台，增加一个CNAME别名设置，使你的域指向 ghs.google.com

![](http://lh5.google.com/wuzhisong2008/RygunLEkYPI/AAAAAAAAAOs/GRZYk2pqlZc/s400/2007103103.PNG.jpg)

最后，等待域名解析生效。

至此，域名绑定就完成了，至于以后被不被 wall，那就看 RP 了～

