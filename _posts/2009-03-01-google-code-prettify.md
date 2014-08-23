---
title: "使用 google-code-prettify 为 Blogspot 添加代码高亮"
date: 2009-03-01 07:10
categories:
- 新闻
tags:
- blog
- css
- google-code-prettify
---

[Blogspot](http://ivenvd.blogspot.com/)
本身没有代码高亮，pre标签只是一个摆设，对于经常要贴代码的人来说简直不可容忍，怎么办呢？

可以使用
[google-code-prettify](http://code.google.com/p/google-code-prettify/)
为代码添加高亮，参见
[这里](http://google-code-prettify.googlecode.com/svn/trunk/README.html)
。

简单说下方法：

1.在 自定义-布局-修改模板HTML 中，\<head\>和\</head\>之间加入：

{% highlight html %}
<link href="prettify.css" type="text/css" rel="stylesheet" /><script type="text/javascript" src="prettify.js"></script>
{% endhighlight %}

2.在把\<body\>改成

{% highlight html %}
<body onload="prettyPrint()">
{% endhighlight %}

3.修在pre标签到你喜欢的样式，比如：

{% highlight css %}
pre {
    margin: 5px 20px;
    border: 1px dashed #666;
    padding: 5px;
    background: #f8f8f8;
    white-space: pre-wrap;
    /* css-3 */
    white-space: -moz-pre-wrap;  /* Mozilla, since 1999 */
    white-space: -pre-wrap;      /* Opera 4-6 */
    white-space: -o-pre-wrap;    /* Opera 7 */
    word-wrap: break-word;       /* Internet Explorer 5.5+ */
}
{% endhighlight %}

4.现在可以在你的帖子里使用代码高亮了！在“修改Html”标签下：

{% highlight html %}
<pre class="prettyprint">print "Hello world!"</pre>
{% endhighlight %}

参考：
[<http://edwin-chain.blogspot.com/2008/11/how-to-publish-source-code-in.html>](http://edwin-chain.blogspot.com/2008/11/how-to-publish-source-code-in.html)

