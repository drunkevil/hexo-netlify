title: 5G NR 协议学习：物理层
date: 2019-2-9 18:38:27
categories: 学习笔记

---

5G是第五代移动通信的简称，当然，就像4G有另一个名字LTE一样，5G也有另一个名字：NR（New Radio），新空口。

<!--more-->



![](http://wx1.sinaimg.cn/mw690/aeba7ac3gy1fzzzagalqoj20kk0asq30.jpg)

虽然5G的正式商用还没有开始，但是5G第一个版本的标准协议已经在2018年底冻结，本文主要总结了R15协议中物理层的主要内容，方便后续查阅。

首先给出物理层协议的下载地址，3GPP协议的38.2xx系列：

http://www.3gpp.org/ftp/Specs/archive/38_series/

![](http://wx3.sinaimg.cn/mw690/aeba7ac3gy1fzzzakflxvj20r60hx0tg.jpg)

## 1、38.201：概述

物理层的协议是38.2xx系列，其中38.201是物理层的概述，简单介绍了物理层协议的主要内容，包括：多址接入方式，帧结构，物理信道和调整方式，信道编码，物理层处理流程，以及物理层测量等。

除了38.201之外，物理层协议还有另外6个文档，分别详细介绍了上述主要内容，各个协议之间的关系可以用下图表示：

![](http://wx4.sinaimg.cn/mw690/aeba7ac3gy1fzzzanpjnyj20m60e4mxm.jpg)



## 2、38.202：物理层的功能和服务

38.202是物理层协议除了概述之外最短的一个文档，主要介绍了终端侧物理层各个信道的模型和处理流程。

从终端侧到基站侧的上行处理流程如下图所示：

> \-    Higher-layer data passed to/from the physical layer
>
> \-    CRC and transport-block-error indication
>
> \-    FEC and rate matching
>
> \-    Data modulation
>
> \-    Mapping to physical resource
>
> \-    Multi-antenna processing
>
> \-    Support of L1 control and Hybrid-ARQ-related signalling



![](http://wx3.sinaimg.cn/mw690/aeba7ac3gy1fzzzqqqt4gj20sz0fxta3.jpg)

从终端侧到基站侧的上行处理流程如下图所示：

> \-    Higher-layer data passed to/from the physical layer;
>
> \-    CRC and transport-block-error indication;
>
> \-    FEC and rate matching;
>
> \-    Data modulation;
>
> \-    Mapping to physical resource;
>
> \-    Multi-antenna processing;
>
> \-    Support of L1 control and Hybrid-ARQ-related signalling.

![](http://wx3.sinaimg.cn/mw690/aeba7ac3gy1fzzzqw5sblj20t00eyjsp.jpg)

上下行的处理流程基本相同，唯一的差别就是方向相反。