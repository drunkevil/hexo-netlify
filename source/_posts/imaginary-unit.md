title: YouTube上面一个关于虚数单位的视频
date: 2015-04-28 09:31:27
categories: 学习笔记
mathjax: true

---
我们知道，虚数是平方为负数的数。“虚数”这个名词是17世纪著名数学家笛卡尔创制，因为当时的观念认为这是实际中不存在的数字，故其英文名字为imaginary number，意思是想象中的数字。

<!--more-->

一个虚数可表达为：$ib$，其中$b$为实数，$i$为虚数单位，它的基本定义为：$i=\sqrt{-1}$。在物理学中，$i$通常用来表达电流，故一般改为以$j$来表示虚数单位，即：$j=\sqrt{-1}$。



YouTube上面有一个关于虚数单位的[小视频](https://www.youtube.com/watch?v=5iCoBU0o86Q)，视频的作者称，虚数的单位不等于$\sqrt{-1}$，即$j\ne\sqrt{-1}$，我以为是在开玩笑，没想到竟有模有样的给出了反证法的证明过程。

![](http://ww4.sinaimg.cn/mw690/aeba7ac3gw1erkgh4a0w0j20hz0aydh6.jpg)

乍一看，证明过程似乎没有什么破绽。

事实上，他的错误在于第三个等号，即：$\sqrt{(-1)(-1)}=\sqrt{(-1)}\sqrt{(-1)}$，真的能够取等号吗？

我们知道，$\sqrt{(x)(y)}=\sqrt{(x)}\sqrt{(y)}$的成立与否是存在条件的，那就是$x$,$y$均为非负数。视频中忽略了这样的条件。

视频的后面，则得到了正确的结论。即：虚数单位的定义应该为：$j^2=-1$，进而$j =  \pm \sqrt { - 1} $。

![](http://ww2.sinaimg.cn/mw690/aeba7ac3gw1erkgh4tcpyj20hu0axdhb.jpg)

实际上，$j$并不是一个数，而是一个旋转因子。任何一个数与$j$相乘，意味着将这个数在复平面内沿着逆时针方向旋转90度，如下图所示。从这样的角度去理解也许更容易一些。

![](http://ww1.sinaimg.cn/mw690/aeba7ac3gw1erkgh3ukvqj20dh0dcdg6.jpg)




