---
title: "那些在 Python 3 中闪亮的"
date: 2011-11-15 13:57
categories:
- 新闻
tags:
- python
featured: true
---

大家好，又到了科普时间，咳咳。

距离 Python 3 发布已经有一段时间了，主流发行版都已经带了 Python 3
的软件包，甚至 Arch 等发行版还将其设为了默认的 Python
版本。多数的库也已经带了 Python 3 的支持（也有 Twisted、Django
等例外），是不是偶尔也想着要不要将自己的程序升级一下呢？

昨天稍微有时间研究了一下 Python
3，就将我在文档中找到的有趣新特性分享给大家。

默认返回迭代器（Iterator）
==========================

print 成为一个函数、默认不用地板除（Floor
Divide）之类的我就不说了，想必地球人都知道有这么回事。

值得一提的是，原来需要使用 xrange 、 iteritems
等等函数和方法才能返回的迭代器现在成为了默认，替代了原来返回列表的函数。就连
map 、 filter 、 zip 等函数都返回迭代器了。

大家都知道相对于返回完整的列表，迭代器省去了一次生成所有元素的开销，并且在循环
break
的时候，就停止迭代，防止了额外的开销，所以一般情况下迭代器要比列表快得多。

如果你仍然需要完整列表，可以通过 list(some\_iter)
构造，不过这种问题往往使用列表解析（List comprehension）就能够解决。

字符串分为 str 和 bytes
=======================

在 Python 2 中，字符串分为 ASCII 码表示（‘some text’）和 Unicode
表示（u‘Unicode 字符串’），默认为 ASCII 码。

不过在 Python 3 中，默认就是万能的 Unicode
码了，所以字符串前面不用加字母 u 也可以写 Unicode
了，当然这不是重点，重点是不会有各种 ASCII 和 Unicode
转换和混用带来的错误了。

另外， Python 3 中增加了一种 bytes
对象（`b‘\xb6\xfe\xbd\xf8\xd6\xc6\xca\xfd\xbe\xdd’`），专门用来表示编码后的（二进制）数据，所以现在对字符串的编码就是从
str 到 bytes
的转换，反之亦然，两者不能混用，这样编码与否一目了然，免除了很多错误。

源文件编码默认为 UTF–8
----------------------

Python 3 在字符编码方面有很多改进，其中之一就是默认的源文件编码从 ASCII
变为 UTF–8 ，也就是说以前在文件头加上的各种花样的 coding=utf–8
不再需要了！

{% highlight python %}
# coding: UTF-8
# vim:fileencoding=UTF-8
# -*- coding=UTF-8 -*-
# vim: set fileencoding=UTF-8
{% endhighlight %}

标识符支持非 ASCII 字符
-----------------------

这个自行理解，易语言表示压力很大。

{% highlight pycon python3 %}
>>> 所有 = all
>>> class 男人:
...     @classmethod
...     def 包括(cls, Ta):
...         return isinstance(Ta, cls)
...
>>> def 一起玩(人们):
...     if 所有(男人.包括(Ta) for Ta in 人们):
...         print('他们是基友')
...     else:
...         print('他们是朋友')
...
>>> 小攻 = 男人()
>>> 小受 = 男人()
>>> 一起玩([小攻,小受])
他们是基友
>>>
{% endhighlight %}

新的字符串格式化语法
====================

原来的 %s %d %你妹
语法已经不推荐，并且很快会被弃用，新的字符串格式化方法（2.6 版引入）为
str.format 或者内置函数 format 。比如：

{% highlight pycon python3 %}
>>> 三青年 = {'小红':'普通青年','小明':'文艺青年','小亮':'二逼青年'}
>>> '{小红}说我想吃罐头，{小明}说更上一层楼，{小亮}说阿伊呀伊呦。'.format(**三青年)
'普通青年说我想吃罐头，文艺青年说更上一层楼，二逼青年说阿伊呀伊呦。'
>>>
{% endhighlight %}

字典解析和集合解析
==================

有了列表解析，当然也少不了字典解析：

{% highlight pycon python3 %}
>>> {k: v + '青年' for k, v in [('小明', '文艺'), ('小红', '普通'), ('小亮', '二逼')]}
{'小明': '文艺青年', '小红': '普通青年', '小亮': '二逼青年'}
>>>
{% endhighlight %}

还有集合解析：

{% highlight pycon python3 %}
>>> {小吃 for 小吃 in ('豆浆', '油条', '包纸')}
{'油条', '包纸', '豆浆'}
>>>
{% endhighlight %}

有序字典与 configparser
=======================

默认 Python 字典是无序的，不过新引入的 `collections.OrderedDict`
类提供了一种有序字典实现，并且被 configparser 默认使用，现在使用
configparser 类就可以得到有序的 ini 格式配置文件了！

而 configparser 模块现在完全支持使用类字典的方法进行读写了！你妹，[我之前的工作]({% post_url 2010-05-07-python-ordered-dict %})全白做了！

ABC
===

抽象基类（Abstract Base Classes），就是像 C++
里面虚类一样的东西。作为其子类，只有将所有抽象方法都实现，才能实例化。

抽象基类是对 Duck Typing 的补充，由于引入了 `@abstractmethod` ，
`@abstractstaticmethod` ， `@abstractclassmethod` ， `@abstractproperty`
四个修饰符，强制抽象方法必须实现，所以可以一定程度上避免错误，用起来感觉比
Duck Typing 安心一些。

结局
====

以上就是我把 Python 3.0 到 3.2 的 What’s new 看了一遍的成果，总体来说
Python 3 本身变得更加规范，更加灵活，如果你的程序不依赖于 Python 2
特有的库的话，来试试 Python 3 很不错！

结局？结局？结局就是小亮和小红幸福地生活在了一起，小明自己吃豆浆油条包纸。

（完）

