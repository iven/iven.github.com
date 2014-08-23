---
title: Linux下统计代码行数的方法
date: 2009-02-17 14:06
categories:
- Linux
tags:
- shell
---

我们编程时常常想统计一下自己写过多少行代码了，这时候该怎么办呢？

虽然Vim等编辑器中有代码行数显示，但是不能一个个打开然后加起来吧？

这个时候需要用到wc这个工具，呵呵，别看名字不怎么样，功能可是很强大的哦。

用法：

当前目录下：

{% highlight console %}
$ wc -l *.c *.h
{% endhighlight %}

当前目录及子目录：

{% highlight console %}
$ find . -name *.c |xargs wc -lfind . -name *.cpp | xargs wc -lfind . -name *.h |xargs wc -l
{% endhighlight %}

很方便吧？

PS：我的Cugb Linker原来还不到600行……努力！

