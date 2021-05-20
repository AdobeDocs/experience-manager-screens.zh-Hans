---
title: 功能包201907的发行说明
seo-title: 功能包201907的发行说明
description: 请阅读本页以了解2019年7月31日发布的AEM Screens功能包201907的相关信息。
seo-description: 请阅读本页以了解2019年7月31日发布的AEM Screens功能包201907的相关信息。
uuid: e5349c92-d532-4f04-a757-7c4545cdb074
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: release-notes
content-type: reference
discoiquuid: 826d1599-02d1-4d24-b15d-26c1ffee36a2
docset: aem65
feature: 功能包
role: Developer
level: Intermediate
exl-id: 6a05a014-aedf-4261-849d-abf1ce070964
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 2%

---

# 功能包201907 {#release-notes-for-feature-pack}发行说明

>[!CAUTION]
>
>建议您升级到最新版本的Adobe Experience Manager(AEM)。 Screens为AEM 6.3 Screens平台提供维护支持。

AEM Screens发布了AEM 6.4.5功能包5和AEM 6.5.1功能包1，其中包含以下详细信息。

## 发布日期 {#release-date}

AEM Screens功能包201907的发行日期是2019年7月31日。

### 新增功能 {#what-s-new}

* **数据触发器在AEM Screens渠道中推动资产更改**

当接收到由紧急系统触发的事件时，播放器切换到显示紧急信息的频道。 在紧急情况结束之前，该频道只播放。

有关实施，请参阅[紧急渠道](emergency-channel.md)用例。

* **为异步组件启用定位

现在，可以为AEM Screens项目中使用的资产启用定位。

要详细了解如何为AEM Screens项目中的资产启用定位，请参阅[在AEM Screens中配置ContextHub](configuring-context-hub.md)。

在为AEM Screens项目配置ContextHub后，请遵循不同的用例，以了解数据触发的资产如何在不同行业中发挥关键作用：

**[零售库存目标激活](retail-inventory-activation.md)**

**[旅行中心温度激活](local-temperature-activation.md)**

**[酒店预订激活](hospitality-reservation-activation.md)**

* **更新处理程序的改进**

更新处理程序现在解析体验片段并收集与其关联的任何图像、视频或产品。

* **启动项**

启动项允许内容作者创建渠道的未来版本。 借助启动项的帮助，作者可以预览启动项中的每个渠道，并应能够发起审阅请求。 批准者组将收到通知并可批准或拒绝请求。 达到实时日期后，内容将在设备中播放。
有关更多详细信息，请参阅[启动项](launches.md) 。

* **体验片段中的离线配置**

现在，您可以在配置Screens体验片段时添加离线配置（客户端库和静态文件）。 有关更多详细信息，请参阅[使用体验片段](experience-fragments-in-screens.md)。

### 已发布的AEM Screens播放器{#released-aem-screens-players}

以下AEM Screens播放器已发布适用于AEM 6.4.5功能包5和AEM 6.5.1功能包1:

* ChromeOS
* Windows
* Android

#### AEM Screens播放器下载{#aem-screens-player-downloads}

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅[AEM Screens播放器下载](https://download.macromedia.com/screens/)。
