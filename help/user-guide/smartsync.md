---
title: 从ContentSync过渡到SmartSync
seo-title: 从ContentSync过渡到SmartSync
description: 请阅读本页，了解SmartSync功能以及如何从ContentSync迁移到SmartSync。
seo-description: 请阅读本页，了解SmartSync功能以及如何从ContentSync迁移到SmartSync。
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
feature: 管理屏幕
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 1%

---


# 从ContentSync转换到SmartSync {#transitioning-from-contentsync-to-smartsync}

本节概述了SmartSync功能，以及它如何最大限度地减少服务器负载/存储和网络流量以降低成本。

## 概述 {#overview}

SmartSync是AEM Screens使用的最新机制。 它取代了当前用于缓存离线渠道并将其交付到播放器的方法。

它同时在服务器端和客户端执行。

**在服务器端**:

* 渠道的内容（包括资产）缓存在&#x200B;*/var/contentsync*&#x200B;中。
* 缓存通过描述显示屏可用内容的清单向播放器公开。

**在客户端**:

* 播放器会根据上面生成的清单更新其内容。

### 使用SmartSync {#benefits-of-using-smartsync}的好处

SmartSync功能为您的AEM Screens项目提供了许多好处。 它允许

* 大幅降低网络流量和服务器端存储需求
* 仅当资产丢失或发生更改时，播放器才会智能地下载资产
* 服务器端和客户端存储优化

>[!NOTE]
>
>Adobe强烈建议对AEM Screens项目使用SmartSync。

## 从ContentSync迁移到SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>如果您已安装AEM 6.3功能包5和AEM 6.4功能包3，则可以为资产启用SmartSync以提高磁盘空间使用率。 要启用SmartSync，请按照以下部分从ContentSync转换到SmartSync，从而启用SmartSync。
>
>SmartSync可用于具有受支持服务器AEM 6.4.3 FP3的Screens播放器。
>
>请参阅[AEM Screens Player Downloads](https://download.macromedia.com/screens/)以下载最新的播放器。 下表描述了每个平台所需的最低播放器版本：

| **平台** | **支持的最低播放器版本** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

请按照以下步骤从ContentSync迁移到SmartSync:

1. 从ContentSync迁移到SmartSync时，需要先清除ContentSync缓存，然后再激活SmartSync。

   使用链接&#x200B;***https://localhost:4502/libs/cq/contentsync/content/console.html***&#x200B;从实例导航到ContentSync控制台，然后单击&#x200B;**清除缓存**，如下图所示：

   ![clear_contensync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >在首次使用SmartSync之前，必须清除所有内容缓存。

1. 通过AEM实例导航到&#x200B;**Adobe Experience Manager Web控制台配置** —>锤子图标 — > **操作** —> **Web控制台**。

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience Manager Web控制台** 配置打开。搜索&#x200B;*offlinecontentservice*。

   要搜索&#x200B;**Screens Offline Content Service**&#x200B;属性，请按&#x200B;**Command+F**（对于&#x200B;**Mac**）和&#x200B;**Control+F**（对于&#x200B;**Windows**）。

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 单击&#x200B;**Save**&#x200B;以启用&#x200B;**Screens Offline Content Services**&#x200B;属性，从而为AEM Screens使用SmartSync。
1. 启用SmartSync后，必须导航到您的项目并单击&#x200B;**更新离线内容** *（从操作栏中），*，如下图所示。

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)