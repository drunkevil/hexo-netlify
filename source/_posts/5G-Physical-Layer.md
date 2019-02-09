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

## 3、38.211：物理信道和调制

物理层的核心协议之一，详细介绍了物理层的帧结构，物理资源，上下行信道信号的产生过程等。

NR与LTE系统都基于OFDM传输。两者主要有两点不同：

（1）LTE只支持一种子载波间隔15KHz，而NR目前支持5种子载波间隔配置；

（2）LTE上行采用基于DFT预编码的CP-Based OFDM，而NR上行可以采用基于DFT预编码的CP-Based OFDM，也可以采用不带DFT的CP-Based OFDM。

211协议主要包含下面内容：

### 3.1、帧结构：

帧，子帧，时隙等。

![](http://www.sharetechnote.com/html/5G/image/NR_Numerology_FrameStructure_u_1__NormalCP_38_211_01.png)

### 3.2、物理资源

天线端口，时频资源格，RB，RE，载波带宽。

### 3.3、通用函数 

各种调制方式、序列产生方式，OFDM时域信号。

### 3.4、物理层上行信道/信号：

PUSCH加扰、调制、层映射、预编码、资源映射等；

PUCCH Format0-4序列产生、加扰、调制、预编码和映射；

PRACH序列产生和资源映射；

DM-RS、PT-RS和SRS信号产生和映射等。

### 3.5、物理层下行信道/信号：

PDSCH加扰、调制、层映射、天线端口映射、资源映射等；

PDCCH CCE，加扰、调制和资源映射等；

PBCH加扰、调制和资源映射等；

DM-RS，PT-RS，CSI-RS参考信号的产生和映射；

SSS和PSS同步信号的产生和映射。



## 4、38.212：复用和信道编码

212协议主要包含下面内容：

### 4.1、传输信道与物理信道的映射关系       

### 4.2、信道编码相关流程

CRC计算，分段和CRC添加；

信道编码方式：Polar码，LDPC码，小码块的编码；

速率匹配等。

### 4.3、上行传输信道和控制信息

上行共享信道（UL-SCH）:CRC添加，LDPC Graph选择，分段与CRC添加，信道编码，速率匹配，码块拼接，数据和控制信心的复用；

上行控制信息（PUCCH上传输）：UCI信息产生，分段和CRC添加，信道编码，速率匹配，码块拼接，复用；

上行控制信息（PUSCH上传输）：UCI信息产生，分段和CRC添加，信道编码，速率匹配，码块拼接，复用。

 ### 4.4、下行传输信道和控制信息

广播信道：序列产生，加扰，CRC添加，信道编码，速率匹配；

下行共享信道和寻呼信道：CRC添加，LDPC Graph选择，分段和CRC添加，信道编码，速率匹配，码块拼接；

下行控制信道：DCI格式，CRC添加，信道编码，速率匹配。







## 5、38.213：物理层过程（控制）

213协议主要包含下面内容：

1.       同步流程：小区搜索，传输时间调整，辅小区激活时间

2.       无限链路监视：UE需要监视主小区的链路质量

3.       链路重配流程

4.       上行功率控制

5.       随机接入流程

6.       UE报告控制信息流程：

HARQ-ACK码本判决（CBG-based HARQ-ACK，Type-1 HARQ-ACK，Type-2 HARQ-ACK）

在上行控制信道上报告UCI

在上行共享信道上报告UCI

7.       UE接收控制信息流程

8.       UE-Group公共信令：时隙配置信令，非连续传输指示，SRS切换

9.       带宽相关操作

10.       UE监视Type0-PDCCH公共搜索区域





## 6、38.214：物理层过程（数据）

214协议主要包含下面内容：

1.     下行功率控制

2.     物理下行共享信道相关流程

UE接收PDSCH信号流程：传输方案，资源分配（时域，频域），调制方式确定和对应码率等（TBS表格），资源映射（RB层次和RE层次），UE接收下行参考信号；

UE发送CSI信道流程：CSI信息框架，报告配置，基于PUCCH和PUSCH传输；

UE PDSCH处理时间。

3.      物理上行共享信道相关流程

UE发送PUSCH信号流程：传输方案（基于码本传输，非码本传输），资源分配（时域，频域），变换预编码（Transform precoding），调制方式确定和对应码率等；

UE参考信号流程：DM-RS，PT-RS，SRS；

UE PUSCH 调频流程；

UE PUSCH准备过程时间。





## 7、38.215：物理层测量

215协议主要包含下面内容：

1. UE测量能力

2. NR-RAN测量能力