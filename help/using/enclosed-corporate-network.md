---
title: 封闭的公司网络
description: 封闭的公司网络
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---


# 封闭的公司网络（有线／无线） {#enclosed-corporate-networks}

封闭式公司网络设置适用于规模较小、规模较大和企业的企业。 理论上可能更复杂，逻辑设置如下图所示。

![](/help/using/assets/enclosed-network-1.png)


## 将AEM Screens播放器连接到直接Internet访问 {#connecting-aem-screens-players}

请按照以下步骤确保此配置中的AEM Screen播放器正确连接：

1. 确保每个AEM Screen播放器都连接到路由器网络。
1. 通过在系统浏览器中调用URL来测试Internet连接。

   >[!NOTE]
   >如果收到错误，请检查网络设置。正常网络连接基本有两个选项：
   >* DHCP
   >* 手动IP配置


1. 确保“网络适配器设置”与“路由器设置”匹配，并检查网络中是否未达到最大可用IP地址数。

1. 检查路由器是否正确连接到ISP广域网（Internet链路）。 此外，还可以使用标准路由器上的信号LED来标识。
1. 如果URL调用成功，您可以继续安装AEM Screens并注册。 开始AEM Screens。

   >[!NOTE]
   >**疑难解答提示**
   >如果AEM Screens连接不正常，并且未显示预期内容：
   >
   >1. 如果对Internet路由器防火墙有任何限制，请检查 `TCP/IP Port 80/443`。
   >1. 确保允许所有必需的端口。


## 建立封闭的公司网络 {#requirements-enclosed-networks}

封闭的公司网络设置可以逻辑上分为两个模块：

* 广域网
* 内部局域网(LAN)。

### 广域网 {#wan-connection}

除了网络可通性外，因特网连接的性能还必须提供足够的带宽，以便顺利地运行AEM Screens内容更新。
*足够的带宽* 取决于已连接AEM屏幕的数量以及网络中其他用户（如智能手机、平板电脑、收银机、计算机或来宾Wi-Fi网络）的使用情况。

>[!NOTE]
>
>所有设备都可同时访问Internet连接，当您向网络添加更多消费者或计算机时，带宽会线性减少。

### 局域网 {#lan-connection}

局域网(LAN)的性能除了网络可通性外，还必须提供足够的带宽，以便顺利地运行AEM Screens内容更新。

企业组织内的LAN网络通常至少为1000 MBit/sec网络，因此有足够的带宽将性能良好的许多设备连接到系统。 使用其他活动网络组件时，必须使所有组件都与网络带宽要求相符。

例如，网络组件应至少匹配100 Mbps的标准，并匹配Internet访问／路由器规范提供的带宽。

### 其他公司网络详情 {#other-networks}

公司网络连接了多个设备，被分离成各种子网络，并具有冗余或多路的因特网连接，为数千个并发访问提供足够的性能。
此模式得到简化，并适合客户端的环境。

如果设想使用Wi-Fi解决方案将Screens连接到Internet Link，则建议使用现代Wi-Fi标准， `IEEE 802.11g` 如最低标准。 此标准支持高达54 Mbps的连接。 任何 *较新的* “标准” `802.11h-n` 都具有更高的质量。 如果需要Wi-Fi中继器，我们强烈建议使用Mesh Wi-Fi接入点技术，如Google Nest Mesh Wi-Fi或类似技术。
其他Wi-Fi重复技术最终导致整个网络的带宽大量丢失。

## 下载媒体和资产 {#download}

AEM Screens为数字标牌用户提供了巨大优势。 它下载并本地保存所有必需的媒体文件，如图像和视频。 当特定显示屏上显示新内容时，将发生主要网络流量。

对于正常操作，例如，定义的播放列表在一天中频繁更新——在所有文件都保存到播放器上后，优惠接近与网络无关的操作。

对于与传感器或触发器以及动态内容交互更多的场景，快速可靠的网络连接对于立即进行屏幕反应来确保最佳客户体验至关重要。

下表提供网络连接密钥数据的概述。

>[!NOTE]
>
>该信息允许您视图请求和下载因特网源的网络中每台设备的使用情况。 这些请求中的每个请求都会累加并延长下载时间。

![](/help/using/assets/enclosed-network-download.png)
