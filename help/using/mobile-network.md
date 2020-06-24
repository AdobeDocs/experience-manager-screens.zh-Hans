---
title: 直接移动网络
description: 本页介绍“直接移动网络设置”
translation-type: tm+mt
source-git-commit: 8e62b3fc4ce324e02aaec6fca9df79b1aaf94d72
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---


# 直接移动网络 {#mobile-network-setup}

AEM Screens播放器也可以使用运行至少3G网络的移动或蜂窝网络进行连接。

在AEM Screens中，所需内容将物理下载到播放器控制器或计算机，并正确存储在基础操作系统中。 因此，给定的带宽仅影响初始下载时间，而不影响显示器的性能。

AEM Screens播放器与蜂窝3/4/5G的连接连接到您的移动服务数据提供者。 此设置的好处是，移动路由器可放置在优化位置，以确保最佳的可用网络覆盖。 这通常处于一个高开的位置，尽可能地优化周围的混凝土或金属结构。

此SetUp允许AEM Screen用户极大的灵活性，因为无需固定连接即可连接到AEM Screens。

下图显示了直接移动网络设置，它包含一个单一网络连接段，即每个播放器与移动／蜂窝数据网络的连接。

![](/help/using/assets/direct-mobile-1.png)

## 将AEM Screens播放器连接到直接移动网络 {#connecting-aem-screens-players}

按照以下步骤连接此配置中的AEM Screens播放器：

1. 确保每个AEM Screen播放器都连接到路由器网络。

1. 通过在系统浏览器中调用URL来测试Internet连接。

   >[!NOTE]
   >如果收到错误消息，请检查网络设置。正常网络连接基本有两个选项：
   >* DHCP
   >* 手动IP配置


1. 确保“Network Adapter Setting（网络适配器设置）”与“Router（路由器）”设置匹配。

1. 检查路由器是否正确连接到ISP广域网（Internet链路）。这也可以使用标准路由器上的信号LED进行标识。

1. 如果URL调用成功，您可以继续安装AEM Screens并注册。 开始AEM Screens。

   >[!NOTE]
   >**疑难解答提示**
   >如果AEM Screens连接不正常，且不显示预期内容：
   >
   >1. 如果存在任何限制，请检查您的Internet路由器防火墙 `TCP/IP Port 80/443`。
   >1. 确保允许所有需要的端口。



## 设置移动网络设置的要求 {#requirements-direct}

网络设置可以在两个块中逻辑地分开：

* 移动Internet连接

* 局域网

### 移动Internet连接 {#mobile-internet-connection}

除网络可达性外，Internet连接的性能还提供足够的带宽，以便顺利地运行AEM Screens。

*足够* ，这取决于已连接AEM屏幕的数量以及网络中其他消费者（如智能手机、平板电脑、收银机、计算机或来宾WIFI网络）的使用情况。

>[!NOTE]
>所有设备都可同时访问因特网连接，并且带宽线性减少，同时增加更多消费者或计算机到网络。

数据网络提供标准带宽：

**3G**
* 42 Mbps

**4G**
* 150 Mbps

**5G**
* 1000 Mbps-10000 Mbps

在考虑应使用哪个数据网络时，建议您回答以下问题：

* 有多少台客户端连接到路由器？

* 需要进行多少次内容更改，这些平均文件大小是多少？

>[!NOTE]
>需要的数据包至少必须是：
`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>确保有足够的缓冲区。
>对于媒体文件的初始上传，例如，在集成新播放器时，需要有更多数据和更长的下载时间，并反映在上述假设中。覆盖范围 *好* 、数 *据无限* 的4G网络应与此网络设置中最常见的安装相匹配。


### 局域网 {#lan-connection}

局域网(LAN)的性能除了网络的可到达性外，还提供足够的带宽来平稳地运行AEM Screens。 LAN网络通常至少与100 Mbps网络匹配，因此应该有足够的带宽将许多性能良好的设备连接到系统。

使用其他活动网络组件时，必须使所有组件都与网络带宽要求相匹配。 例如，网络组件应至少匹配100 Mbps标准，并匹配Internet访问／路由器规范提供的带宽。

## 下载媒体和资产 {#download}

AEM Screens为数字标牌用户提供了巨大优势。 它下载并本地保存所有必需的媒体文件，如图像和视频。 因此，当特定屏幕上显示新内容时，会出现主要网络流量。
对于正常操作，例如，在播放器上保存所有文件后，在一天中不频繁更新的已定义播放列表会优惠接近与网络无关的操作。
对于那些与传感器或其他触发器进行更多交互且内容非常动态的用例，快速可靠的网络连接对于立即进行屏幕反应来确保尽可能最佳的客户体验至关重要。

下表概述了网络连接关键数据，这些数据负责预期的性能和潜在等待时间。

>[!NOTE]
>所有信息都指请求和下载因特网源的网络中每个设备的消耗。 这些请求中的每个请求都会累加并延长下载时间。

![](/help/using/assets/download-times-mobile.png)



