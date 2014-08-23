---
title: Arch Linux 下 texlive 2008 的安装
date: 2009-04-22 09:52
categories:
- Linux
tags:
- arch
- tex
---

最近忙里偷闲，想学学一直放在藏书阁里的 LATEX Notes，于是边看边装 texlive
……

{% highlight console %}
$ pacman -S texlive-bin
{% endhighlight %}

先来个 hello world：

{% highlight latex %}
%hello_world.tex
\documentclass{article}
\begin{document}
Hello, World!
\end{document}
{% endhighlight %}

生成 dvi 文件：

{% highlight console %}
$ latex hello_world
{% endhighlight %}

很无情地给出错误：

> Latex error: I can’t find the format file \`latex.fmt’!

查了半天，发现 texlive-core 才是正主，texlive-bin 只是它的一个依赖，汗……

{% highlight console %}
$ pacman -S texlive-core
{% endhighlight %}

这下终于通过了……

这才明白 texlive 果然是个庞然大物，texlive-bin 就 16M 了，texlive-core
有 50 多M，又安个 texlive-cjk 又是 50M，真不知道 texlive-most 有多大……

以下是某高手解释 tex、latex 等的关系，转自
[这里](http://bbs.ctex.org/viewthread.php?tid=40867) ：

-   tex可理解为一个标准，如C/C++标准，定义基本API；
-   LaTeX是对tex的扩展，封装了一些功能，以便于使用，就像Boost/ACE库之于C++一样；ConTeXt是TeX的另外一个封装库，级别跟LaTeX一样；最早的tex扩展应该是plain
    tex，现在仍然有很多人在使用；
-   pdftex, xetex可以看成是tex的编译器，就像gcc,
    icc之于C/C++；luatex是现在比较新的tex\`编译器’，而knuth
    tex是最早的tex编译器；当然不同的编译器可能有不同的扩展，如xetex对unicode的支持，luatex对内嵌lua脚本的扩展等等。
-   winedt是一个tex编辑器，跟notepad，vim，emacs一样，编辑器而已，只是对latex文件的语法、语义支持强一些；
-   miktex, texlive就像Visual C++，C++
    Builder一样，提供了写tex/latex/context文档所需要的基本的和必要的工具，如tex编译器和常用的宏包，可以理解为集成开发环境；
-   ctex是基于miktex的二次开发，加入了一些中文配置（如CJK/CCT），方便了国内用户使用。如果非要打比方的话，可以理解为“支持中文的linux”。

