---
title: 管理网络流量
description: 本页介绍标准网络设置以及如何管理网络通信。
translation-type: tm+mt
source-git-commit: 173ce977549ed64e3750bb751a8fe1b27e277aa2
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---


# 管理网络流量 {#managing-network-traffic}

网络设置可以具有各种结构。 本节介绍组织内最常见的网络设置和一般方法。

本指南重点介绍代理服务器，然后介绍在不同组织内设置的各种网络结构。

>[!NOTE]
>
>**AEM Screens网络要求**
>
>AEM Screens作为Cloud Service直接与AEM通信，因此需要在两个节点之间建立稳定的连接。 防火墙对商业Internet访问是绝对必需的，作为客户，您必须了解在这些防火墙和其他与IT安全相关的网络组件中需要打开哪些通信端口。

## 代理服务器概述 {#proxy-servers}

Internet连接依赖于代理服务器的使用。 代理服务器是在计算机上运行的专用计算机或软件系统，该计算机充当端点设备（例如计算机）和用户或客户端请求服务的另一服务器之间的中介。 代理服务器可以与防火墙服务器位于同一台计算机中，也可以存在于单独的服务器上，后者通过防火墙转发请求。

代理服务器的一个优点是其缓存可以为所有用户服务。 如果经常请求一个或多个因特网站点，这些站点可能位于代理的缓存中，这进一步缩短了用户响应时间。 代理还可以记录其交互，这可用于故障排除。

当代理服务器收到Internet资源请求（如网页或连接到AEM Publisher时）时，它会扫描其以前称为url的本地缓存。 如果找到该页面，它会将其返回给用户，而不将请求转发给Internet。 如果页面不在缓存中，则代理服务器（充当客户端）代表用户并从Internet中的服务器请求页面。 当返回内容时，代理服务器将其与原始请求相关，并将其转发给用户。

## 了解标准网络设置 {#network-setups}

要实施网络设置，您必须参考以下方案及其优势和部署详细信息。

本指南重点介绍组织内四种不同的网络设置：

* **[直接因特网网络（有线／无线）](/help/using/direct-internet-network.md)**
* **[直接移动网络](/help/using/mobile-network.md)**
* **[具有移动数据路由器和活动网络组件的移动网络](/help/using/mobile-network-router.md)**
* **[封闭的公司网络（有线／无线）](/help/using/enclosed-corporate-network.md)**

下表列出了各种网络设置的优缺点：

| 网络设置 | 优势 | 缺点 |
|--- |--- |--- |
| **直接因特网网络（有线／无线）** | 轻松而直接地进行设<br>置适合中型或大型安装<br>专用网络可封装少<br>量故障点相<br>对便宜<br>的可扩展性 | 强制性Internet数据计划 |
| **直接移动网络** | 易于设<br>置适用于中型或大型安装的最佳选择良好的可<br>伸缩性<br>封装的屏幕 | 强制Internet连接 |
| **具有移动数据路由器和活动网络组件的移动网络** | 易于设<br>置中型或大型安装的最佳选<br>择专用网络可封装少<br>数故障点相<br>对便宜<br>的可扩展性 | 强制性Internet数据计划 |
| **封闭的公司网络（有线／无线）** | 高灵活性和可<br>伸缩性由于不同的防御线路而高度安<br>全封装<br>的网络易于监控和<br>维护可靠 | 复杂且昂贵<br>推荐给网络专家或系统集成商 |