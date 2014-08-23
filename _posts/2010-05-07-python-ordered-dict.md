---
title: "简单实现 Python 有序字典（Ordered Dict）"
date: 2010-05-07 16:16
categories:
- 编程
tags:
- python
---

Python 的 Dict 类型很好用，不过有一点可惜就是它的 keys()
是乱序的，想要用它来保存有序的 key-value
对（比如配置文件）就比较困难，碰巧我的毕设就要用到这样一个类型来存放配置文件，怎么办呢？

搜索了一下，Python 2.7 / 3.1 才有 Ordered Dict 的支持，我总不能去 Python
源码里面拽吧……

还有些方法比较陈旧，继承自 UserDict，不支持 iter\*()
系列方法，虽然不碍事，不过心里还是不舒服。

不过找来找去，还是让我找到了相对比较简洁，功能有符合要求的代码，见下：

{% highlight python %}
from UserDict import DictMixin

class odict(DictMixin):

    def __init__(self):
        self._keys = []
        self._data = {}

    def __setitem__(self, key, value):
        if key not in self._data:
            self._keys.append(key)
        self._data[key] = value

    def __getitem__(self, key):
        return self._data[key]

    def __delitem__(self, key):
        del self._data[key]
        self._keys.remove(key)

    def keys(self):
        return list(self._keys)

    def copy(self):
        copyDict = odict()
        copyDict._data = self._data.copy()
        copyDict._keys = self._keys[:]
        return copyDict
{% endhighlight %}

代码来自
[ActiveState](http://code.activestate.com/recipes/496761-a-more-clean-implementation-for-ordered-dictionary/)
，PSF 许可。

