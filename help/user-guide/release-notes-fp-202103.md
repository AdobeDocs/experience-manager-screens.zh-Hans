---
title: 功能包202103发行说明
description: 详细了解2021年3月5日发布的AEM Screens功能包202103。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 2%

---

# 功能包202103发行说明 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe建议您升级到Adobe Experience Manager (AEM)的最新版本。 AEM Screens提供了对AEM 6.3 Screens平台的维护支持。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包7。

您可以从以下网站下载AEM Screens 6.5.7版本的最新功能包： [软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。 导航至 **Adobe Experience Manager** 选项卡和搜索 **Screens** 获取标题为 **AEM 6.5 Screens FP7**.

## 发布日期 {#release-date}

AEM Screens功能包202103的发布日期是2021年3月5日。

### 新增功能 {#what-is-new}

* **AEM Screens自动注册播放器**

  手动批量注册数千个播放器非常麻烦，而且增加了时间和成本。 为简化此过程，播放器自动注册功能允许您在AEM中指定预共享密钥。 此密钥可以通过配置文件或移动设备管理(MDM)解决方案预配到播放器中。

  请参阅 [播放器自动注册](/help/user-guide/auto-registration-players.md) 以了解更多详细信息。


* **使用企业移动性管理批量预配Android™ Player**

  批量部署Android™播放器时，手动向AEM注册每个播放器会变得繁琐起来。 强烈建议使用EMM（企业移动性管理）解决方案，例如 `VMWare Airwatch`， `MobileIron`，或 `Samsung Knox` 远程配置和管理部署。 AEM Screens Android™播放器支持行业标准EMM AppConfig以允许远程配置。

  请参阅 [使用企业移动性管理批量预配Android™ Player](/help/user-guide/implementing-android-player.md#implementation) 以了解更多详细信息。


### 错误修复 {#bug-fixes}

* 提高了计算性能 `clientlib` 和 `asset hashes`.

* 如果缓存未失效，则SmartSync迁移会中断播放器。

* 如果分配 *OfflineConfig*.

* 更新至 `Tizen` 由于不支持反向链接策略strict-origin-when-cross-origin而中断的播放器。

* 更改已分配渠道的计划 *重复* 字段损坏了UI。

* 更新离线内容失败，出现查询异常。

* 现在，交互式体验中交互期间过渡之间的时间延迟已得到修复。

* 失败的配置更新请求导致屏幕空白。

### 已发布的AEM Screens Players

已为AEM 6.5 Feature Pack 7发布以下AEM Screens Player：

* Chrome操作系统
* Windows
* Linux®

#### AEM Screens播放器下载

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅 **[AEM Screens播放器下载](https://download.macromedia.com/screens/index.html)**.
