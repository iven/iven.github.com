---
title: "今天邂逅了我的处女 Wall——附解决方法"
date: 2009-05-14 11:55
categories:
- 新闻
tags:
- blog
- domain
- google
- wall
---

今天天气很好很水产！本域名申请以来第一次被 Wall 掉！大家鼓掌～

呵呵准确来说是 ghs.google.com 被 Wall 了～以前 [liangsuilong
兄](http://liangsuilong.blogspot.com/)
跟我说的时候，我还怀着侥幸心理，以为伟大的 Wall
会稍稍漏点风，没想到，这么快就报应到我身上了……

今天大约下午 4 点左右，收到 [ABitNo 兄](http://abitno.linpie.com/)
的邮件，说我的网站上不去。我还以为是教育网的平行空间问题，没想到自己一访问，无论教育网还是网通都上不去了……

{% highlight console %}
[iven@~] $ ping www.kissuki.com
PING ghs.l.google.com (209.85.171.121) 56(84) bytes of data.
--- ghs.l.google.com ping statistics ---
219 packets transmitted, 0 received, 100% packet loss, time 218016ms
{% endhighlight %}

简单来说，`ghs.google.com` 被 Wall 了，连忙打开“免费门”，还可以正常上～

好吧，上网找了半天，才找到解决方法：

把原来的 CNAME 由 `ghs.google.com` 改成 `ghs.behind***.com`（把 `***
` 换成“寡妇湾”的首字母缩写，地球人都知道这个域名什么意思），然后就可以了。

这个域名自动指向 `ghs.google.com` 的可用
IP，还会不时更新，真的很不错～国内像这样的服务还有很多，看来 Wall
真的弄得天怒人怨了！

