---
title: "数字图像处理（三）——高斯噪声"
date: 2009-04-18 06:05
categories:
- 编程
tags:
- c
- dip
---

与[椒盐噪声]({% post_url 2009-04-11-dip-salt-pepper-noise %})相似，高斯噪声（gauss
noise）也是数字图像的一个常见噪声，产生该噪声的算法也很简单。

上次说过，椒盐噪声是出现在随机位置、噪点深度基本固定的噪声，高斯噪声与其相反，是几乎每个点上都出现噪声、噪点深度随机的噪声。

该噪声效果如下：

![](http://lh3.ggpht.com/_6pI9N0iQzXE/SeyM2QR9MsI/AAAAAAAAAK8/Osi6dBVOMOI/output.jpg?imgmax=800)

这个算法比较简单，需要注意，颜色值不要超出范围（0–255），不然效果很可怕……

代码如下：

{% highlight cpp %}
BmpPixmap & BmpPixmap::gauss (int level)
{
    assert (level >= 0);
    BmpPixmap *temp = new BmpPixmap (*this);
    int k, rand_temp, pixel [3];
    /*-----------------------------------------------------------------------------
     *  Init the random seed with time.
     *-----------------------------------------------------------------------------*/
    srand (time (NULL));
    /*-----------------------------------------------------------------------------
     *  Salt & Pepper.
     *-----------------------------------------------------------------------------*/
    for (i = 0; i < height; i++) {
        for (j = 0; j < width; j++) {
            rand_temp = rand () % level - level / 2;
            pixel [0] = temp->pdata [i][j]->get_blue () + rand_temp;
            pixel [1] = temp->pdata [i][j]->get_green () + rand_temp;
            pixel [2] = temp->pdata [i][j]->get_red () + rand_temp;
            for (k = 0; k < 3; k++) {
                if (pixel [k] < 0) {
                    pixel [k] = 0;
                } else if (pixel [k] > 255) {
                    pixel [k] = 255;
                }
            }
            temp->pdata [i][j]->set (pixel [0], pixel [1], pixel [2]);
        }
    }
    return *temp;
}  /* -----  end of method BmpPixmap::gauss  ----- */
{% endhighlight %}
