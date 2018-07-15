title: LTE-Advanced之载波聚合
date: 2015-07-28 20:33:12
categories: 学习笔记

---

[LTE-Advanced](http://www.3gpp.org/technologies/keywords-acronyms/97-lte-advanced)是LTE的演进版本，是3GPP为了满足IMT-Advanced的要求而推出的标准。

<!--more-->

LTE-Advanced要求下行峰值速率达到1Gbit/s，上行峰值速率达到500Mbit/s。为了支持这样的峰值速率，根据香农极限定理，需要提供最大100 MHz的传输带宽。然而在实际中很少有连续这么大的可用频谱资源，LTE-A提出了载波聚合（Carrier Aggregation, CA）的解决方案。

## 一. 基本原理

所谓载波聚合，简单来说就是将两个或更多的分量载波（Component Carrier, CC）聚合在一起以产生较宽的传输频带资源。

打个比方：原本只能在一条大道（频谱）上运输的某批货物（某UE的数据），由于货物太多或者时间很紧，没有合适的一条很宽的通道。现在通过载波聚合能够在多条道路（CCs）上同时运输这批货物。这样，某个时段可以运输的货物量（throughputs）就得到了明显提升。每条道路的路况可能不同（频点、带宽等），路况好的就多运点，路况差的就少运点，最终完成了整体的运输任务。

![][1]

除了提高系统传输速率，载波聚合带来的好处还有，有效利用离散的频谱资源，并可通过跨载波调度支持异构网络的部署，而异构网络则是下一代无线网络架构的核心之一。

在LTE系统中，每个分量载波（CC）的最大带宽为20MHz，而LTE-A支持最大带宽100MHz的传输。

考虑到系统下行和上行有不同的峰值速率要求，以及数据业务的传输特点，上下行的载波段的大小可以不同，聚合的载波段的数目也可以不同。

## 二. 分类

为了高效地利用零碎的频谱资源，载波聚合支持不同CC之间的聚合，如下图所示，分别为：

- 同一频带内，连续的分量载波；
- 同一频带内，非连续的分量载波；
- 不同频带内的分量载波。

![][2]

其中，第一种又称为连续载波聚合，后两者成为离散载波聚合。从基带(baseband)实现角度来看，这几种情况没有区别，其主要影响RF实现的复杂性。相比于离散CA技术，连续CA更容易实施资源分配和管理算法。

## 三. 典型场景

##### 1.

在分量载波（CC）是相同或者不同的频段，但是频率间隔很小的情况下，eNodeB如图分布，对于所有分量载波波束方向和模式是相同的。

![][3]

##### 2.

根据载波扇区数目部署的不同或者为了提高边缘吞吐量，对于不同的分量载波，eNodeB的天线波束方向和部署不同。

![][4]

##### 3.

一个固定的eNodeB提供宏覆盖，离基站较远的地方放置热点（提供另一个载频），热点小区通过光纤跟基站相连。宏小区与热点小区的载波聚合。实际上就是一个典型的异构网络。

![][5]

## 四. 实现方案

##### 1.连续载波聚合：

对于连续载波聚合来说，系统实现较为容易，信令开销小，UE需要检测的频点也较少，更容易使用一套RF和FFT设备完成多个频带数据的连续接收，节省终端的成本。目前主要有下面三种方案：

方案1：

如图所示，只有中间载波段的中心频点为100kHz的整数倍，其它载波段的中心频点不在100kHz的整数倍。每个载波段由100个资源块组成，带宽18.015MHz。LTE遗留的UE只能接入中间的载波段。

![][6]

方案2：

在载波段之间插入19个子载波(285 kHz)，保证每个载波段的中心频点都是100kHz的整数倍，在频带聚合的两端的保护带宽会相应减少。

![][7]

方案3：

适当减少每个载波段的带宽，减少其中子载波数目，并保证每个载波的中心频点是100kHz的整数倍。新的带宽需要在协议中定义，UE的复杂度和兼容性都需要被重新考虑。

![][8]

##### 2.离散载波聚合：

实际中很少有连续这么大（100MHz）的可用频谱资源，很多的可用频带资源都是离散的，因此，离散载波聚合更加实用。但其实现难度也较连续载波聚合增加很多，一些新的资源分配和调度算法需要重新设计。

一种可行的指导方案是：各个子载波可以根据各自不同的配置选择不同的传送等级，使用独立的链路自适应技术，并根据实际链路情况采用不同的调制编码方案。





## 五. 其他问题

1. 不同频带相差的传播损耗不同频率高的路径损耗大；

2. 不同频带多普勒频移和相干时间相差很大；

3. 切换以及功率控制；

4. 终端复杂度的问题；

5. 小区边缘接收问题。

## 六. 参考链接

- 雒秦川：[LTE-Advanced系统的多载波聚合技术研究][9]
 
- 金辉_LTE的博客：[LTE之载波聚合][10]
 
- 百度文库：[载波聚合介绍][11]

- YouTube：[LTE Advanced Carrier Aggregation][12]

- 3GPP：[Carrier Aggregation explained][13]


  [1]: http://ww3.sinaimg.cn/mw690/aeba7ac3jw1euioebvtjdj211s0a1q5u.jpg
  [2]: http://ww2.sinaimg.cn/mw690/aeba7ac3jw1euirelgk6pj20fr06h74i.jpg
  [3]: http://ww4.sinaimg.cn/mw690/aeba7ac3jw1euipcweu5lj20l306uaai.jpg
  [4]: http://ww2.sinaimg.cn/mw690/aeba7ac3jw1euipcx8oqdj20i10620su.jpg
  [5]: http://ww4.sinaimg.cn/mw690/aeba7ac3jw1euipcy8lnkj20ig06emxg.jpg
  [6]: http://ww2.sinaimg.cn/mw690/aeba7ac3jw1euipqhieefj20s60bq0tn.jpg
  [7]: http://ww4.sinaimg.cn/mw690/aeba7ac3jw1euipqilxz2j20uc0e13zm.jpg
  [8]: http://ww4.sinaimg.cn/mw690/aeba7ac3jw1euipqjml0aj20tb0dedgw.jpg
  [9]: https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CCsQFjABahUKEwiGj4GF5_3GAhVTm4gKHVXUBpc&url=http://www.paper.edu.cn/download/downPaper/201012-755&ei=nXK3VcbMENO2ogTVqJu4CQ&usg=AFQjCNF1zoOJ4nnLrnjSmkuGkq4e474Wxg&sig2=HxaBWJ6Bh6YRk-Snd6GY9w
  [10]: http://blog.sina.com.cn/s/blog_927cff01010181t7.html
  [11]: http://wenku.baidu.com/view/ae529e3987c24028915fc3de.html
  [12]: https://www.youtube.com/watch?v=6bsGJEQX3SM
  [13]: http://www.3gpp.org/technologies/keywords-acronyms/101-carrier-aggregation-explained