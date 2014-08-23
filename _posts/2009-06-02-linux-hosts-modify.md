---
title: Linux 下修改 hosts 文件的方法
date: 2009-06-02 15:41
categories:
- Linux
tags:
- twitter
- wall
---

今天的事情，大家都知道了，中国的知道了，外国人知道了，地球人都知道了，我不仔细说了。

目前访问的 twitter
的方法很多，可能吧已经做了详细的介绍，其中最为简单的就是修改 hosts
文件。

这里照顾少数不知道如何修改 hosts 文件的同学，附上方法。

其实很简单，Linux 下 hosts 文件，就在
/etc/hosts，在里面加上下面两行即可：

    168.143.162.100 twitter.com
    168.143.162.100 www.twitter.com

这个方法只能使部分 twitter 客户端好使，比如
TwitterFox，网页还是没有办法浏览的。

完了。

以下内容转载自 [Shellex is Not
ShelleXtend](http://www.sxnsx.com/blah-blah-blah-about-gfw/) ：

    oooooooooooo                       oooo
    `888'     `8                       `888
     888         oooo  oooo   .ooooo.   888  oooo
     888oooo8    `888  `888  d88' `"Y8  888 .8P'
     888    "     888   888  888        888888.
     888          888   888  888   .o8  888 `88b.
    o888o         `V88V"V8P' `Y8bod8P' o888o o888o

      .oooooo.    oooooooooooo oooooo   oooooo     oooo
     d8P'  `Y8b   `888'     `8  `888.    `888.     .8'
    888            888           `888.   .8888.   .8'
    888            888oooo8       `888  .8'`888. .8'
    888     ooooo  888    "        `888.8'  `888.8'
    `88.    .88'   888              `888'    `888'
     `Y8bood8P'   o888o              `8'      `8'
