---
title: Python 版 Linux 下的迅雷
date: 2009-05-16 07:46
categories:
- Linux
- 编程
tags:
- python
- thunder
---

Linux
下该不该有迅雷，这个问题一直存在分歧，在此也不予讨论。不过，迅雷抗死链的作用是巨大的，这点是不容置疑的，很多人确实用得着。

有需求就有市场，于是乎，Ubuntu 中文论坛的一位 [放出了 furl
这个小程序](http://forum.ubuntu.org.cn/viewtopic.php?f=73&t=195557)
，不但可以解析迅雷的 thunder:// 协议，还可以返回迅雷候选地址， xiooli
大侠更是做出了 [Shell
脚本](http://joolix.com/2009/04/script-for-downloading-thunder-sources/)
，自动调用 aria2 进行下载。

可惜的是，furl 是 32 位闭源程序，所依赖的 lib32-libopenssl2 在 Arch
Linux 下面安装不了……

突然想起，前些日子，可可熊大侠不是 [写过一个
pythunder](http://cocobear.info/blog/2009/05/04/rewrite-pythunder/)
么？干嘛不用这个下载呢？于是就有了下面的程序……

{% highlight python %}
#!/usr/bin/env python

import os, sys, urllib

def usage():
    print """Usage: python tharia2.py [OPTIONS] URL

OPTIONS: As same as options of aria2c"""

def get_url_list(url, listpath):
    if not os.path.exists(listpath):
        print "Getting URL list, please wait..."
        f = urllib.urlopen("http://cocobear.info/demo/pythunder/?url=%s" % url)
        lst = open(listpath, "w+")
        lst.writelines(f.readlines())
        f.close
        lst.seek(0)
    else:
        print "Found existing url list: ", listpath
        lst = open(listpath)

    url_list = [line[:-1] for line in lst]
    lst.close()
    print "Recieved %d url(s)." % len(url_list)
    return " ".join(url_list)

def download(url):
    for prefix in (r"http://", r"https://", r"ftp://"):
        if url.startswith(prefix):
            break
    else:
        print "Invalid URL: %s" % url
        exit()

    listdir = os.path.expanduser("~/.tharia2/list/")
    listfile = os.path.split(url)[-1] + ".list"
    if not os.path.exists(listdir):
        os.makedirs(listdir)
    listpath = os.path.join(listdir, listfile)

    url_list = get_url_list(url, listpath)
    cmd = " ".join(("aria2c -c", " ".join(sys.argv[1:-1]), url_list))
    print "Executing command: %s" % cmd
    if not os.system(cmd):
        os.remove(listpath)

if __name__ == "__main__":
    if len(sys.argv) > 1:
        download(sys.argv[-1])
    else:
        usage()
{% endhighlight %}

很简单的一个脚本，呵呵，参数和 aria2 是一样的，区别只在于对于 url
的处理（暂时 url 只能放在命令行的最后）。

比如下载 <http://www.dmato.com/DownloadFile/FishDesk2009Beta4.exe>
，就运行：

{% highlight console %}
$ python tharia2.py http://www.dmato.com/DownloadFile/FishDesk2009Beta4.exe
{% endhighlight %}

默认 aria2 可以支持 5 线程，如果你想改为 10 线程，那么：

{% highlight console %}
$ python tharia2.py -s 10 http://www.dmato.com/DownloadFile/FishDesk2009Beta4.exe
{% endhighlight %}

指定下载目录，用 -d：

{% highlight console %}
$ python tharia2.py -d "/home/iven" -s 10 http://www.dmato.com/DownloadFile/FishDesk2009Beta4.exe
{% endhighlight %}

更多用法详见：

{% highlight console %}
$ aria2c --help
{% endhighlight %}

目前的主要问题是，可可熊大侠的网站响应速度太慢了，过半分钟才会返回候选列表，汗……不知道是不是我的网速问题，大家可以试一下。另外，就是没有解迅雷的
thunder:// 协议了，还有快车什么的，这个貌似不难，有时间研究一下。

现在还没有开源版本的迅雷候选地址搜索工具，主要大家怕流传太广，遭到迅雷封锁。但是还是好想看看代码是怎么写的啊……

最后，项目的地址：
[<http://github.com/iven/tharia2/>](http://github.com/iven/tharia2/)

