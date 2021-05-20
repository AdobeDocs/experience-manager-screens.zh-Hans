---
title: 功能包202103的发行说明
description: “请阅读本页以了解2021年3月5日发布的AEM Screens功能包202103的相关信息。”
feature: 功能包
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 2%

---

# 功能包202103 {#release-notes-for-feature-pack}发行说明

>[!CAUTION]
>建议您升级到最新版本的Adobe Experience Manager(AEM)。 Screens为AEM 6.3 Screens平台提供维护支持。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包7。

您可以使用Adobe ID从[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载AEM Screens 6.5.7版的最新功能包。 导航到&#x200B;**Adobe Experience Manager**&#x200B;选项卡并搜索&#x200B;**Screens**&#x200B;以获取标题为&#x200B;**AEM 6.5 Screens FP7**&#x200B;的最新功能包。

## 发布日期 {#release-date}

AEM Screens功能包202103的发行日期是2021年3月5日。

### 新增功能 {#what-is-new}

* **AEM Screens播放器自动注册**

   手动批量注册数千个播放器非常麻烦，而且会增加时间和成本。 为简化此过程，播放器的自动注册功能允许您在AEM中指定一个预共享密钥，该密钥可通过配置文件或移动设备管理(MDM)解决方案配置到播放器中。

   有关更多详细信息，请参阅[播放器自动注册](/help/user-guide/auto-registration-players.md)。


* **使用企业移动管理批量配置Android播放器**

   批量部署Android播放器时，使用AEM手动注册每个播放器会很繁琐。 强烈建议使用EMM（企业移动性管理）解决方案（如VMWare Airwatch、MobileIron或Samsung Knox）来远程配置和管理您的部署。 AEM Screens Android播放器支持行业标准EMM AppConfig，以允许进行远程配置。

   有关更多详细信息，请参阅[使用企业移动管理批量配置Android播放器](/help/user-guide/implementing-android-player.md#implementation) 。


### 错误修复 {#bug-fixes}

* 改进了计算`clientlib`和`asset hashes`的性能。

* 如果缓存未失效，则SmartSync迁移会中断播放器。

* 如果赋值具有&#x200B;*OfflineConfig*，则未创建脱机缓存。

* 更新了因反向链接策略crist-origin-when-cross-origin不受支持而中断的Tizen播放器。

* 更改分配渠道的计划&#x200B;*重复项*&#x200B;字段会破坏UI。

* 更新离线内容失败，但出现查询异常。

* 现在可修复交互式体验中交互期间过渡之间的时间延迟。

* 配置更新请求失败，导致出现空白屏幕。

### 已发布的AEM Screens播放器{#released-aem-screens-players}

AEM 6.5功能包7发布了以下AEM Screens播放器：

* Chrome OS
* Windows
* Linux

#### AEM Screens播放器下载{#aem-screens-player-downloads}

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅&#x200B;**[AEM Screens播放器下载](https://download.macromedia.com/screens/index.html)**。
