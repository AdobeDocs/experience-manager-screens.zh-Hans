---
title: 了解代理服务器
seo-title: 了解代理服务器
description: 本页介绍代理服务器
seo-description: 本页介绍代理服务器
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# 标准网络设置简介 {#intro-standard-networks}

网络设置可以具有各种结构。 本节概述在环境中部署的网络结构。 有时从零开始实施不同的设置。

本节重点介绍代理服务器，然后介绍在不同组织中设置的不同网络结构。

## 代理服务器 {#proxy-servers}

代理服务器是在计算机上运行的专用计算机或软件系统，该计算机充当端点设备（例如计算机）和用户或客户端请求服务的另一服务器之间的中间。 代理服务器可以与防火墙服务器位于同一台计算机中，也可以位于单独的服务器上，后者通过防火墙转发请求。

代理服务器的一个优点是它的缓存可以为所有用户服务。 如果经常请求一个或多个因特网站点，这些站点可能位于代理的缓存中，这将缩短用户响应时间。 代理还可以记录其交互，这有助于进行故障排除。

## 了解网络设置 {#network-setups}

要实施网络设置，您必须参考以下有利和有弊的情况。

网络设置有三种主要类型：

1. Internet访问设置
1. 移动网络设置
1. 封闭的公司网络设置

下表列出了各种网络设置的优缺点：

<table>
 <tbody>
  <tr>
   <td><strong>网络设置</strong></td>
   <td><strong>优势</strong></td>
   <td><strong>缺点</strong></td>
  </tr>
  <tr>
   <td><strong>Internet访问设置</strong></td>
   <td>轻松而直接地转到SetUp<br>中型或大型安装的最佳选择<br>专用网络可封装少<br>数故障点相对<br>便宜<br>良好的可扩展性</td>
   <td>必需的适当Internet数据计划</td>
  </tr>
    <tr>
   <td><strong>移动网络设置</strong></td>
   <td>轻松直接进入SetUp<br>中型或大型安装的最佳选择专用网络<br>可封装少<br>数故障点相对<br>便宜<br>良好的可扩展性</br></td>
   <td>必须具备适当的Internet连接</td>
  </tr>
    <tr>
   <td><strong>封闭的公司网络</strong></td>
   <td>高灵活性和可伸<br>缩性由于不同的防御线路而高度安全封装<br>的<br>网络易于监控和维护<br>可靠</td>
   <td>建议使用复杂<br>、昂贵的网络专家或系统集成商</td>
  </tr>
  </tr>
 </tbody>
</table>


