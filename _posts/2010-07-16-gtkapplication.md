---
title: GtkApplication - GTK+ 3 中的 Application 支持
date: 2010-07-16 03:27
categories:
- 编程
tags:
- gtk
---

GTK+ 3 在紧锣密鼓的开发之中，虽然说 3.0 版本相对于 GTK+ 2
在编程方面的改变并不大，不过仍然有些改变是和 GTK+
使用者密切相关的，比如新加入的 GtkApplication 类。

大家知道开始学习 GTK+ 的一个难点就是莫名其妙的
gtk\_init()、gtk\_main()，以及 quit、destroy
等信号的区别之类的，简单来说，一个 Hello World
程序的构建过程很让人困惑，感觉就像记住了一个模板，每次都要写一次。

GTK+ 3 为了解决这个问题，抽象出了 GtkApplication
这个类，那么一切都变得容易理解起来：gtk\_init() 就是 GtkApplication
的构造函数，现在只需要调用 gtk\_application\_new() 就可以，gtk\_main()
现在变成了 gtk\_application\_run()，意义很明显，而程序的退出也只需要连接
GtkApplication 类的 quit 信号即可。

GtkApplication 默认自带一个 GtkWindow，可以通过
gtk\_application\_get\_window() 获得，因此一个新的 Hello World
看起来可能是这样：

{% highlight c %}
#include <gtk/gtk.h>
int main (int argc, char **argv)
{
  GtkApplication *app;
  GtkWindow *window;app = gtk_application_new ("org.gtk.Example", &argc, &argv);
  window = gtk_application_get_window (app);
  gtk_container_add (GTK_CONTAINER (window), gtk_label_new ("Hello world"));
  gtk_widget_show_all (GTK_WIDGET (window));
  gtk_application_run (app);
  return 0;
}
{% endhighlight %}

怎么样，是不是简单明了得多？

更多关于 GtkApplication 类的信息可以参照 [GTK+ Reference
Manual](http://library.gnome.org/devel/gtk/unstable/GtkApplication.html)
。

