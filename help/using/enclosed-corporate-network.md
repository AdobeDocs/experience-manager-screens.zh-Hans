---
title: 封闭式公司网络
description: 封闭式公司网络
exl-id: b8c52e72-86da-4089-ba02-0c643862419f
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 0%

---

# 封闭式公司网络（有线/无线） {#enclosed-corporate-networks}

封闭式企业网络设置适用于小型、大型和企业企业。 从理论上讲，它可以更复杂，逻辑设置如下图所示。

![](/help/using/assets/enclosed-network-1.png)


## 连接AEM Screens Player以直接访问Internet

请按照以下步骤操作，以确保在此配置中正确连接AEM屏幕播放器：

1. 确保每个AEM Screen播放器都连接到路由器网络。
1. 通过调用系统浏览器中的URL来测试Internet连接。

   >[!NOTE]
   >如果收到错误，请检查网络设置。 对于正确的网络连接，基本上有两种选项：
   >* DHCP
   >* 手动IP配置

1. 确保网络适配器设置与路由器设置不匹配，并检查是否未达到网络中可用IP地址的最大数。

1. 检查路由器是否已正确连接到ISP广域网（Internet链路）。 也可以使用标准路由器上的信号LED来识别此连接。
1. 如果URL调用成功，您可以继续安装AEM Screens并注册。 启动AEM Screens。

   >[!NOTE]
   >**疑难解答提示**
   >如果AEM Screens未正确连接并且未显示预期的内容：
   >
   >1. 如果有任何相关限制，请检查Internet路由器防火墙 `TCP/IP Port 80/443`.
   >1. 确保允许使用所有必需的端口。

## 设置封闭式公司网络 {#requirements-enclosed-networks}

随附的公司网络设置可以在逻辑上分为两个块：

* 广域网(WAN)
* 内部局域网(LAN)。

### 广域网 {#wan-connection}

除了网络可达性之外，Internet连接的性能还必须提供足够的带宽来平稳地运行AEM Screens内容更新。
*足够的带宽* 取决于连接的AEM Screens的数量。 它还取决于网络中其他消费者的使用情况，如智能手机、平板电脑、收银机、计算机或来宾Wi-Fi网络。

>[!NOTE]
>
>当您将更多消费者或计算机添加到网络时，所有设备都可以并行访问Internet连接，带宽会线性减少。

### 局域网 {#lan-connection}

除了网络可达性之外，局域网(LAN)的性能还必须提供足够的带宽，以平稳地运行AEM Screens内容更新。

公司组织内的LAN网络通常至少为1000 MBit/s网络，因此有足够的带宽将许多性能良好的设备连接到系统。 在使用其他活动网络组件时，必须要求所有组件都符合网络带宽要求。

例如，网络组件至少应与100 Mbps标准匹配，并与Internet访问/路由器规范提供的带宽匹配。

### 其他公司网络详情 {#other-networks}

公司网络连接了多个设备，被分成多个子网，并且拥有冗余或多路Internet连接，为数千个并发访问提供足够的性能。
此架构已得到简化，大多数情况下都适合客户端可用的环境。

如果设想使用Wi-Fi解决方案将AEM Screens连接到Internet Link，则建议使用如下现代Wi-Fi标准 `IEEE 802.11g` 最起码。 此标准支持高达54 Mbps的连接。 任何 *较新* 标准赞 `802.11h-n` 质量更好。 如果需要使用Wi-Fi中继器，Adobe推荐使用Google Nest Mesh Wi-Fi等网格Wi-Fi接入点技术或类似技术。
其他Wi-Fi重复技术最终导致整个网络的带宽大量丢失。

## 正在下载媒体和资产 {#download}

AEM Screens为数字标牌用户提供了显着的优势。 它下载并在本地保存所有必需的媒体文件，如图像和视频。 当有新内容需要显示在特定显示器上时，就会出现主要的网络流量。

对于正常操作（例如，定义的播放列表在当天频繁更新），当所有文件都保存在播放器上后，可提供接近独立于网络的操作。

对于与传感器或触发器和动态内容存在更多交互的场景，快速可靠的网络连接对于即时屏幕反应至关重要，以确保最佳客户体验。

下表提供了网络连接关键数据的概览。

>[!NOTE]
>该信息允许您通过请求和下载Internet源来查看网络中每台设备的使用情况。 其中每个请求都会增加并延长下载时间。

![](/help/using/assets/enclosed-network-download.png)
