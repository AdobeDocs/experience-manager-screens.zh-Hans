---
title: 功能包202008发行说明
description: 本页介绍功能包202008的发行说明。
translation-type: tm+mt
source-git-commit: f13adf375631e3b7d7d03324458d91d9d55b0f80
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 2%

---


# 功能包202008发行说明 {#release-notes-for-feature-pack}

>[!CAUTION]
>
>建议您升级到最新版Adobe Experience Manager(AEM)。 Screens为AEM 6.3 Screens平台提供维护支持。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包5。

您可以使用您的AEM Screens从软件分发门户下载Adobe ID6.5.5版 [的最新功能](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 包。 导航到 **Adobe Experience Manager** 选项卡并搜 **索Screens** ，获取最新的功能包。

## 发布日期 {#release-date}

AEM Screens功能包202008的发布日期为2020年9月3日。

### 新增功能 {#what-is-new}

* **时间轴视图计划仪表板**

   时间轴视图允许用户从显示视图将分配的计划仪表板到渠道。

   有关更 [多详细信息](/help/user-guide/channel-assignment-latest-fp.md#timeline-view) ，请参阅时间轴视图。

* **循环计划**

   循环计划允许您为渠道设置循环计划。 为渠道设置多个重复计划。

   有关更 [多详细信息](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) ，请参阅重复计划。

* **语音识别功能到AEM Screens**

   语音识别功能允许在由语音交互驱动的AEM Screens渠道中更改内容。

   内容作者可以将显示器配置为启用语音。 此功能旨在允许客户利用语音作为与其显示器交互的方法。

   有关更 [多详细信息](voice-recognition.md) ，请参阅语音识别。

### 已知问题和修复 {#known-issues}

如果您使用的是AEM Screens6.5.5 Service Pack，则必须为Windows或Android播放器设置环境。

在所有AEM **作者和发布实例上，** 将Lax的登录令牌Cookie **的SameSite属** 性 **设置为None** ，从 **Adobe Experience ManagerWeb ConsoleConfiguration** 中将登录令牌Cookies设置为SameSite属性。

* 有关详 [细信息，请参阅实](implementing-windows-player.md#fp-environment-setup) 施Windows 10 Player。

* 有关更 [多详细信息](implementing-android-player.md#fp-environment-setup) ，请参阅实施Android Player。

### 已释放的AEM Screens球员 {#released-aem-screens-players}

已为AEM Screens发布以下AEM Screens播放器，发布了AEM 6.5功能包5。

* Chrome OS
* Windows
* Android

#### AEM Screens播放器下载  {#aem-screens-player-downloads}

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅 **[AEM Screens播放器下载](https://download.macromedia.com/screens/index.html)**。
