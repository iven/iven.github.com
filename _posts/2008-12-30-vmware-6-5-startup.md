---
title: Vmware 6.5安装后无法启动的解决
date: 2008-12-30 14:11
categories:
- Linux
tags:
- vmware
---

终端运行出现类似提示：

    Logging to /tmp/vmware-root/setup-5583.logmodinfo: could not find module vmmonmodinfo: could not find module vmnetmodinfo: could not find module vmblockmodinfo: could not find module vmcimodinfo: could not find module vsockmodinfo: could not find module vmmonmodinfo: could not find module vmnetmodinfo: could not find module vmblockmodinfo: could not find module vmcimodinfo: could not find module vsock

原因是你的系统太新啦！Vmware经常出现这些问题。

解决方法是：

{% highlight console %}
$ mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old
{% endhighlight %}

顺便奉上一个可用序列号，试试就好，不要乱用。

    LR5HT-16602-T814A-4MEN2
