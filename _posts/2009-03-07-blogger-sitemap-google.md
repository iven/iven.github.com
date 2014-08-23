---
title: "将Blogger的Sitemap提交给Google网站管理员工具的方法（修正版）"
date: 2009-03-07 06:32
categories:
- 新闻
tags:
- blog
- google
- rss
- sitemap
---

之前发了一个帖子《将Blogger的Sitemap提交给Google网站管理员工具的方法》，结果等了几天，Google网站管理员工具里面只能找到到
26
个网址……开始还以为是Google的问题，到网上查了查，才发现是我自己想当然了……

那两个 RSS 最多只能找到26个网址，如图（郁闷，就连这26个网址 Google
都不索引我）：

![](http://lh4.ggpht.com/_6pI9N0iQzXE/SbIXPjpHX8I/AAAAAAAAACY/gYTa3VWZwCc/Sitemap_RSS.jpeg?imgmax=800)

搜索了一下，才发现在 default 后面加上
`?redirect=false&start-index=1&max-results=500` 就可以了！

![](http://lh6.ggpht.com/_6pI9N0iQzXE/SbIl9noZaVI/AAAAAAAAACw/HxlPxinjK0Q/Sitemap_RSS_fixed.png?imgmax=800)

