---
title: git中修改commit的message的方法
date: 2009-01-23 02:04
categories:
- Linux
tags:
- git
---

一不小心commit时message写错了，找了好长时间，走了不少弯路，才找到方法……

{% highlight console %}
$ git rebase -i master~5
{% endhighlight %}

这个是找出master分支最近5次的commit，看见那个写错的了吧？把pick改成edit，保存退出。

此时工作目录已经变成这次commit的样子了，不要慌，然后：

{% highlight console %}
$ git commit --amend -m "message"
{% endhighlight %}

修改这次的message。最后：

{% highlight console %}
$ git rebase --continue
{% endhighlight %}

怎么样，成功了吧？

利用这个方法也可以修改commit的文件。

