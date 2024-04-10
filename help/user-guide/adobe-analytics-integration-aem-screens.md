---
title: Adobe Analytics与AEM Screens集成
description: 关注本页，了解AEM Screens与Adobe Analytics的现成集成，并为您提供播放证明。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 92c8c42b-7c1e-4d4a-8662-18c99666e9c6
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 0%

---

# Adobe Analytics与AEM Screens集成 {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>仅当您安装了AEM 6.4.2 Feature Pack 2或AEM 6.3.3 Feature Pack 4的最低版本时，此AEM Screens功能才可用。 对于AEM Screens Cloud Service客户，请联系您的Adobe关系经理，以在Screens Cloud中启用Adobe Analytics。

>[!NOTE]
>
>要访问这两个功能包中的任何一个，您必须联系Adobe支持部门并请求获取访问权限。 您可以从以下网站下载AEM Screens的最新功能包： [软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。

本节涵盖以下主题：

* **概述**
* **体系结构详细信息**
* **配置属性**

## 概述 {#overview}

***AEM Screens*** 利用Adobe Analytics，借助该功能，您可以实现市场上独一无二的功能 — 跨渠道分析，即帮助将位置中显示的内容与其他数据源相关联。

AEM Screens提供了与Adobe Analytics的现成集成，并为您提供了使用证明。

本节介绍以下与AEM Screens项目与Adobe Analytics的连接相关的功能：

* 允许按设备提供播放报告验证
* 允许按资产提供播放报表的证明
* 确保捕获所有播放器事件并为其添加时间戳
* 如果播放未连接到网络，请确保所有播放器事件都存储在本地
* 允许创建反馈循环，以跟踪一段时间内的播放事件
* 允许系统根据内容作者定义的成功标准修改内容和布局

因此，Adobe Analytics与AEM Screens的集成强制执行以下操作 *目标*：

* 实现数字标牌实施的ROI
* 集成Analytics作为未来支持收集和分析使用信息的基础

## 体系结构详细信息 {#architectural-details}

AEM Screens客户想要了解在哪个时间显示了哪些内容，以及显示时间长短（汇总）。 这是标牌解决方案的常见功能。 AEM Screens不会构建我们自己的分析，而是将利用Adobe Analytics，借助它，我们可以实现市场上独一无二的东西 — 跨渠道分析，它有助于将位置中显示的内容与其他数据源相关联。

以下架构图介绍了Adobe Analytics与AEM Screens的集成：

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## 在AEM Screens中启用Adobe Analytics {#enabling-adobe-analytics-in-aem-screens}

可以从OSGi控制台配置Adobe Analytics设置。

导航到 **Adobe Experience Manager Web控制台配置** 要为AEM Screens配置Adobe Analytics，如下图所示：

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Screens Analytics：启用流 {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>在配置资产之前，请与Adobe关系经理联系以创建票证以获取 **Analytics API密钥** 和 **Analytics项目** 用于AEM Screens。

![]()

### 配置属性 {#configuring-the-properties}

>[!CAUTION]
>
>在配置资产之前，请与Adobe关系经理联系以创建票证以获取 **Analytics API密钥** 和 **Analytics项目** 用于AEM Screens。

下表重点列出了用于为AEM Screens配置Adobe Analytics的属性及其说明：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong>Analytics URL</strong></td>
   <td>用于从播放器发布分析数据的URL。 <br>
   用于开发/暂存</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>用于生产</em> - https://cc-api-data.adobe.io/ingest/<br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Analytics API密钥</strong></td>
   <td>用于向Adobe Analytics服务器进行身份验证的API密钥（由帐户管理器提供）。</td>
  </tr>
  <tr>
   <td><strong>Analytics项目</strong></td>
   <td>在您的Analytics上配置为接收数据的AEM Screens项目（由客户经理提供）。</td>
  </tr>
  <tr>
   <td><strong>环境</strong></td>
   <td><p>暂存或生产环境（选择暂存或生产）。</p></td>
  </tr>
  <tr>
   <td><strong>Analytics发送频率</strong></td>
   <td>从播放器发送分析数据的频率（分钟）。 默认情况下，此时间设置为15分钟。</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>默认情况下， **Analytics发送频率** 是15分钟。

#### 在AEM Screens中使用Adobe Analytics服务 {#using-adobe-analytics-service-in-aem-screens}

此场景通过固件和Instrument Screens核心组件中的Analytics服务中的REST调用调用Analytics API，以明确创建和发送特定于特定用例的事件，同时允许扩展，在这种情况下，任何自定义消息都可从自定义开发的渠道发送到Analytics。

Analytics事件离线存储在indexedDB中，稍后进行分块并发送到云。

>[!NOTE]
>
>要了解有关 ***排序*** 和 ***事件的标准数据模型***，请参见 **[为AEM Screens配置Adobe Analytics](configuring-adobe-analytics-aem-screens.md)**.
