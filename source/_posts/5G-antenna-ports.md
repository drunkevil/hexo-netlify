title: 5G NR 笔记（3）：天线端口
date: 2019-3-13 18:38:27
categories: 无线通信

---

从LTE到5G NR，最难以理解的概念大概是天线端口（Antenna Ports）了。

<!--more-->

在5G NR协议38.211中，天线端口的定义是：

> An antenna port is defined such that the channel over which a symbol on the antenna port is conveyed can be inferred from the channel over which another symbol on the same antenna port is conveyed.

标准的3GPP式定义：相当的精炼。起初我在LTE时曾经默默地读过很多遍这句话，却还是不理解到底说的是什么意思。

后来终于有了一点的理解。

1. 天线端口是指能进行信道估计分辨的端口数，即与参考信号有关。
2. 每个天线端口对应一套资源格（Resourse Grid），以及对应的参考信号图案。
3. 天线端口是从接收者的角度定义的（下行的接收是UE，上行的接收是基站），一个端口对于接收者来说是一个独立的天线信道。
4. 天线端口是一个逻辑上的概念，与实际的物理天线没有一一对应的关系，二者之间的映射关系由各个厂商自己实现，协议并没有规定。

在5G NR协议中，每种物理信道和参考信号对应的端口号如下。

| Channel/Signal | Antenna Ports                      |
| -------------- | ---------------------------------- |
| PDSCH          | Antenna   ports starting with 1000 |
| PDCCH          | Antenna   ports starting with 2000 |
| CSI-RS         | Antenna   ports starting with 3000 |
| SS/PBCH        | Antenna   ports starting with 4000 |
| PUSCH/DMRS     | Antenna   ports starting with 0    |
| SRS            | Antenna   ports starting with 1000 |
| PUCCH          | Antenna   ports starting with 2000 |
| PRACH          | Antenna   port 4000                |



