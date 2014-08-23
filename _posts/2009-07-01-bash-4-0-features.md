---
title: Bash 4.0 新功能概览
date: 2009-07-01 18:27
categories:
- Linux
tags:
- shell
---

Bash 是 Linux 平台下使用最多的 Shell，虽然 Bash 4.0
早已经发布了，然而毕竟是主要版本，各大发行版都对其采用了谨慎的态度。就在昨天（2009.7.1），Arch
将 Bash 加入了 Core 仓库，这意味着 Bash 4 已经被 Arch 认可为稳定版本了。

那么，Bash 4 为我们带来了那些改进呢？我们来看一下。

新的或者改进的命令或关键字
==========================

-   新的 `coproc` 关键字：Bash 4
    引入了“协同进程”（coprocesses）的概念，这允许你在后台打开程序，并与它的输入输出数据流进行交流。
-   新的 `mapfile` 内置命令：直接将文本文件读入到数组里面，它允许你设置读入的行数，还允许指定回调函数，这在显示进度条的时候很有用。
-   对 `case` 关键字的修改：新增
    `;&` 终止符，用于执行下一个动作列表而不是终止 case 结构；新增 `;;&` 终止符，用于继续检测下一个表达式（pattern）。
-   对 `declare` 内置命令的修改：`-p` 现在显示所有已声明的属性和值。`-l`、`-u
` 分别用来声明内容为小写、大写的变量。-c 用于声明标题化的变量。`-A` 用于声明联合数组。
-   对 `read` 内置命令的修改：`-t` 指明超时时间，可以是分数。`-i`
    可以用一些文本来预加载输入缓冲区（当启用 readline 时，使用 `-e`）。
-   对 `help` 内置命令的修改：帮助文本的格式更好，更加易读。`-d`
    显示帮助摘要，`-m` 显示 manpage 风格帮助。
-   对 `unlimit` 内置命令的修改：除了 POSIX 模式下的 512
    字节块大小限制之外，新增两种：`-b` 为最大 Socket 缓冲区大小，`-T`
    为最大线程数。

扩展（Expansions）
==================

-   大括号扩展：产生一行数字的时候允许前置 0。
-   参数扩展：通过添加操作符，使参数在扩展时改变大小写。
-   子字符串扩展：当在位置参数中使用子字符串扩展时，以 0 开始的索引将使
    `$0` 前缀在列表中，而不是以前的 `$1`。
-   文件名替换：新的 Shell 选项 `globstar`，将对 `**`
    进行递归的文件名替换；新选项 `dirspell` 将启用文件夹名拼写修正。

联合数组（Associative Arrays）
==============================

联合数组是一个以任意字符串索引的数组，例如：

{% highlight bash %}
declare -A ASSOCASSOC[First]="first element"
ASSOC[Hello]="second element"
ASSOC[Peter Pan]="A weird guy"
{% endhighlight %}

重定向（Redirection）
=====================

新的 `&>>` 符号将标准输出和标准错误输出追加到指定文件，与 `>>FILE 2>&1`
相同作用。而 `|&` 与 `2>&1 |` 相同作用。

新的 Shell 变量
===============

-   `BASHPID`：包含当前 Shell 的 PID。
-   `PROMPT_DIRTRIM`：指明提示符下未缩短的路径的最高极。

新的 Shell 选项（默认关闭）
===========================

-   `checkjobs`：在 Shell 退出时检查并报告运行中的任务。
-   `compat*`：设置旧版 Shell 兼容性。

杂项
====

在没有找到命令时，Shell 会试图调用 `command_not_found_handle`
这个函数，可以用这个功能显示更友好的出错信息。

`set -e (errexit)` 模式的行为已经发生变化，变得更加直觉化。

via: [Bash 4 - a rough
overview](http://bash-hackers.org/wiki/doku.php/bash4)

相关文章： [Bash 4.0 和 Readline 6.0
发布](http://linuxtoy.org/archives/bash-40-and-readline-60.html) / [Bash
4.0 比较有用的功能](http://bbs.linuxeden.com/viewthread.php?tid=170253)

