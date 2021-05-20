---
title: 直接Internet访问
description: 直接Internet访问
exl-id: a393ce2f-b774-4cd5-9001-c5cc24d445ae
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---

# 直接Internet网络（有线/无线）{#direct-internet-access}

直接Internet网络包含用于Internet访问的入口接入点，以便访问AEM Screens需要连接的AEM云服务。

AEM Screens通信的标准端口包括：
* `ssl-secured https (TCP Port 443)`

   <br>或者，</br>

* `http (TCP Port 80)`，如果您的特定用例不需要达到该安全级别。

端口可能因您设置的专用AEM配置而异。 在此SetUp中，所有设备都直接连接到您的Internet路由器，如下图所示。

![](/help/assets/direct-access-2.png)

此配置还包括任何Internet服务提供商(ISP)及其Internet线路的Internet接入。 大多数ISP提供的Internet路由器涵盖Internet调制解调器、网络交换机、Wi-Fi接入点、防火墙和其他网络功能（取决于制造商和型号）。

## 将AEM Screens Player连接到Direct Internet Access {#connecting-aem-screens-players}

请按照以下步骤确保在此配置中正确连接AEM屏幕播放器：

1. 确保每个AEM Screen播放器都连接到路由器的网络。
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


## 设置直接访问网络{#requirements-direct}

直接互联网网络在逻辑上分为两个块：

* 广域网

* 局域网

### 广域网{#wan-connection}

除了网络的可达性外，Internet连接的性能还是提供足够的带宽来运行AEM Screens。

** 充分取决于连接的AEM屏幕的数量以及网络内其他用户（如智能手机、平板电脑、收银机、计算机或来宾Wi-Fi网络）的使用情况。

>[!NOTE]
>
>上述所有设备都可同时访问Internet连接，并且当您向网络中添加更多消费者或计算机时，带宽会线性减少。

### 局域网{#lan-connection}

局域网(LAN)的性能，除了网络的可达性外，还提供足够的带宽来运行AEM Screens。

LAN网络通常至少与100 Mbps网络匹配，因此有足够的带宽将许多性能良好的设备连接到系统。
如果设想使用Wi-Fi解决方案将AEM Screens连接到Internet Link，则建议至少使用诸如`IEEE 802.11g`之类的现代Wi-Fi标准。 此标准支持高达54 Mbps的连接。 任何较新的&#x200B;**&#x200B;标准（如`802.11h-n`）都具有更好的质量。

>[!NOTE]
>
>如果需要Wi-Fi中继器，强烈建议使用Google Nest Mesh Wi-Fi或类似的Mesh Wi-Fi接入点。 其他Wi-Fi重复技术最终导致整个网络的带宽严重丢失。

## 下载媒体和资产 {#download}

AEM Screens为数字标牌用户提供了巨大优势。 It可下载并在本地保存所有必需的媒体文件，如图像和视频。 当特定显示屏上显示新内容时，会出现主要网络流量。

例如，对于常规操作，定义的播放列表在一天中经常更新 — 在播放器上保存了所有文件后，即可提供接近网络独立操作的播放列表。

对于与传感器或触发器以及动态内容的交互较多的情况，快速可靠的网络连接对于立即进行屏幕反应以确保最佳客户体验至关重要。

下表提供了网络连接关键数据的概述。

>[!NOTE]
>
>该信息允许您查看请求和下载互联网源的网络中每个设备的使用情况。 每个请求都会累加并延长下载时间。

![](/help/assets/download-times-direct.png)
