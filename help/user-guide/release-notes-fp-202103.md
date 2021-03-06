---
title: 功能包发行说明202103
description: 本页重点介绍功能包202103的发行说明。
translation-type: tm+mt
source-git-commit: dfbf904c1f23f7e41a9d65a270c5ca667ddcdb31
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 2%

---


# 功能包的发行说明202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>建议您升级到最新版Adobe Experience Manager(AEM)。 Screens为AEM 6.3 Screens平台提供维护支持。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包7。

您可以使用Adobe ID从[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载AEM Screens 6.5.7版的最新功能包。 导航到&#x200B;**Adobe Experience Manager**&#x200B;选项卡并搜索&#x200B;**Screens**&#x200B;以获取最新的功能包，标题为&#x200B;**AEM 6.5 Screens FP7**。

## 发布日期 {#release-date}

AEM Screens功能包202103的发布日期为2021年3月05日。

### 新增功能 {#what-is-new}

* **AEM Screens播放器自动注册**

   手动批量注册数千个播放器非常繁琐，并增加了时间和成本。 为简化此过程，播放器的自动注册功能允许您在AEM中指定预先共享的密钥，该密钥可以通过配置文件或移动设备管理(MDM)解决方案设置到播放器中。

   有关详细信息，请参阅[播放器的自动注册](/help/user-guide/auto-registration-players.md)。


* **使用企业移动性管理批量配置Android Player**

   批量部署Android播放器时，使用AEM手动注册每个播放器会变得很繁琐。 强烈建议使用VMWare Airwatch、MobileIron或Samsung Knox等EMM（企业移动管理）解决方案来远程配置和管理您的部署。 AEM Screens Android player支持行业标准EMM AppConfig，以允许远程设置。

   有关更多详细信息，请参阅[使用企业移动管理批量配置Android Player](/help/user-guide/using-emm-bulkprovision-android-player.md)。


### 错误修复 {#bug-fixes}

* 改进了计算`clientlib`和`asset hashes`的性能。

* 如果缓存未失效，SmartSync迁移将中断播放器。

* 如果赋值具有&#x200B;*OfflineConfig*，则未创建脱机缓存。

* 对Tizen播放器的更新，由于不支持推荐人策略严格来源时跨来源而中断。

* 更改已分配渠道的计划&#x200B;*重复*&#x200B;字段将中断UI。

* 更新脱机内容失败，查询例外。

* 现在可修复交互式体验中过渡之间在交互过程中的时间延迟。

* 配置更新请求失败导致出现空白屏幕。

### 已发布AEM Screens播放器{#released-aem-screens-players}

为AEM 6.5功能包7发布了以下AEM Screens播放器：

* Chrome OS
* Windows
* Linux

#### AEM Screens Player下载{#aem-screens-player-downloads}

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅&#x200B;**[AEM Screens Player下载](https://download.macromedia.com/screens/index.html)**。
