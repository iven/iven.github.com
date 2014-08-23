---
title: "数字图像处理（四）——均值滤波"
date: 2009-04-21 06:41
categories:
- 编程
tags:
- c
- dip
---

上次提到产生[高斯噪声]({% post_url 2009-04-18-dip-gauss-noise %})的算法，我们知道，[椒盐噪声]({% post_url 2009-04-11-dip-salt-pepper-noise %})是可以通过[中值滤波]({% post_url 2009-04-13-dip-median-filter %})来修复的，[高斯噪声]({% post_url 2009-04-18-dip-gauss-noise %})也可以通过均值滤波来还原。

顾名思义，均值滤波也是构建一个 n\*n
的模板，然后取其平均值来替代模板中间的值。这样做出的效果明显不如用中值滤波修复椒盐噪声的效果好，不过当
n 取很大值的时候，图片看起来像是高斯模糊，不知道是不是一个原理……

看效果，n=3 时：

![](http://lh5.ggpht.com/_6pI9N0iQzXE/Se1skW3GcuI/AAAAAAAAALI/7bDHHe9K-0E/gauss3.jpg?imgmax=800)

n=11 时：

![](http://lh4.ggpht.com/_6pI9N0iQzXE/Se1sxMDGVBI/AAAAAAAAALQ/OMjpJfV6uQk/gauss11.jpg?imgmax=800)

算法更加简单，有以前的基础不成问题：

{% highlight cpp %}
BmpPixmap & BmpPixmap::mean_filter (int n)
{
    assert (n >= 3 && n % 2);int ii, jj, nn, sum [3];
    BmpPixmap *temp = new BmpPixmap (*this);
    for (i = n / 2; i < height - n / 2; i++) {
        for (j = n / 2; j < width - n / 2; j++) {
            for (nn = 0; nn < 3; nn++) {
                sum [nn] = 0;
            }
            /*-----------------------------------------------------------------------------
             *  Calculate the average of the model.
             *-----------------------------------------------------------------------------*/
            for (ii = i - n / 2, nn = 0; ii <= i + n / 2; ii++) {
                for (jj = j - n / 2; jj <= j + n / 2; jj++, nn++) {
                    sum [0] += pdata [ii][jj]->get_blue ();
                    sum [1] += pdata [ii][jj]->get_green ();
                    sum [2] += pdata [ii][jj]->get_red ();
                }
            }
            temp->pdata [i][j]->set (sum [0] / (n * n), sum [1] / (n * n), sum [2] / (n * n));
        }
    }
    return *temp;
}  /* -----  end of method BmpPixmap::mean_filter  ----- */
{% endhighlight %}
