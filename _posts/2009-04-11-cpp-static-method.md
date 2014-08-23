---
title: C++ 中出现“不能将成员函数声明为有静态链接“的解决方法
date: 2009-04-11 17:57
categories:
- 编程
tags:
- c
---

类中遇到快速排序，准备把排序函数声明为静态的，于是有了以下代码：

{% highlight c++ %}
class BmpPixmap{
    static int cmp_Byte (const void *p1, const void *p2);
}; /* -----  end of class BmpPixmap  ----- */

static intBmpPixmap::cmp_Byte (const void *p1, const void *p2)
{
    return (* (Byte *) p1 - * (Byte *) p2);
}  /* -----  end of method BmpPixmap::cmp_Byte  ----- */
{% endhighlight %}

结果出现了错误：

> 不能将成员函数‘static int BmpPixmap::cmp\_Byte(const void\*, const
> void\*)’声明为有静态链接

这个是因为声明的时候已经提过是静态的了，实现的时候就不能再说一遍了，把实现函数的
static 去掉即可。

