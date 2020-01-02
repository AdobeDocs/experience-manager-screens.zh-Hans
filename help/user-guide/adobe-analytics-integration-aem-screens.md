---
title: Adobe Analytics与AEM Screens集成
seo-title: Adobe Analytics与AEM Screens集成
description: 可查看本页以了解AEM Screens与Adobe Analytics的开箱即用集成，并为您提供播放证明。
seo-description: 可查看本页以了解AEM Screens与Adobe Analytics的开箱即用集成，并为您提供播放证明。
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
translation-type: tm+mt
source-git-commit: 3621082c7880e61f659d3bca956159d22d7df6de

---


# Adobe Analytics与AEM Screens集成 {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>仅当您安装了AEM 6.4.2功能包2和AEM 6.3.3功能包4时，此AEM Screens功能才可用。

>[!NOTE]
>要访问这些功能包中的任何一个，您必须联系Adobe支持并请求访问权限。 您获得权限后，就可以从“包共享”下载它。

本节涵盖以下主题：

* **概述**
* **架构细节**
* **配置属性**

## 概述 {#overview}

***AEM Screens利用Adobe Analytics ***，您可以实现市场上独一无二的功能——跨渠道分析可帮助将位置显示的内容与其他数据源关联起来。

AEM Screens提供与Adobe Analytics的开箱即用集成，并为您提供播放证明。

本节介绍将AEM Screens项目与Adobe Analytics连接时涉及的以下功能：

* 允许按设备进行播放报告证明
* 允许按资产进行播放证明报告
* 确保捕获所有播放器事件并加盖时间戳
* 如果播放未连接到网络，则确保所有播放器事件都存储在本地
* 允许创建反馈循环，跟踪一段时间内的播放事件
* 允许系统根据内容作者定义的成功标准修改内容和布局

因此，Adobe Analytics与AEM Screens集成可实现以下 *目标*:

* 通过数字标牌实施实现投资收益
* 将Analytics集成为将来支持收集和分析使用信息的基础

## 架构细节 {#architectural-details}

AEM Screens客户希望了解在什么时间显示了哪些内容以及显示的时间（汇总）。 这是标牌解决方案的常见功能。 AEM Screens将利用Adobe Analytics构建我们自己的分析，而不是构建自己的分析，这样，我们就可以获得市场上独一无二的功能——跨渠道分析可帮助将位置显示的内容与其他数据源关联起来。

以下架构图说明了Adobe Analytics与AEM Screens的集成：

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## 在AEM Screens中启用Adobe Analytics {#enabling-adobe-analytics-in-aem-screens}

可以从OSGi控制台配置Adobe Analytics设置。

导航到 **Adobe Experience Manager Web Console配置** ，为AEM Screens配置Adobe Analytics，如下图所示：

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## 屏幕分析：启用流程 {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>在配置属性之前，请与Adobe关系管理器联系以创建票证以获取 **Analytics API Key** and **Analytics Project** ，以便与AEM Screens一起使用。

![]()

### 配置属性 {#configuring-the-properties}

>[!CAUTION]
>
>在配置属性之前，请与Adobe关系管理器联系以创建票证以获取 **Analytics API Key** and **Analytics Project** ，以便与AEM Screens一起使用。

下表重点介绍了为AEM Screens配置Adobe Analytics的属性及其说明：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong>分析URL</strong></td>
   <td>从播放器发布分析数据的URL。 <br>
   针对开发／阶段</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>For Production</em> - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Analytics API密钥</strong></td>
   <td>用于验证到Adobe Analytics服务器（由帐户管理器提供）的API密钥。</td>
  </tr>
  <tr>
   <td><strong>分析项目</strong></td>
   <td>在您的分析上配置用于接收数据的AEM Screens项目（由帐户管理器提供）。</td>
  </tr>
  <tr>
   <td><strong>环境</strong></td>
   <td><p>舞台或生产环境（选择舞台或生产）。</p></td>
  </tr>
  <tr>
   <td><strong>分析发送频率</strong></td>
   <td>从播放器发送分析数据的频率（以分钟为单位）。 默认情况下，它设置为15分钟。</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>默认情况下， **Analytics发送频率** 为15分钟。

#### 在AEM Screens中使用Adobe Analytics Service {#using-adobe-analytics-service-in-aem-screens}

此方案通过固件和仪器屏幕核心组件中分析服务的REST调用调用Analytics API，以明确创建和发送特定用例的特定事件，同时允许可扩展性，在可扩展性方面，任何自定义消息都可以从自定义开发的渠道发送到Analytics。

分析事件脱机存储在indexedDB中，稍后分组并发送到云。

>[!NOTE]
>
>要进一步了解事 ***件的排序&#x200B;***和标***准数据模型***，请参阅为AEM Screens配 **[置Adobe Analytics](configuring-adobe-analytics-aem-screens.md)**。

