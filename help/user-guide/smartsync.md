---
title: 从ContentSync转换为SmartSync
description: 了解有关SmartSync功能以及如何从ContentSync过渡到SmartSync的更多信息。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b8d0c089-af79-403e-870f-fb46b66fecd3
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# 从ContentSync转换为SmartSync {#transitioning-from-contentsync-to-smartsync}

本节概述SmartSync功能，以及它如何最大限度地减少服务器负载/存储和网络流量以降低成本。

## 概述 {#overview}

SmartSync是AEM Screens使用的最新机制。 它取代了当前用于缓存离线渠道并将其交付给播放器的方法。

它同时在服务器端和客户端执行。

**在服务器端**

* 渠道的内容（包括资产）已缓存在&#x200B;*`/var/contentsync`*&#x200B;中。
* 缓存通过描述用于显示的可用内容的清单向播放器公开。

**在客户端**

* 播放器会根据上面生成的清单更新其内容。

### 使用SmartSync的好处 {#benefits-of-using-smartsync}

SmartSync功能可为您的AEM Screens项目提供以下几项好处：

* 大大减少了网络流量和服务器端存储需求。
* 仅当资产丢失或更改时，播放器才会智能地下载资产。
* 服务器端和客户端存储优化。

>[!NOTE]
>
>Adobe建议您对AEM Screens项目使用SmartSync。

## 从ContentSync迁移到SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>如果您已安装AEM 6.3 Feature Pack 5和AEM 6.4 Feature Pack 3，则可以启用SmartSync for Assets以提高磁盘空间利用率。 要启用SmartSync，请按照以下部分从ContentSync过渡到SmartSync，从而启用SmartSync。
>
>SmartSync适用于Screens Player，以及受支持的服务器AEM 6.4.3 FP3。
>
>查看[AEM Screens播放器下载](https://download.macromedia.com/screens/)以下载最新的播放器。 下表描述了每个平台所需的最低播放器版本：

| **平台** | **最低支持的播放器版本** |
|---|---|
| Android™ | 3.3.72 |
| Chrome操作系统 | 1.0.136 |
| Windows | 1.0.136 |

按照以下步骤从ContentSync过渡到SmartSync：

1. 从ContentSync迁移到SmartSync要求在激活SmartSync之前清除ContentSync缓存。

   使用链接&#x200B;***https://localhost:4502/libs/cq/contentsync/content/console.html***&#x200B;从实例导航到ContentSync控制台，然后单击&#x200B;**清除缓存**，如下图所示：

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >在首次使用SmartSync之前，必须清除所有内容缓存。

1. 通过Adobe Experience Manager实例>锤子图标> **操作** > **Web控制台**&#x200B;导航到&#x200B;**AEM Web控制台配置**。

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience Manager Web控制台配置**&#x200B;打开。 搜索&#x200B;*offlinecontentservice*。

   要搜索&#x200B;**Screens脱机内容服务**&#x200B;属性，请在&#x200B;**Mac**&#x200B;中按&#x200B;**Command+F**，在&#x200B;**Windows**&#x200B;中按&#x200B;**Control+F**。

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 单击&#x200B;**保存**&#x200B;以启用&#x200B;**Screens Offline Content Services**&#x200B;属性，从而为AEM Screens使用SmartSync。
1. 启用SmartSync后，导航到您的项目，然后单击&#x200B;**更新离线内容** *（从操作栏中），*，如下图所示。

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)
