---
title: 直接访问Internet
description: 直接访问Internet
translation-type: tm+mt
source-git-commit: 77cf87cbce39a00528b2690d9689861b91e61fc5
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 0%

---


# 直接因特网网络（有线／无线） {#direct-internet-access}

直接因特网网络包含一个用于因特网访问的入口接入点，以便到达AEM Screens需要连接的AEM cloud services。

AEM Screens通信的标准端口为：
* `http (TCP Port 80)`或者，
* `ssl-secured https (TCP Port 443)`

端口可能因您设置的专用AEM配置而异。 在此SetUp中，所有设备都直接连接到您的Internet路由器，如下图所示。

![](/help/assets/direct-access-2.png)

该配置还包括任何Internet服务提供商(ISP)及其Internet线路的Internet访问。 大多数ISP提供的Internet路由器涵盖Internet调制解调器、网络交换机、WIFI接入点、防火墙和其他网络功能（取决于制造商和型号）。

## 将AEM Screens播放器连接到直接Internet访问 {#connecting-aem-screens-players}

按照以下步骤连接此配置中的AEM Screen播放器：

1. 确保每个AEM Screen播放器都连接到路由器网络。
1. 通过在系统浏览器中调用URL来测试Internet连接。

   >[!NOTE]
   >如果收到错误消息，请检查网络设置。正常网络连接基本有两个选项：
   >* DHCP
   >* 手动IP配置


1. 确保“网络适配器设置”与“路由器设置”匹配，并检查网络中是否未达到最大可用IP地址数量。

1. 检查路由器是否正确连接到ISP广域网（Internet链路）。 此外，还可以使用标准路由器上的信号LED来标识。
1. 如果URL调用成功，您可以继续安装AEM Screens并注册。 开始AEM Screens。

   >[!NOTE]
   >**疑难解答提示**
   >如果AEM Screens连接不正常，且不显示预期内容：
   >
   >1. 如果存在任何限制，请检查您的Internet路由器防火墙 `TCP/IP Port 80/443`。
   >1. 确保允许所有需要的端口。


## 设置直接访问网络的要求 {#requirements-direct}

直接因特网网络可以逻辑上分为两个块：

* 广域网

* 局域网

### 广域网 {#wan-connection}

除网络的可达性外，因特网连接的性能是提供足够的带宽来运行AEM Screens。

*足够* ，这取决于已连接AEM屏幕的数量以及网络中其他消费者（如智能手机、平板电脑、收银机、计算机或来宾WIFI网络）的使用情况。

>[!NOTE]
>所有设备都可同时访问Internet连接，当您向网络添加更多消费者或计算机时，带宽会线性减少。

### 局域网 {#lan-connection}

局域网(LAN)的性能，除了网络的可达性外，还提供足够的带宽来运行AEM Screens。

LAN网络通常至少与100 Mbps网络匹配，因此有足够的带宽将许多性能良好的设备连接到系统。
如果设想使用WIFI解决方案将AEM Screens连接到Internet Link，则建议使用现代WIFI标准， `IEEE 802.11g` 如最低标准。 此标准支持高达54 Mbps的连接。 任何 *较新的* “标准” `802.11h-n` 都具有更高的质量。

>[!NOTE]
>如果需要WIFI中继器，我们强烈建议使用Google Nest Mesh WIFI或类似的Mesh WIFI接入点技术。 其他WiFi重复技术最终导致整个网络的带宽大量丢失。

## 下载媒体和资产 {#download}

AEM Screens为数字标牌用户提供了巨大优势。 它下载并本地保存所有必需的媒体文件，如图像和视频。 当特定显示屏上显示新内容时，将发生主要网络流量。

对于正常操作，例如，定义了在一天中频繁更新的播放列表后，当所有文件都保存在播放器上后，此优惠将接近与网络无关的操作。

对于那些与传感器或其他触发器进行更多交互且内容非常动态的用例，快速可靠的网络连接对于立即进行屏幕反应来确保尽可能最佳的客户体验至关重要。

下表提供网络连接密钥数据的概述。

>[!NOTE]
>该信息允许您视图请求和下载因特网源的网络中每个设备的使用情况。 这些请求中的每个请求都会累加并延长下载时间。

![](/help/assets/download-times-direct.png)

