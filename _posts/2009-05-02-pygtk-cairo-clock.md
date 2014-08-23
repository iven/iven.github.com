---
title: "使用 PyGTK 和 Cairo 编写一个简单的时钟"
date: 2009-05-02 07:47
categories:
- 编程
tags:
- cario
- gtk
- python
---

呵呵，其实说这个是个自定义控件也不为过。

先介绍一下 Cairo：Cairo 是一套提供设备独立的矢量图形 API
的二维图形库，支持很多不同的后端，如果可能的话，还可以使用硬件加速绘图。Cairo
是用 C 语言编写的，但是提供了很多其他语言的绑定，Factor, Haskell, Lua,
Perl, Python, Ruby, Scheme, Smalltalk 等等。Cairo 基于 LGPL 和 MPL
双许可，这意味着你可以用它开发闭源软件。Cairo 是自由软件。

关于 Cairo 的更多详情，可以参照
[维基百科](http://en.wikipedia.org/wiki/Cairo_(graphics)) 。

Cairo 的使用方法很简单，跟中学时学习的 LOGO 语言差不多，这里用 GTK+
编写一个时钟出来。

首先，建立一个窗口。GTK+ 提供了一个专门用来画图的控件
DrawingArea，我们继承它，建立一个类
CairoDrwa，并且把一个对象加到窗口上去。虽然 GTK+
本身提供了不少绘图功能，不过这里只说 Cairo。

{% highlight python %}
import gtk, glib, math, time

class CairoDraw(gtk.DrawingArea):
    """Drawing with Cairo"""

    def __init__(self):
        super(self.__class__,self).__init__()


class MainWindow(gtk.Window):
    """Main window of the test program"""

    def __init__(self):
        super(self.__class__, self).__init__(gtk.WINDOW_TOPLEVEL)
        self.set_title("Cairo test")
        self.connect("delete-event", gtk.main_quit)
        cairo_test = CairoDraw()
        self.add(cairo_test)

   def main(self):
        self.show_all()
        gtk.main()


if __name__ == "__main__":
    window = MainWindow()
    window.main()
{% endhighlight %}

然后，连接事件。把这个类的 expose-event 连接到一个回调函数 on\_expose
上去，expose-event 是一个“曝光”事件，在控件被显示的时候会触发此事件。

{% highlight python %}
class CairoDraw(gtk.DrawingArea):
    """Drawing with Cairo"""

    def __init__(self):
        super(self.__class__,self).__init__()
        self.connect("expose-event", self.on_expose)
{% endhighlight %}

下面来写 on\_expose 函数。首先我们要取得我们的 Cairo
Context（可以理解为“画板”），这个画板是从 DrawingArea 中的 GdkWindow
中取得的。

{% highlight python %}
def on_expose(self, widget, event):
    context = widget.window.cairo_create()
    return False
{% endhighlight %}

我们需要设定 DrawingArea 的刷新区域。这样以后每次触发 expose-event
的时候，都会重绘这个区域。

{% highlight python %}
def on_expose(self, widget, event):
    context = widget.window.cairo_create()
    context.rectangle (event.area.x, event.area.y,
                       event.area.width, event.area.height)
    context.clip()
    return False
{% endhighlight %}

我们把绘图的部分写在 draw
这个函数中，然后让控件每秒钟重绘一次。这样每秒时间改变的时候，图形就会刷新，指针就会动了。

{% highlight python %}
def on_expose(self, widget, event):
    context = widget.window.cairo_create()
    context.rectangle (event.area.x, event.area.y,
                       event.area.width, event.area.height)
    context.clip()
    self.draw(context)
    glib.timeout_add(1000, self.queue_draw)
    return False
{% endhighlight %}

下面来写 draw 这个函数。

首先来画表盘，也就是一个圆。我们用 arc
函数来画一个弧线，这个弧线的角度从 0 到 2 \*
pi，也就是一个圆了。注意，这时候我们还没有上色，所以画板依然是空的。使用
set\_source\_rgb 来设定画笔颜色，fill\_preserve 和 stroke
分别用于填充和描边。

{% highlight python %}
def draw(self, context):
    rect = self.get_allocation()
    x = rect.x + rect.width / 2
    y = rect.x + rect.height / 2
    radius = min(rect.width / 2, rect.height / 2) - 5
    context.arc(x, y, radius, 0, 2 * math.pi)
    context.set_source_rgb(1, 1, 1)
    context.fill_preserve()
    context.set_source_rgb(0, 0, 0)
    context.stroke()
{% endhighlight %}

接下来画刻度。很简单的算法，值得注意的是 save 和 restore
两个函数，这是一种类似堆栈的保存 Context
状态的方法，这样对线的长度修改之后，很容易就可以恢复过来。

{% highlight python %}
for i in xrange(12):
    context.save()
    if i % 3 == 0:
        inset = .2 * radius
    else:
        inset = .1 * radius
        line_width = context.get_line_width()
        context.set_line_width(.5 * line_width)

    context.move_to(
            x + (radius - inset) * math.cos(i * math.pi / 6),
            y + (radius - inset) * math.sin(i * math.pi / 6))
    context.line_to(
            x + radius * math.cos(i * math.pi / 6),
            y + radius * math.sin(i * math.pi / 6))

    context.stroke()
    context.restore()
{% endhighlight %}

  最后，对指针进行绘制。和表盘差不多的算法。   :

{% highlight python %}
tm_hour, tm_min, tm_sec = time.localtime()[3:6]
handlist = (
            (tm_hour, .3, 12, 1.5),
            (tm_min, .2, 60, 1),
            (tm_sec, .1, 60, .5),
           )

for (hand, inset, num, width) in handlist:
    context.save()
    inset *= radius
    line_width = context.get_line_width()
    context.set_line_width(width * line_width)
    context.move_to(
            x + (radius - inset) * math.sin(2 * hand * math.pi / num),
            y - (radius - inset) * math.cos(2 * hand * math.pi / num))
    context.line_to(x, y)
    context.stroke()
    context.restore()
{% endhighlight %}

这样，一个简单的时钟程序就做好了。
[源代码在这里](http://github.com/iven/MyPractices/) 。

参考： [Writing a Widget Using Cairo and PyGTK
2.8](http://www.pygtk.org/articles/cairo-pygtk-widgets/cairo-pygtk-widgets.htm)

PS：晕，写完了才发现这篇文章还有
[下半部分](http://www.pygtk.org/articles/cairo-pygtk-widgets/cairo-pygtk-widgets2.htm)
……

