---
title: "轻松建立 Ubuntu/Debian 源镜像"
date: 2009-05-03 06:35
categories:
- Linux
tags:
- cron
- debian
- shell
- tofree
- ubuntu
---

服务器上的源是 Debian 的，考虑到学校里面已经没有多少人使用
Debian，而使用 Ubuntu
来做推广显然更加合适，同学们遇到什么问题，也可以得到更好的支持，于是决定把
Debian 源换成 Ubuntu 的。

建立源，当然要用 rsync ，不过这里并非直接使用，而是用的 Debian
官网提供的一段脚本，叫做 anonftpsync，加上 cron 作为定时任务做成的。

cron 是 Linux
下的计划任务工具，可以按每小时、每天、每星期、每月执行任务，支持多用户多设置，很是方便。往下看之前，确认你安装了
rsync，并且开启了 cron 守护程序。

下面说一下步骤：

首先，建立源目录。如果想放在 FTP 服务器上，应该建立在 FTP 目录里，比如：

{% highlight console %}
$ mkdir /home/ftp/ubuntu
{% endhighlight %}

由于脚本的需要，最好建立一个文件夹来记录最后同步的时间：

{% highlight console %}
$ mkdir -p /home/ftp/ubuntu/project/trace/
{% endhighlight %}

然后建立脚本 anonftpsync。拷贝下面的脚本存放在稳妥位置。

{% highlight bash %}
#! /bin/sh -p
set -e

# EXCLUDE 是你要排除的文件和目录。
EXCLUDE="--exclude *alpha.deb \
    --exclude *alpha.udeb \
    --exclude binary-alpha/ \
    --exclude disks-alpha/ \
    --exclude *-alpha.gz \
    --exclude installer-alpha/ \
    --exclude binary-arm/ \
    --exclude *arm.deb \
    --exclude *arm.udeb \
    --exclude disks-arm/ \
    --exclude *-arm.gz \
    --exclude installer-arm/ \
    --exclude binary-m68k/ \
    --exclude *m68k.deb \
    --exclude *m68k.udeb \
    --exclude disks-m68k/ \
    --exclude *-m68k.gz \
    --exclude installer-m68k/ \
    --exclude binary-hppa/ \
    --exclude *hppa.deb \
    --exclude *hppa.udeb \
    --exclude disks-hppa/ \
    --exclude *-hppa.gz \
    --exclude installer-hppa/ \
    --exclude binary-ia64/ \
    --exclude *ia64.deb \
    --exclude *ia64.udeb \
    --exclude disks-ia64/ \
    --exclude *-ia64.gz \
    --exclude installer-ia64/ \
    --exclude binary-mips/ \
    --exclude *mips.deb \
    --exclude *mips.udeb \
    --exclude disks-mips/ \
    --exclude *-mips.gz \
    --exclude installer-mips/ \
    --exclude binary-mipsel/ \
    --exclude *mipsel.deb \
    --exclude *mipsel.udeb \
    --exclude disks-mipsel/ \
    --exclude *-mipsel.gz \
    --exclude installer-mipsel/ \
    --exclude binary-s360/ \
    --exclude *s360.deb \
    --exclude *s360.udeb \
    --exclude disks-s360/ \
    --exclude *-s360.gz \
    --exclude installer-s360/ \
    --exclude binary-s390/ \
    --exclude *s390.deb \
    --exclude *s390.udeb \
    --exclude disks-s390/ \
    --exclude *-s390.gz \
    --exclude installer-s390/ \
    --exclude binary-sh/ \
    --exclude *sh.deb \
    --exclude *sh.udeb \
    --exclude disks-sh/ \
    --exclude *-sh.gz \
    --exclude installer-sh/ \
    --exclude binary-sparc/ \
    --exclude *sparc.deb \
    --exclude *sparc.udeb \
    --exclude disks-sparc/ \
    --exclude *-sparc.gz \
    --exclude installer-sparc/ \
    --exclude /Debian-1.3* \
    --exclude /Debian3.1* \
    --exclude local/ \
    --exclude stable/ \
    --exclude slink-proposed-updates/ \
    --exclude slink/ \
    --exclude bo/ \
    --exclude bo-unstable/ \
    --exclude bo-updates/ \
    --exclude binary-hurd-i386/ \
    --exclude *hurd-i386.deb \
    --exclude *hurd-i386.udeb \
    --exclude disks-hurd-i386/ \
    --exclude *-hurd-i386.gz \
    --exclude installer-hurd-i386/ \
    --exclude binary-powerpc/ \
    --exclude *powerpc.deb \
    --exclude *powerpc.udeb \
    --exclude disks-powerpc/ \
    --exclude *-powerpc.gz \
    --exclude installer-powerpc/ "
#--exclude /contrib/ --exclude /non-free/ --exclude source/\
#    --exclude Incoming/ \
#######################################

# TO 是目标目录
TO=/home/ftp/Ubuntu
# 以下两个合起来就是源地址： debian.ustc.edu.cn/Ubuntu/
# 这里设置同步的服务器域名
RSYNC_HOST=debian.ustc.edu.cn
# 这里是同步服务器上源所在的目录
RSYNC_DIR=Ubuntu/

LOCK="${TO}/Archive-Update-in-Progress-`hostname -f`"

# Get in the right directory and set the umask to be group writable
#
cd $HOME
umask 002

# Check to see if another sync is in progress
if lockfile -! -l 43200 -r 0 "$LOCK"; then
  echo `hostname` is unable to start rsync, lock file exists
  exit 1
fi
trap "rm -f $LOCK > /dev/null 2>&1" exit  

set +e

#result=1
#while (( $result != 0 )) ; do
rsync -rltv --progress --delete \
     --exclude "Archive-Update-in-Progress-`hostname -f`" \
     --exclude "project/trace/`hostname -f`" \
     $EXCLUDE \
     $RSYNC_HOST::$RSYNC_DIR $TO > ${HOME}/log/rsync.log 2>&1
#result=$?
#done

date -u > "${TO}/project/trace/`hostname -f`"
savelog ${HOME}/log/rsync.log > /dev/null 2>&1
{% endhighlight %}

设置权限。确定脚本可以被执行，目标目录有写权限。

{% highlight console %}
$ chmod +x anonftpsyncchmod 755 /home/ftp/ubuntu
{% endhighlight %}

添加计划任务。这里使用 crontab 设置，-e 选项表示编辑设置：

{% highlight console %}
$ crontab -e
{% endhighlight %}

输入下面的一行，表示每天凌晨 2:00 运行
/usr/local/bin/anonftpsync，添加完毕保存：

    00 2 * * *   /usr/local/bin/anonftpsync

使用下面的命令查看是否添加成功：

{% highlight console %}
$ crontab -l
{% endhighlight %}

重启 cron。更改完设置需要重启 cron，通常是：

{% highlight console %}
# /etc/init.d/cron restart
{% endhighlight %}

Arch Linux 下是：

{% highlight console %}
# /etc/rc.d/crond restart
{% endhighlight %}

接下来就是等待咯，如果你迫不及待，可以直接运行脚本同步。

可以看到，建立一个 Ubuntu/Debian 源并没有如何麻烦，这不得不归功于 linux
下工具和脚本的强大，呵呵～

如果有教育网的同学，可以加这个源，现在还在同步中，呵呵～每天从中国科技大学同步一次。从这里下载源列表： ftp://tofree.org/sources.list/

如果对 cron 不够明白，可以参考： [计划任务工具 cron
的配置和说明](http://www.linuxsir.org/main/?q=node/209)

