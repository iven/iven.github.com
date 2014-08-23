---
title: "在 blogspot 中设定摘要功能"
date: 2009-04-26 15:21
categories:
- 新闻
tags:
- blog
- css
---

Blogspot
虽然很强大，可是默认支持的功能太少了，比如摘要，很常用的功能，可以在首页只显示博文的一部分，这样首页就可以显示更多的内容啦～可惜
Blogspot 默认不支持……

查了很多资料，还是没有找到比较完美的实现方法，[我的博客](http://www.kissuki.com/)现在使用的这种，原理是用 CSS
把多余的部分隐藏，也就是说，这样对于网页提速没有任何帮助。

网上有一种方法是修改帖子高度的，不过这样实现的效果虽然很整齐，但是有时会出现文字和图片显示一半的效果，个人不推荐这种方法。

下面说下我的做法（注意备份哦～）：

1.  熟练地进入后台，选择布局——修改HTML，在“扩展窗口小部件模板”前打勾。
2.  找到这段代码：

{% highlight html %}
<data:post.body>
{% endhighlight %}

修改为：

{% highlight html %}
<b:if cond='data:blog.pageType == "item"'>
<style>.fullpost{display:inline;}</style>
<p><data:post.body/></p>
<b:else/>
<style>.fullpost{display:none;}</style>
<p><data:post.body/>
<br/>
<b:if cond='data:post.url'>
<a expr:href='data:post.url'><strong>Read More...</strong></a>
<b:else/>
<data:post.title/>
</b:if>
</p>
</b:if>
{% endhighlight %}

3.  在设置——格式设置——帖子模板中，加入以下内容：

{% highlight html %}
<span class="fullpost">
</span>
{% endhighlight %}

4.  以后发布帖子的时候，在\<span
    class=“fullpost”\>和\</span\>之外写摘要部分，在其之间写全文部分即可。

参考：
[<http://free123456.blogspot.com/2007/01/blogger.html>](http://free123456.blogspot.com/2007/01/blogger.html)

