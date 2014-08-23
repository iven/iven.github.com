---
title: "使用 PolicyKit 进行身份认证（中）"
date: 2009-03-12 15:31
categories:
- Linux
- 编程
tags:
- c
- policykit
---

PolicyKit 的运作流程
====================

在[上次的图中]({% post_url 2009-03-10-policykit %})，我们可以看出 PolicyKit
运作过程中的几个要素：请求发出者（gnome-mount），请求目标（磁盘），请求的动作（挂载）。下面我们来看一下
PolicyKit 的运作流程。

![](http://lh6.ggpht.com/_6pI9N0iQzXE/SbfL7VWVKkI/AAAAAAAAADg/trZ5VX7OnVc/diagram-interaction.png?imgmax=800)

图一：用户点击了磁盘图标，系统通过 DBus 发送请求给 HAL。

图二：HAL收到并验证请求（请求被包装在一个叫做 PolKitCaller
的对象中，包含 uid 、 pid
、会话标识符、会话是否为活动状态、是否远程、远程地址和其他可选信息），并据此构建了
PolKitCaller 对象，之后，HAL 会调用 libpolkit 中的函数
polkit\_context\_can\_caller\_do\_action ()
，并把以上两个结构体作为参数。

根据这个函数传递来的参数，系统会到 PolicyKit
的配置文件（关于配置文件，会在下次说明）中进行验证，根据配置文件的返回值和验证数据库中的内容决定是否允许请求的操作。

可能的返回值有三种：通过（POLKIT\_RESULT\_YES）、拒绝（POLKIT\_RESULT\_NO）、需要验证（POLKIT\_RESULT\_AUTH
系列）。返回值被包含在一个叫做 PolKitResult 的结构体中。

图三：当返回值不是 POLKIT\_RESULT\_YES 时，HAL
把这个返回值外加之前所请求的操作一起返回给请求者。

图四：如果返回值是 POLKIT\_RESULT\_AUTH 系列（例如
POLKIT\_RESULT\_AUTH\_ADMIN\_KEEP\_ALWAYS），顺带返回的还有定义在配置文件里的说明字符串（这样可以识别你正在验证的是什么动作）。

现在文件管理器知道想要随便挂载一个磁盘是不行的了，只好向 Authentication
Agent 求助，说：”快快！帮我做个验证窗口出来！“顺带把刚才 HAL 发给它的
PolKitResult 和 PolKitAction 发给它。

图五：Authentication Agent 收到请求，也跟图二中的 HAL
一样，先验证一下传来的东西是否正确，构建个 PolKitCaller
去配置文件那里验证一下，检查 PolKitResult 是否和文件管理器传过来的一样。

然后 Authentication Agent
听话地构建一个验证窗口，包含之前返回的说明字符串。

图六：如果验证成功，它会让 HAL
去重新请求一下。此时因为验证成功，验证数据库中已经允许了此程序，当然验证通过了！

下次我们来分析一下 PolicyKit 的配置文件。

