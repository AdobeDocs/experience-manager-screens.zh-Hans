---
title: Adobe Analytics与AEM Screens
seo-title: Adobe Analytics与AEM Screens
description: 可查看本页，了解AEM Screens与Adobe Analytics的开箱即用集成，并为您提供一验证重头戏。
seo-description: 可查看本页，了解AEM Screens与Adobe Analytics的开箱即用集成，并为您提供一验证重头戏。
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 2%

---


# Adobe Analytics与AEM Screens整合{#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>只有安装了AEM 6.4.2功能包2和AEM 6.3.3功能包4，此AEM Screens功能才可用。

>[!NOTE]
>
>要访问这些功能包中的任何一个，您必须联系Adobe支持并请求访问权限。 您获得权限后，就可以从“包共享”下载它。

本节涵盖下列主题：

* **概述**
* **架构细节**
* **配置属性**

## 概述 {#overview}

***AEM*** Screens利用Adobe Analytics，通过它，您可以获得市场上独一无二的功能——跨渠道分析，帮助将位置显示的内容与其他数据源关联起来。

AEM Screens提供与Adobe Analytics的开箱即用集成，并为您提供一个验证。

本节介绍将AEM Screens项目与Adobe Analytics连接时涉及的下列功能：

* 允许按设备验证播放报告
* 允许按资产验证播放报告
* 确保捕获所有播放器事件并加盖时间戳
* 确保当播放未连接到网络时，所有播放器事件都存储在本地
* 允许创建反馈循环，跟踪一段时间内的播放事件
* 允许系统根据内容作者定义的成功标准修改内容和布局

Adobe Analytics因此与AEM Screens一体化执行以下&#x200B;*目标*:

* 通过数字标牌实施实现ROI
* 将Analytics集成为将来支持收集和分析使用信息的基础

## 架构详细信息{#architectural-details}

AEM Screens客户希望了解在什么时间显示哪些内容以及显示时间（汇总）。 这是标牌解决方案的常见功能。 AEM Screens将利用Adobe Analytics，而不是构建自己的分析，这样，我们就能在市场上实现独一无二的功能——跨渠道分析，帮助将位置显示的内容与其他数据源关联起来。

以下架构图解释了Adobe Analytics与AEM Screens的集成：

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## 在AEM Screens启用Adobe Analytics{#enabling-adobe-analytics-in-aem-screens}

可以从OSGi控制台配置Adobe Analytics设置。

导航到&#x200B;**Adobe Experience ManagerWeb控制台配置** ，为AEM Screens配置Adobe Analytics，如下图所示：

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## 屏幕分析：启用流{#screens-analytics-enablement-flow}

>[!CAUTION]
>
>在配置属性之前，请与Adobe关系管理器联系以创建票证，以获取&#x200B;**Analytics API密钥**&#x200B;和&#x200B;**Analytics Project**，以便与AEM Screens一起使用。

![]()

### 配置属性{#configuring-the-properties}

>[!CAUTION]
>
>在配置属性之前，请与Adobe关系管理器联系以创建票证，以获取&#x200B;**Analytics API密钥**&#x200B;和&#x200B;**Analytics Project**，以便与AEM Screens一起使用。

下表重点介绍了为AEM Screens配置Adobe Analytics的属性及其说明：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong>分析URL</strong></td>
   <td>用于从播放器发布分析数据的URL。 <br>
   针对开发／阶段</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em> For Production</em> - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Analytics API密钥</strong></td>
   <td>用于验证到Adobe Analytics服务器（由帐户管理器提供）的API密钥。</td>
  </tr>
  <tr>
   <td><strong>分析项目</strong></td>
   <td>AEM Screens项目在您的分析上配置为接收数据（由客户经理提供）。</td>
  </tr>
  <tr>
   <td><strong>环境</strong></td>
   <td><p>暂存或生产环境（选择暂存或生产）。</p></td>
  </tr>
  <tr>
   <td><strong>分析发送频率</strong></td>
   <td>从播放器发送分析数据的频率（以分钟为单位）。 默认情况下，它设置为15分钟。</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>默认情况下，**Analytics Send Frequency**&#x200B;为15分钟。

#### 在AEM Screens使用Adobe Analytics服务{#using-adobe-analytics-service-in-aem-screens}

此方案通过固件和仪器屏幕核心组件中分析服务的REST调用调用Analytics API，以明确创建和发送特定用例的事件，同时允许可扩展性，在可扩展性方面，任何自定义消息都可以从自定义开发渠道发送到Analytics。

分析事件脱机存储在indexedDB中，稍后分块并发送到云。

>[!NOTE]
>
>要进一步了解&#x200B;***Sequencing***&#x200B;和&#x200B;***事件标准数据模型***，请参阅&#x200B;**[为AEM Screens配置Adobe Analytics](configuring-adobe-analytics-aem-screens.md)**。

