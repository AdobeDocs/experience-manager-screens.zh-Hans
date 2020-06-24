---
title: 标准网络设置简介
description: 此页介绍标准网络设置
translation-type: tm+mt
source-git-commit: 8e62b3fc4ce324e02aaec6fca9df79b1aaf94d72
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# 管理网络流量 {#managing-network-traffic}

网络设置可以具有各种结构。 本节介绍组织网络设置中最常见的网络设置。

本指南重点介绍代理服务器，然后介绍在不同组织内设置的各种网络结构。

>[!NOTE]
>**AEM Screens网络要求&#x200B;**>AEM Screens作为Cloud Service直接与AEM通信，因此需要在两个节点之间建立稳定的连接。 防火墙对商业Internet访问是绝对必需的，作为客户，您必须了解在防火墙和其他IT安全相关网络组件中需要打开哪些通信端口。

## 代理服务器概述 {#proxy-servers}

Internet连接依赖于代理服务器的使用。 代理服务器是在计算机上运行的专用计算机或软件系统，该计算机充当端点设备（例如计算机）和用户或客户端请求服务的另一服务器之间的中介。 代理服务器可以与防火墙服务器位于同一台计算机中，也可以位于单独的服务器上，后者通过防火墙转发请求。

代理服务器的一个优点是它的缓存可以为所有用户服务。 如果经常请求一个或多个因特网站点，则这些站点可能位于代理的缓存中，这会缩短用户响应时间。 代理还可以记录其交互，用于故障排除。

## 了解标准网络设置 {#network-setups}

要实施网络设置，您必须参考以下方案及其优势和部署详细信息。

网络设置有四种主要类型：

1. [直接因特网网络（有线／无线）](/help/using/direct-internet-network.md)
1. [直接移动网络](/help/using/mobile-network.md)
1. [具有移动数据路由器和活动网络组件的移动网络](/help/using/mobile-network-router.md)
1. [封闭的公司网络（有线／无线）](/help/using/enclosed-corporate-network.md)

下表列出了各种网络设置的优缺点：

<table>
 <tbody>
  <tr>
   <td><strong>网络设置</strong></td>
   <td><strong>优势</strong></td>
   <td><strong>缺点</strong></td>
  </tr>
  <tr>
   <td><strong>直接因特网网络（有线／无线）</strong></td>
   <td>轻松而直接地设置<br>适用于中型或大型安装的<br>好选择专用网络可封装少<br>数故障点相<br>对便宜<br>的可扩展性</td>
   <td>强制性Internet数据计划 </td>
  </tr>
    <tr>
   <td><strong>直接移动网络</strong></td>
   <td>易于设置<br>中型或大型安装的最佳选择良好的可扩展性<br>封装的<br>屏幕
</td>
   <td>强制Internet连接</td>
  </tr>
    <tr>
<tr>
   <td><strong>具有移动数据路由器和活动网络组件的移动网络</strong></td>
   <td>易于设置<br>中型或大型安装的最佳选择专用网络<br>可封装少<br>量故障点相对<br>便宜<br>的可扩展性</br></td>
   <td>强制性Internet数据计划</td>
  </tr>
    <tr>

<td><strong>封闭的公司网络（有线／无线）</strong></td>
   <td>高灵活性和可扩展性<br>由于防护线路不同而高度安全封装<br>的网<br>络易于监视和维护可靠<br></td>
   <td>对于网络专家<br>或系统集成商，建议使用复杂且昂贵的</td>
  </tr>
  </tr>
 </tbody>
</table>


