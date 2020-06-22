---
title: 直接访问Internet
description: 直接访问Internet
translation-type: tm+mt
source-git-commit: 88ba9ab26c4ecc3f829f53244117041a9a1fd2b3
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---


# 直接访问Internet {#direct-internet-access}

直接因特网访问设置包含用于因特网访问的入口接入点，以便到达AEM Screens需要连接的AEM cloud services。

AEM Screens通信的标准端口为：
* `http (TCP Port 80)`或者，
* `ssl-secured https (TCP Port 443)`

端口可能因您的专用AEM配置的配置而异。 在此SetUp中，所有设备都直接连接到您的Internet路由器，如下图所示。

![](/help/assets/direct-access-2.png)

该配置还包括任何Internet服务提供商(ISP)及其Internet线路的Internet访问。 大多数ISP提供的Internet路由器涵盖Internet调制解调器、网络交换机、WIFI接入点、防火墙和其他网络功能（具体取决于制造商和型号）。

>[!NOTE]
>**疑难解答提示&#x200B;**>如果AEM Screens连接不正常，且不显示预期内容：
>
>1. 如果存在任何限制，请检查您的Internet路由器防火墙 `TCP/IP Port 80/443`。
>1. 确保允许所有需要的端口，然后重试。


## 设置直接访问网络的要求 {#requirements-direct}

直接接入网络设置可以逻辑上分成两个块。 WAN/Outer World/Internet连接块和内部LAN/局域网。

### WAN/Internet连接 {#wan-connection}

除了已经描述的网络可到达性外，Internet连接的性能还提供了足够的带宽，使AEM Screens能够良好而顺畅地运行。 在详细信息中，“足够”取决于已连接AEM屏幕的数量以及网络中其他用户（如智能手机、平板电脑、收银机、计算机或来宾WIFI网络）的使用情况。
请记住，所有设备都可以同时访问因特网连接，带宽通常线性减少，同时向网络添加更多消费者／计算机。

### LAN连接 {#lan-connection}

除了已描述的网络可通性外，LAN的性能还提供了足够的带宽，使AEM Screens能够良好、顺畅地运行。 如今，局域网通常至少与100MBit/s的网络匹配，因此应该有足够的带宽将许多性能良好的设备连接到系统。
如果设想使用WIFI解决方案将屏幕连接到因特网链接，则建议使用IEEE 802.11g等现代WIFI标准作为最低要求。 此标准支持高达54Mb的连接。 任何 *较新* 的标准（如802.11h-n）都具有更好的质量。 如果需要WIFI中继器，我们强烈建议使用Google Nest Mesh WIFI或类似的Mesh WIFI接入点技术。
其他WiFi重复技术最终导致整个网络的带宽大量丢失。

## 下载媒体和资产 {#download}

AEM Screens为数字标牌用户提供了巨大优势。 它正在下载并本地保存所有必需的媒体文件，如图像和视频。 由于这一概念，当在特定屏幕上显示新内容时，将发生主要网络流量。
对于正常操作，例如，定义了在一天中不经常更改的播放列表后，当所有文件都保存在播放器上后，此优惠将接近与网络无关的操作。
对于那些与传感器或其他触发器进行更多交互且内容非常动态的用例，快速、可靠的网络连接对于立即进行屏幕反应来确保尽可能最佳的客户体验至关重要。

下表提供网络连接密钥数据概述：

![](/help/assets/download-times-direct.png)

>[!NOTE]
>该信息允许您视图请求和下载因特网源的网络中每个设备的使用情况。 因此，每个请求都会累加并延长下载时间。