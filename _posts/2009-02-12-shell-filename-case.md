---
title: shell - 转换文件名大小写的方法
date: 2009-02-12 17:18
categories:
- Linux
tags:
- shell
---

{% highlight bash %}
for file in `ls`
do
    mv $file `echo $file | tr "[A-Z]" "[a-z]"`
done
{% endhighlight %}
