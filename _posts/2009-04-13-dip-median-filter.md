---
title: "数字图像处理（二）——中值滤波"
date: 2009-04-13 14:25
categories:
- 编程
tags:
- c
- dip
---

中值滤波（median filter）是一种有效消除[椒盐噪声]({% post_url 2009-04-11-dip-salt-pepper-noise %})的算法。

基本原理是，对图像中所有点进行遍历，对于每个点，取以其为中心的 n \* n
的矩形区域，对矩形区域中点的灰度值进行排序，取其中间值替换当前点。

这样，如果这个点灰度值与周围点相差较大的话，就可以将其平滑化。

当然，这里要求 n 是个大于 1 的奇数。

在这里，我对算法进行了优化，使只有当前点是矩形区域灰度值的最大或者最小值的时候才进行替换，这样效果好了很多。

原始图像：

![](http://lh5.ggpht.com/_6pI9N0iQzXE/SeNRQ3xSMII/AAAAAAAAAKk/Zt2ZI_RbYtM/lena.jpg?imgmax=800)

椒盐噪声：

![](http://lh4.ggpht.com/_6pI9N0iQzXE/SeNRbrfigzI/AAAAAAAAAKs/2ndKr2WBJFU/output.jpg?imgmax=800)

中值滤波后：

![output2.jpg](http://lh6.ggpht.com/_6pI9N0iQzXE/SeNRjrp0zPI/AAAAAAAAAK0/VTwp1Im6Fks/output2.jpg?imgmax=800)

可以看到，图像损失很小，只有边缘处有小的细节损失。同时，由于所加的噪点比较密集，少数地方仍然有噪点，这是因为矩形区域噪点太多，以至于中值本身也是个噪点了。

源代码：

{% highlight cpp %}
BmpPixmap & BmpPixmap::median_filter (int n)
{
    assert (n >= 3 && n % 2);
    int ii, jj, nn;
    Byte model [3][n * n];
    BmpPixmap *temp = new BmpPixmap (*this);
    for (i = n / 2; i < height - n / 2; i++) {
        for (j = n / 2; j < width - n / 2; j++) {
            /*-----------------------------------------------------------------------------
             *  Put n*n pixels around current pixels to the model.
             *-----------------------------------------------------------------------------*/
            for (ii = i - n / 2, nn = 0; ii <= i + n / 2; ii++) {
                for (jj = j - n / 2; jj <= j + n / 2; jj++, nn++) {
                    model [0][nn] = pdata [ii][jj]->get_blue ();
                    model [1][nn] = pdata [ii][jj]->get_green ();
                    model [2][nn] = pdata [ii][jj]->get_red ();
                }
            }
            /*-----------------------------------------------------------------------------
             *  Sort the model.
             *-----------------------------------------------------------------------------*/
            qsort (model [0], nn, sizeof (Byte), cmp_Byte);
            qsort (model [1], nn, sizeof (Byte), cmp_Byte);
            qsort (model [2], nn, sizeof (Byte), cmp_Byte);
            if (pdata [i][j]->get_blue () == model [0][nn - 1] ||
                    pdata [i][j]->get_blue () == model [0][0] ||
                    pdata [i][j]->get_green () == model [1][nn - 1] ||
                    pdata [i][j]->get_green () == model [1][0] ||
                    pdata [i][j]->get_red () == model [2][nn - 1] ||
                    pdata [i][j]->get_red () == model [2][0])
            {
                temp->pdata [i][j]->set (model [0][nn / 2], model [1][nn / 2], model [2][nn / 2]);
            }
        }
    }
    return *temp;
}  /* -----  end of method BmpPixmap::median_filter  ----- */
{% endhighlight %}
