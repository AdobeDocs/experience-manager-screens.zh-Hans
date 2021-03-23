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
feature: 管理屏幕
role: 管理员
level: 中间
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 1%

---


# 从ContentSync过渡到SmartSync {#transitioning-from-contentsync-to-smartsync}

本节概述了SmartSync功能，以及它如何最大限度地减少服务器负载/存储和网络流量以降低成本。

## 概述 {#overview}

SmartSync是AEM Screens使用的最新机制。 它用作当前方法的替换，当前方法用于缓存脱机渠道并将它们交付到播放器。

它同时在服务器端和客户端执行。

**在服务器端**:

* 渠道的内容（包括资源）将缓存在&#x200B;*/var/contentsync*&#x200B;中。
* 缓存通过描述用于显示的可用内容的清单公开给播放器。

**在客户端**:

* Player根据上述生成的清单更新其内容。

### 使用SmartSync的优势{#benefits-of-using-smartsync}

SmartSync功能为您的AEM Screens项目提供了许多优势。 它允许

* 大幅降低网络流量和服务器端存储要求
* 仅当资产丢失或发生更改时，播放器才会智能下载资产
* 服务器端和客户端存储优化

>[!NOTE]
>
>Adobe强烈建议将SmartSync用于AEM Screens项目。

## 从ContentSync迁移到SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>如果您已经安装了AEM 6.3功能包5和AEM 6.4功能包3，则可以为资产启用SmartSync以提高磁盘空间的使用。 要启用SmartSync，请按照以下部分将ContentSync过渡到SmartSync，从而启用SmartSync。
>
>SmartSync可用于具有受支持服务器AEM 6.4.3 FP3的Screens播放器。
>
>请参阅[AEM Screens Player下载](https://download.macromedia.com/screens/)以下载最新播放器。 下表描述了每个平台所需的最低播放器版本：

| **平台** | **支持的最低播放器版本** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

请按照以下步骤将ContentSync过渡到SmartSync:

1. 从ContentSync迁移到SmartSync需要在激活SmartSync之前清除ContentSync缓存。

   使用链接&#x200B;***https://localhost:4502/libs/cq/contentsync/content/console.html***&#x200B;从实例导航到ContentSync控制台，然后单击&#x200B;**清除缓存**，如下图所示：

   ![clear_contensync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >首次使用SmartSync之前必须清除所有内容缓存。

1. 通过AEM实例 — >锤子图标 — > **Operations** —> **Web控制台**&#x200B;导航到&#x200B;**Adobe Experience Manager Web Console Configuration**。

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience Manager Web控制台** 配置打开。搜索&#x200B;*offlinecontentservice*。

   要搜索&#x200B;**Screens Offline Content Service**&#x200B;属性，请按&#x200B;**Command+F**（对于&#x200B;**Mac**）和&#x200B;**Control+F**（对于&#x200B;**Windows**）。

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 单击&#x200B;**保存**&#x200B;以启用&#x200B;**Screens Offline Content Services**&#x200B;属性，因此使用AEM Screens的SmartSync。
1. 启用SmartSync后，您必须导航到您的项目并单击&#x200B;**更新脱机内容** *（从操作栏中），*，如下图所示。

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)