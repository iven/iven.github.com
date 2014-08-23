---
title: "使用 PolicyKit 进行身份认证（下）"
date: 2009-03-13 05:32
categories:
- Linux
- 编程
tags:
- c
- policykit
---

PolicyKit 的配置文件
====================

分析完了[PolicyKit的机制]({% post_url 2009-03-12-policykit %})，我们来看一下它的配置文件是如何书写的。

PolicyKit
的配置文件藏在哪里呢？我们来进入/usr/share/PolicyKit/policy这个目录，怎么样，是不是看到很多.policy文件？（不要告诉我你没装
PolicyKit ……）

好的，打开其中的org.freedesktop.hal.storage.policy这个文件，你可能会看到下面的内容：

{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN" "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>
    <action id="org.freedesktop.hal.storage.mount-fixed">
        <description>Mount file systems from internal drives.</description>
        <message>System policy prevents mounting internal media</message>
        <defaults>
            <allow_inactive>no</allow_inactive>
            <allow_active>auth_admin_keep_always</allow_active>
        </defaults>
    </action>
    <action id="org.freedesktop.hal.storage.mount-removable">
        <description>Mount file systems from removable drives.</description>
        <message>System policy prevents mounting removable media</message>
        <defaults>
            <allow_inactive>no</allow_inactive>
            <allow_active>yes</allow_active>
        </defaults>
    </action>
</policyconfig>
{% endhighlight %}

我们来依次分析一下：

-   id: id 是对 PolicyKit 中 Action
    的唯一标识，可以看到，各个域从大到小，用圆点分隔。从下图我们可以看出，这是一种树形结构。
-   description:
    这个是注释，没什么好说的，让读配置文件的人知道这个选项的意义。
-   message:
    这个就是前面提到的说明字符串了，强烈推荐写上，让使用者明白他在验证什么操作，以免引发安全隐患。
-   defaults:
    关键的地方到了！这里可以写上对于请求者是否为活动状态的三种情况（allow\_any、allow\_inactive、allow\_active）返回的值。

defaults 可以返回的值有以下几种：

-   no
-   auth\_self\_one\_shot
-   auth\_self
-   auth\_self\_keep\_session
-   auth\_self\_keep\_always
-   auth\_admin\_one\_shot
-   auth\_admin
-   auth\_admin\_keep\_session
-   auth\_admin\_keep\_always
-   yes

这个实在没有什么可说的，它们的作用从字面上理解就可以了……如果不懂还是好好学学英语吧……

好了，说了这么多，可能大家还是不知道怎么使用 PolicyKit
编程吧？其实最简单的办法还是看手册啊！什么，你想要例子？看下
[这里](http://hal.freedesktop.org/docs/PolicyKit-gnome/PolKitGnomeAction.html)
吧！呵呵，相信懂得原理的你，再看这个例子的时候就不会那么吃力，很快就能应用
PolicyKit 进行编程了吧？

（全文完）

