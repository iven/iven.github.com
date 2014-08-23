---
title: "用vim格式化代码"
date: 2009-01-17 08:14
categories:
- Linux
tags:
- c
- vim
---

虽然不是第一次听说，但是第一次用的感觉还是很神奇。

以下转自：
<http://hi.baidu.com/seesea8/blog/item/b96c8e51eb8f352743a75b41.html>

从别的编辑器里粘贴到vim里的代码经常由于不正常的缩进变得格式混乱。在vim的官方FAQ
（ <http://vimdoc.sourceforge.net/cgi-bin/vimfaq2html3.pl> ）找到的：

格式化全文：

    gg=G

自动缩进当前行：

    ==

这个是原文节选：

> 14.6. How do I format/indent an entire file?
>
> You can format/indent an entire file using the gg=G command, where
>
> gg - Goto the beginning of the file
>
> = - apply indentation
>
> G - till end of file
>
> For more information, read
>
> :help gg
>
> :help =
>
> :help G
>
> :help ‘formatprg’
>
> :help C-indenting

