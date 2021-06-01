---
title: 封闭式企业网络
description: 封闭式企业网络
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---


# 封闭式公司网络（有线/无线）{#enclosed-corporate-networks}

封闭式企业网络集适用于规模较小、规模较大和企业性的企业。 理论上讲，它可能更复杂，逻辑设置如下图所示。

![](/help/using/assets/enclosed-network-1.png)


## 将AEM Screens Player连接到Direct Internet Access {#connecting-aem-screens-players}

请按照以下步骤确保在此配置中正确连接AEM屏幕播放器：

1. 确保每个AEM Screen播放器都连接到路由器网络。
1. 通过在系统浏览器中调用URL来测试Internet连接。

   >[!NOTE]
   >如果收到错误，请检查网络设置。基本上有两个选项可用于正确的网络连接：
   >* DHCP
   >* 手动IP配置


1. 确保“网络适配器设置”与“路由器设置”匹配，并检查网络中的可用IP地址最大数量是否未达到。

1. 检查路由器是否正确连接到ISP广域网（Internet链路）。 这也可以使用标准路由器上的信号LED来标识。
1. 如果URL调用成功，您可以继续安装AEM Screens并注册。 启动AEM Screens。

   >[!NOTE]
   >**疑难解答提示**
   >如果AEM Screens连接不正确，并且未显示预期内容：
   >
   >1. 如果对`TCP/IP Port 80/443`存在任何限制，请检查您的Internet路由器防火墙。
   >1. 确保允许所有必需的端口。


## 设置封闭的公司网络{#requirements-enclosed-networks}

封闭的公司网络设置可以在逻辑上分为两个块：

* 广域网(WAN)
* 内部局域网(LAN)。

### 广域网{#wan-connection}

除了网络可达性外，Internet连接的性能还必须提供足够的带宽才能顺利地运行AEM Screens内容更新。
*足够* 的带宽取决于连接的AEM屏幕的数量以及网络内其他消费者（如智能手机、平板电脑、收银机、计算机或来宾Wi-Fi网络）的使用情况。

>[!NOTE]
>
>所有设备都具有并发访问Internet连接的权限，并且当您向网络添加更多消费者或计算机时，带宽会线性减少。

### 局域网{#lan-connection}

局域网(LAN)的性能除了网络可达性外，还必须提供足够的带宽才能顺利地运行AEM Screens内容更新。

企业组织内的LAN网络通常至少为1000 MBit/s，因此有足够的带宽将许多性能良好的设备连接到系统。 使用其他活动网络组件时，所有这些组件都必须符合网络带宽要求。

例如，网络组件应至少匹配100 Mbps标准，并匹配Internet访问/路由器规范提供的带宽。

### 其他公司网络详情{#other-networks}

公司网络具有许多连接的设备，被分割成各种子网络，并具有冗余或多路的Internet连接，以便为数千个并发访问提供足够的性能。
此模式已得到简化，并适用于客户端可用的环境。

如果设想使用Wi-Fi解决方案将Screens连接到Internet Link，则建议至少使用诸如`IEEE 802.11g`之类的现代Wi-Fi标准。 此标准支持最高54 Mbps的连接。 任何较新的&#x200B;**&#x200B;标准（如`802.11h-n`）都具有更好的质量。 如果需要Wi-Fi中继器，我们确实强烈建议使用Google Nest Mesh Wi-Fi或类似的Mesh Wi-Fi接入点技术。
其他Wi-Fi重复技术最终导致整个网络的带宽严重丢失。

## 下载媒体和资产 {#download}

AEM Screens为数字标牌用户提供了巨大优势。 It可下载并在本地保存所有必需的媒体文件，如图像和视频。 当特定显示屏上显示新内容时，会出现主要网络流量。

例如，对于常规操作，定义的播放列表在一天中经常更新 — 在播放器上保存了所有文件后，即可提供接近网络独立操作的播放列表。

对于与传感器或触发器以及动态内容的交互较多的情况，快速可靠的网络连接对于立即进行屏幕反应以确保最佳客户体验至关重要。

下表提供了网络连接关键数据的概述。

>[!NOTE]
>该信息允许您查看请求和下载互联网源的网络中每个设备的使用情况。 每个请求都会累加并延长下载时间。

![](/help/using/assets/enclosed-network-download.png)
