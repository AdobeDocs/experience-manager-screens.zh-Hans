---
title: 直接访问Internet
description: 直接访问Internet
exl-id: a393ce2f-b774-4cd5-9001-c5cc24d445ae
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---

# 直接互联网网络（有线/无线） {#direct-internet-access}

直接Internet网络包含一个入口访问点，用于访问Internet，以访问AEM Screens必须连接到的AEMCloud Service。

用于AEM Screens通信的标准端口包括：

* `ssl-secured https (TCP Port 443)`
  <br>或，</br>

* `http (TCP Port 80)`，如果您的特定用例不需要该级别的安全性。

端口可能会因您的专用AEM配置设置的配置而异。 在此设置中，所有设备都直接连接到Internet路由器，如下图所示。

![](/help/assets/direct-access-2.png)

该配置还包括任何互联网服务提供商(ISP)及其互联网线路对互联网的访问。 大多数ISP都提供Internet路由器，涵盖Internet调制解调器、网络交换机、Wi-Fi接入点、防火墙和其他网络功能（具体取决于制造商和型号）。

## 连接AEM Screens Player以直接访问Internet

请按照以下步骤操作，以确保在此配置中正确连接AEM屏幕播放器：

1. 确保每个AEM Screen播放器都连接到路由器的网络。
1. 通过调用系统浏览器中的URL来测试Internet连接。

   >[!NOTE]
   >如果收到错误，请检查网络设置。 对于正确的网络连接，基本上有两种选项：
   >* DHCP
   >* 手动IP配置

1. 确保网络适配器设置与您的路由器设置相匹配；检查是否未达到网络中可用IP地址的最大数目。
1. 检查路由器是否已正确连接到ISP广域网（Internet链路）。 或者，也可以使用标准路由器上的信号LED进行识别。
1. 如果URL调用成功，您可以继续安装AEM Screens并注册。 启动AEM Screens。

   >[!NOTE]
   >**疑难解答提示**
   >如果AEM Screens未正确连接并且未显示预期的内容：
   >
   >1. 如果对`TCP/IP Port 80/443`有任何限制，请检查Internet路由器防火墙。
   >1. 确保允许使用所有必需的端口。

## 设置直接互联网网络 {#requirements-direct}

Direct Internet Network在逻辑上分为两个块：

* 广域网

* 局域网

### 广域网 {#wan-connection}

Internet连接的性能除了网络可达性之外，还在于提供足够的带宽来运行AEM Screens。

*足够*&#x200B;取决于连接的AEM Screens的数量。 它还取决于网络中其他消费者的使用情况，如智能手机、平板电脑、收银机、计算机或访客Wi-Fi网络。

>[!NOTE]
>
>上述设备可以并行访问Internet连接，当您将更多消费者或计算机添加到网络时，带宽会线性减少。

### 局域网 {#lan-connection}

局域网(LAN)的性能除了网络的可达性外，还在于提供足够的带宽来运行AEM Screens。

LAN网络通常至少与100-Mbps网络匹配，因此有足够的带宽将许多性能良好的设备连接到系统。
如果设想使用Wi-Fi解决方案将AEM Screens连接到Internet Link，则建议至少使用`IEEE 802.11g`等现代Wi-Fi标准。 此标准支持高达54 Mbps的连接。 任何&#x200B;*较新的*&#x200B;标准（如`802.11h-n`）的质量更好。

>[!NOTE]
>
>如果需要使用Wi-Fi中继器，Adobe建议使用Google Nest Mesh Wi-Fi等网状无线网络接入点或类似接入点。 其他Wi-Fi重复技术最终导致整个网络的带宽大量丢失。

## 正在下载Media和Assets {#download}

AEM Screens为数字标牌用户提供了显着的优势。 它下载并在本地保存所有必需的媒体文件，如图像和视频。 当有新内容需要显示在特定显示器上时，就会出现主要的网络流量。

对于正常操作（例如，定义的播放列表在当天频繁更新），当所有文件都保存在播放器上后，可提供接近独立于网络的操作。

对于与传感器或触发器和动态内容存在更多交互的场景，快速可靠的网络连接对于即时屏幕反应至关重要，以确保最佳客户体验。

下表提供了网络连接关键数据的概览。

>[!NOTE]
>
>该信息允许您通过请求和下载Internet源来查看网络中每台设备的使用情况。 其中每个请求都会增加并延长下载时间。

![](/help/assets/download-times-direct.png)
