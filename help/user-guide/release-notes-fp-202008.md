---
title: 功能包202008的发行说明
description: “请阅读本页以了解2020年9月03日发布的AEM Screens功能包202008的相关信息。”
feature: 功能包
role: Developer
level: Intermediate
exl-id: bd466576-a6d3-494c-82e5-c5326b6e0aca
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 3%

---

# 功能包202008 {#release-notes-for-feature-pack}发行说明

>[!CAUTION]
>
>建议您升级到最新版本的Adobe Experience Manager(AEM)。 Screens为AEM 6.3 Screens平台提供维护支持。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包5。

您可以使用Adobe ID从[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载AEM Screens 6.5.5版的最新功能包。 导航到&#x200B;**Adobe Experience Manager**&#x200B;选项卡，然后搜索&#x200B;**Screens**&#x200B;以获取最新的功能包。

## 发布日期 {#release-date}

AEM Screens功能包202008的发行日期是2020年9月3日。

### 新增功能 {#what-is-new}

* **计划功能板上的时间轴视图**

   时间轴视图允许用户从显示功能板中查看分配给渠道的计划。

   有关更多详细信息，请参阅[时间轴视图](/help/user-guide/channel-assignment-latest-fp.md#timeline-view)。

* **循环计划**

   循环计划允许您为渠道设置循环计划。 为渠道设置多个重复计划。

   有关更多详细信息，请参阅[重复计划](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule)。

* **语音识别功能到AEM Screens**

   语音识别功能允许由语音交互驱动的AEM Screens渠道中的内容更改。

   内容作者可以将显示器配置为启用语音。 此功能旨在允许客户利用语音作为与其显示器进行交互的方法。

   有关更多详细信息，请参阅[语音识别](voice-recognition.md)。

### 已知问题和修复{#known-issues}

如果您使用的是AEM Screens 6.5.5 Service Pack，则必须为Windows或Android播放器设置环境。

将登录令牌Cookie的&#x200B;**SameSite属性从** Lax **设置为**&#x200B;从&#x200B;**Adobe Experience Manager Web控制台的None**
在所有AEM创作实例和发布实例上配置**。**

* 有关更多详细信息，请参阅[实施Windows 10 Player](implementing-windows-player.md#fp-environment-setup)。

* 有关更多详细信息，请参阅[实施Android Player](implementing-android-player.md#fp-environment-setup)。

### 已发布的AEM Screens播放器{#released-aem-screens-players}

为AEM Screens发布的AEM 6.5功能包5发布了以下AEM Screens播放器。

* Chrome OS
* Windows
* Android

#### AEM Screens播放器下载{#aem-screens-player-downloads}

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅&#x200B;**[AEM Screens播放器下载](https://download.macromedia.com/screens/index.html)**。
