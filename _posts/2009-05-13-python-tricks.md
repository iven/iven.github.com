---
title: Python - 你可能不知道的
date: 2009-05-13 14:52
categories:
- 编程
tags:
- python
---

最近决定系统学习 Python，于是把去年 ChinaUnix 的赠书《Python
核心编程》掏出来，使劲啃……

通过这几天的学习，总算是看完了前六章，发现许多以前在《Dive Into
Python》里面没有提到，或者很少提到，或者很容易忘掉的特性，在此记录一下～呵呵，感谢
CU 的赞助，感谢 CCAV，感谢 GFW，感谢 宋吉广 的人品～

-   首先，交换 x, y 的值：

{% highlight python %}
x, y = y, x
{% endhighlight %}

-   跟 C 不同，连续的判断：

{% highlight python %}
if x > y > z:
{% endhighlight %}

-   跨平台，平台自适应的换行符（`\n`、`\r\n`……）：

{% highlight python %}
os.linesep
{% endhighlight %}

-   `` `foo` `` 的作用和 `repr(foo)` 的作用是一样的（虽然 `` ` ` `` 已经不推荐使用）
-   `str()`、`tuple()`、`list()` 等是工厂函数，用来生产对象，而不是简单的强制转换
-   `id()` 函数用来查看对象的唯一标识符
-   int 型会在必要时自动转换成 long 型
-   字符串和 tuple 一样，是不能改变的，例如下面的代码执行会出错：

{% highlight python %}
str[0] = 'a'
{% endhighlight %}

-   Python 中存在复数这个类型
-   `//` 可以用来做整除（地板除）：

{% highlight python %}
>>>1.0 // 2.00.0
{% endhighlight %}

-   幂运算符 `**`
-   对于 list，`extend()` 比 `+` 快
-   可以用 `string.Template()` 实现 Shell 的 `${变量}` 的功能
-   `enumerate()` 函数可以用来产生序列的序号
-   tuple 可以用来作 dict 的 key
-   `copy.deepcopy()` 可以用来做深拷贝

Python 还有很多不知道的啊，继续学习……

