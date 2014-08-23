---
title: "使用 dbus-python 建立单实例进程"
date: 2010-09-23 12:45
categories:
- 编程
tags:
- dbus
- python
- yaner
---

D-Bus 是 Linux 系统上广泛应用的消息总线，是 Linux
桌面程序常用的消息通信机制之一，熟悉 Linux
编程的同学可能对它已经很熟悉了，不过对于我来说，看了好长时间文档才算有点收获，赶紧记录下来。

大家知道 \#yaner 得是个单实例（Single
Instance）程序（不知道的同学赶紧知道），之前这种单实例的特性是由网上抄来的一段代码，用
Socket
的唯一地址实现的。功能虽然实现了，不过想要进一步扩展就比较难了，好吧，相比于
D-Bus，Socket 我更是一窍不通。

为什么要扩展呢？大家知道，作为一个下载器，是要支持浏览器滴，可是怎么支持浏览器呢？当然是浏览器来调用下载器的命令行。这样就要求，下载器是单实例程序的同时，运行其他实例的时候，不仅要提示用户已经有一个实例运行，还要从命令行接收参数，传输给之前存在的实例，这就需要进程间通信了。

下面就是一段简单的用 D-Bus
实现的单实例类，继承这个类的类都将获得单实例特性。目前它还没有通信相关的代码，将在后面加入。

{% highlight python %}
import dbus
import dbus.service
import dbus.mainloop.glib

class SingleInstanceAppMixin:
    "Single Instance Application"

    def __init__(self, bus_name):
        dbus.mainloop.glib.DBusGMainLoop(set_as_default = True)
        self.bus = dbus.SessionBus()
        try:
            self.bus_name = dbus.service.BusName(bus_name,
                    self.bus, allow_replacement = False, replace_existing = True, do_not_queue = True)
        except dbus.exceptions.NameExistsException:
            print "Another instance is already running."
            self.on_instance_exists()

    def on_instance_exists(self):
        """
        This method is called when an instance of the program already
        exists. It may be overwritten by subclasses.
        """
        import sys
        sys.exit(0)
{% endhighlight %}

代码很简单，主要原理就是利用 D-Bus 中 BusName 的唯一性，其中 BusName
的三个 Bool 型常量的设置分别表示不允许被替换、尝试替换同名
Bus、存在同名时不加入队列，这样就可以保证存在同名 Bus 的时候出现异常了。

需要注意的是 self.bus\_name
将其返回结果加上引用，免得执行完函数之后销毁掉了，在调试的时候在这里卡了半天，用
vimdiff 才看出来问题所在……

