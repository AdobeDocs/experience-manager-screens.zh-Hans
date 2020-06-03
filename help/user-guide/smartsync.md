---
title: 从ContentSync过渡到SmartSync
seo-title: 从ContentSync过渡到SmartSync
description: 可查看本页以了解SmartSync功能以及如何从ContentSync过渡到SmartSync。
seo-description: 可查看本页以了解SmartSync功能以及如何从ContentSync过渡到SmartSync。
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
translation-type: tm+mt
source-git-commit: 112aa2a89578243bad49e61839d781e0f29893b4
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 1%

---


# 从ContentSync过渡到SmartSync {#transitioning-from-contentsync-to-smartsync}

本节概述SmartSync功能，以及它如何最大限度地减少服务器负载/存储和网络流量以降低成本。

## 概述 {#overview}

SmartSync是AEM Screens使用的最新机制。 它替代了当前用于缓存脱机渠道并将它们交付到播放器的方法。

它同时在服务器端和客户端执行。

**在服务器端**:

* 渠道的内容（包括资产）将缓存在 */var/contentsync中*。
* 缓存通过清单向播放器公开，清单描述了用于显示的可用内容。

**在客户端**:

* Player根据以上生成的清单更新其内容。

### 使用SmartSync的优势 {#benefits-of-using-smartsync}

SmartSync功能为您的AEM Screens项目提供了许多优势。 它允许

* 大幅降低网络流量和服务器端存储要求
* 仅当资产缺失或已更改时，播放器才会智能下载资产
* 服务器端和客户端存储优化

>[!NOTE]
>
>Adobe强烈建议对AEM Screens项目使用SmartSync。

## 从ContentSync迁移到SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>如果您已安装AEM 6.3 Feature Pack 5和AEM 6.4 Feature Pack 3，则可以为资产启用SmartSync以提高磁盘空间使用率。 要启用SmartSync，请按照以下部分将ContentSync过渡到SmartSync，从而启用SmartSync。
>
>SmartSync可用于具有受支持服务器AEM 6.4.3 FP3的Screens播放器。
>
>请参阅AEM [Screens播放器下载](https://download.macromedia.com/screens/) ，下载最新播放器。 下表描述了每个平台所需的最低播放器版本：

| **平台** | **支持的最低播放器版本** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

请按照以下步骤从ContentSync过渡到SmartSync:

1. 从ContentSync迁移到SmartSync需要先清除ContentSync缓存，然后再激活SmartSync。

   使用链接https://localhost:4502/libs/cq/contentsync/content/console.html从实例导航到ContentSync控 ***制台*** ，然 **后单击清**&#x200B;除缓存，如下图所示：

   ![clear_contensync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >首次使用SmartSync之前，必须清除所有内容缓存。

1. 通过 **AEM实例** —>锤子图标—>操作—> Web Console导航到 **Adobe Experience Manager****Web Console**。

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience Manager Web Console配置**打开。 搜索 *offlineconnectservice*。

   要搜索“ **Screens脱机内容** Service”属性 **，请按** Command+F **（对于Mac）** 和Control **+F(******&#x200B;对于Windows)。

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 单击 **保存** ，以启用 **Screens Offline Content Services属性** ，因此对AEM Screens使用SmartSync。
1. 启用SmartSync后，必须导航到您的项目并单击“ **更新脱机内容***”（从操作栏中）* ，如下图所示。

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)