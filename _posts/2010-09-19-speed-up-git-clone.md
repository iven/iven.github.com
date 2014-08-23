---
title: "加快 git clone 速度的方法"
date: 2010-09-19 08:38
categories:
- Linux
tags:
- git
---

呵呵，不知道我是不是火星了，git clone
原来可以不全部克隆的，而是可以只克隆当前的 commit，使用下面的命令即可：

{% highlight console %}
$ git clone git://... --depth 1
{% endhighlight %}

也就是指定克隆深度为 1。

当然，通过这样克隆的代码就不能进行管理、提交什么的了。

学校的网络不知为何把 git 封了，只好用 proxychains
代理进行克隆，速度慢死，有了这个命令，安装个软件就快多了～

