---
title: Adobe Analytics与AEM Screens集成
seo-title: Adobe Analytics与AEM Screens集成
description: 请阅读本页内容，了解AEM Screens与Adobe Analytics的开箱即用集成，并为您提供播放验证。
seo-description: 请阅读本页内容，了解AEM Screens与Adobe Analytics的开箱即用集成，并为您提供播放验证。
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
feature: 管理屏幕
role: Administrator, Developer
level: Intermediate
exl-id: 92c8c42b-7c1e-4d4a-8662-18c99666e9c6
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---

# Adobe Analytics与AEM Screens集成{#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>仅当您安装了最低版本的AEM 6.4.2功能包2或AEM 6.3.3功能包4时，才提供此AEM Screens功能。

>[!NOTE]
>
>要访问这些功能包中的任何一个，您必须联系Adobe支持并请求获取访问权限。 您可以使用Adobe ID从[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载AEM Screens的最新功能包。

本节涵盖以下主题：

* **概述**
* **架构详细信息**
* **配置属性**

## 概述 {#overview}

***AEM*** 屏幕可利用Adobe Analytics，通过它，您可以实现市场上的一些独特功能 — 跨渠道分析，帮助将位置中显示的内容与其他数据源进行关联。

AEM Screens提供了与Adobe Analytics的开箱即用集成，并为您提供了播放验证。

本节介绍将AEM Screens项目与Adobe Analytics连接时涉及的以下功能：

* 允许按设备进行播放报告验证
* 允许按资产进行播放报告的校样
* 确保捕获所有播放器事件并加盖时间戳
* 如果播放未连接到网络，则确保所有播放器事件都存储在本地
* 允许创建反馈循环，以跟踪一段时间内的播放事件
* 允许系统根据内容作者定义的成功标准修改内容和布局

因此，Adobe Analytics与AEM Screens的集成强制实施以下&#x200B;*目标*:

* 实现数字标牌实施的ROI
* 将Analytics集成为将来支持收集和分析使用信息的基础

## 体系结构详细信息{#architectural-details}

AEM Screens客户希望了解在什么时间显示了哪些内容，以及显示了多长时间（汇总）。 这是标牌解决方案的常见功能。 AEM Screens将利用Adobe Analytics，而不是构建我们自己的分析，通过它，我们可以实现市场上独一无二的功能 — 跨渠道分析可帮助将位置中显示的内容与其他数据源进行关联。

以下架构图说明了Adobe Analytics与AEM Screens的集成：

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## 在AEM Screens中启用Adobe Analytics {#enabling-adobe-analytics-in-aem-screens}

可以从OSGi控制台配置Adobe Analytics设置。

导航到&#x200B;**Adobe Experience Manager Web控制台配置**&#x200B;以配置AEM Screens的Adobe Analytics，如下图所示：

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## 屏幕分析：启用流程{#screens-analytics-enablement-flow}

>[!CAUTION]
>
>在配置资产之前，请联系您的Adobe关系管理器以创建一个票证，以获取&#x200B;**Analytics API密钥**&#x200B;和&#x200B;**Analytics项目**&#x200B;以与AEM Screens一起使用。

![]()

### 配置属性{#configuring-the-properties}

>[!CAUTION]
>
>在配置资产之前，请联系您的Adobe关系管理器以创建一个票证，以获取&#x200B;**Analytics API密钥**&#x200B;和&#x200B;**Analytics项目**&#x200B;以与AEM Screens一起使用。

下表重点介绍了配置Adobe Analytics for AEM Screens的属性及其说明：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong>Analytics URL</strong></td>
   <td>用于从播放器发布分析数据的URL。 <br>
   对于开发/暂存</em>  - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>适用于生产</em>  - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Analytics API密钥</strong></td>
   <td>用于验证Adobe Analytics服务器（由帐户管理器提供）的API密钥。</td>
  </tr>
  <tr>
   <td><strong>Analytics项目</strong></td>
   <td>AEM Screens项目，该项目在您的analytics中配置为接收数据（由帐户管理器提供）。</td>
  </tr>
  <tr>
   <td><strong>环境</strong></td>
   <td><p>暂存或生产环境（选择暂存或生产）。</p></td>
  </tr>
  <tr>
   <td><strong>Analytics发送频率</strong></td>
   <td>从播放器发送分析数据的频率（以分钟为单位）。 默认情况下，此时间设置为15分钟。</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>默认情况下， **Analytics发送频率**&#x200B;为15分钟。

#### 在AEM Screens中使用Adobe Analytics服务{#using-adobe-analytics-service-in-aem-screens}

此方案通过固件中分析服务以及仪器屏幕核心组件中的REST调用Analytics API，以明确创建和发送特定用例的事件，同时允许可扩展性，在该可扩展性中，任何自定义消息都可以从自定义开发的渠道发送到Analytics。

Analytics事件会离线存储在indexedDB中，稍后进行分块并发送到云。

>[!NOTE]
>
>要详细了解&#x200B;***Sequing***&#x200B;和&#x200B;***事件标准数据模型***，请参阅&#x200B;**[为AEM Screens配置Adobe Analytics](configuring-adobe-analytics-aem-screens.md)**。
