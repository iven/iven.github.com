---
title: "博客已经基本配置完毕"
date: 2009-06-21 15:50
categories:
- 新闻
tags:
- blog
- wordpress
---

呵呵，距离 [购买 Homezz 的空间](http://www.homezz.com/)
已经两天了，终于在上面部署好了 WordPress
2.8，并且加上一些常用的插件，现在博客基本已经成型了，接下来的主要就是微调。

还是说下 [Homezz](http://www.homezz.com/)
的主机情况吧，其实也没什么好说的，这两天用起来很稳定，访问不了之类的事情当然不会出现，速度也比较稳定，没有什么忽快忽慢之类的。

我这里（北京网通）ping 服务器的结果如下：

{% highlight console %}
$ ping www.kissuki.com
PING kissuki.com (209.25.170.242) 56(84) bytes of data.
64 bytes from 209.25.170.242: icmp_seq=1 ttl=47 time=228 ms
64 bytes from 209.25.170.242: icmp_seq=2 ttl=47 time=229 ms
64 bytes from 209.25.170.242: icmp_seq=3 ttl=47 time=228 ms
64 bytes from 209.25.170.242: icmp_seq=4 ttl=47 time=228 ms
64 bytes from 209.25.170.242: icmp_seq=5 ttl=47 time=228 ms
64 bytes from 209.25.170.242: icmp_seq=6 ttl=47 time=239 ms
64 bytes from 209.25.170.242: icmp_seq=7 ttl=47 time=228 ms
64 bytes from 209.25.170.242: icmp_seq=8 ttl=47 time=228 ms
^C
— kissuki.com ping statistics —
8 packets transmitted, 8 received, 0% packet loss, time 7010ms
rtt min/avg/max/mdev = 228.013/229.874/239.641/3.723 ms
{% endhighlight %}

虽然连接速度不是特别理想，但是真实浏览时并没有感觉到，还是很流畅的。

我购买的是 A 计划，容量 200M，流量每月 2.5G，可以建一个 MySQL
数据库，只用 WordPress 的话足够了。空间不是问题，图片全在 Picasa 上，1G
的空间够用好长时间了，流量的话，我这几天自己疯狂访问，用掉了
175M，估计以后流量就不会这么多了，考虑到自己惨淡的订阅数量，2.5G
应该勉强够用。

![](http://lh4.ggpht.com/_6pI9N0iQzXE/Sj4pzPMlf5I/AAAAAAAAAYE/EqgvMnlTK7w/Hostzz-A.png?imgmax=800)

空间管理用的是 CPanel，虽然美工差了点，翻译差了点，速度慢了点（Ajax
用得很多），有时还会出现乱码问题，但是不得不承认这是个功能超级强大的系统，不少功能至今还没弄懂……至少现在看来，我能想到的功能都有了……

![](http://lh4.ggpht.com/_6pI9N0iQzXE/Sj4pzFz1kfI/AAAAAAAAAYA/s2xrKKbAlfI/CPanel.png?imgmax=800)

说到这里，也没什么好评测的了，总体来说还是很满意的，50
元/年真是便宜到家了……如果流量不太大的话，可以考虑在
[Homezz](http://www.homezz.com/) 安个家哦～

接下来要做的工作是，修复失效的链接和被 Wall
的图片……唉，工作量还是很大啊……

