---
title: "数字图像处理（一）——椒盐噪声"
date: 2009-04-11 14:34
categories:
- 编程
tags:
- c
- dip
---

椒盐噪声（salt & pepper
noise）是数字图像的一个常见噪声，产生该噪声的算法也比较简单。

椒盐，按我的理解，椒就是黑，盐就是白，椒盐噪声就是在图像上随机出现黑色白色的像素。

那么传入两个参数，分别为黑白像素在图像上所占比例，就可以对图像进行修改。

我们可以使用 srand 函数，根据 time
产生一个随机种子（以免每次随机的结果相同），然后使用 rand
函数产生随机数，rand 产生的随机数是 0 到 RAND\_MAX
之间的整数，可以通过使用 double (rand ()) / RAND\_MAX 产生一个 0 到 1
之间的浮点型。

这样，当这个随机数小于 pepper 时，就把该点调黑，大于 1 - salt
时，就把该点调白，就可以产生随机的椒盐噪声了。

效果如图：

![](http://lh3.ggpht.com/_6pI9N0iQzXE/SeCt8QOtbPI/AAAAAAAAAKE/jPKzUWf1ZeM/output.jpg?imgmax=800)

源代码：

{% highlight cpp %}
#include "bmp_pixmap.h"
/*
 *--------------------------------------------------------------------------------------
 *       Class:  BmpPixmap
 *      Method:  salt_pepper
 * Description:  Add salt and pepper noise to the pixmap.
 *--------------------------------------------------------------------------------------
 */
void BmpPixmap::salt_pepper (double salt, double pepper)
{
    double temp;
    /*-----------------------------------------------------------------------------
     *  Salt & Pepper should be between 0 and 1.
     *-----------------------------------------------------------------------------*/
    salt -= int (salt);
    pepper -= int (pepper);
    /*-----------------------------------------------------------------------------
     *  Init the random seed with time.
     *-----------------------------------------------------------------------------*/
    srand (time (NULL));
    /*-----------------------------------------------------------------------------
     *  Salt & Pepper.
     *-----------------------------------------------------------------------------*/
    for (i = 0; i < height; i++) {
        for (j = 0; j < width; j++) {
            temp = double (rand ()) / RAND_MAX;
            if (temp > 1 - salt) {
                pdata [i][j]->set (255, 255, 255);
            } else if (temp < pepper) {
                pdata [i][j]->set (0, 0, 0);
            }
        }
    }
    return ;
}  /* -----  end of method BmpPixmap::salt_pepper  ----- */
{% endhighlight %}
