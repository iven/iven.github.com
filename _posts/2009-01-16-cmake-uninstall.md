---
title: CMake 项目卸载方法
date: 2009-01-16 13:18
categories:
- Linux
tags:
- c
- cmake
- shell
---

CMake 默认不提供 uninstall 这个 target，想要的话，输入：

{% highlight console %}
# xargs rm < install_manifest.txt
{% endhighlight %}

对于不修改配置的项目足够了。

`manifest.txt` 是CMake生成的安装文件列表。

