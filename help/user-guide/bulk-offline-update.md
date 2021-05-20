---
title: 批量离线更新
seo-title: 批量离线更新
description: 可查看本页以了解如何批量更新所有渠道。
seo-description: 可查看本页以了解如何批量更新所有渠道。
uuid: 9b52c5e7-aa6d-4f55-b23c-8bd923723552
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 5d4ca652-d918-4b2b-b239-a2be9255ef0d
noindex: true
feature: 创作屏幕
role: Administrator, Developer
level: Intermediate
exl-id: d0a0b065-798e-4108-86ac-0a1f4e211cfc
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 8%

---

# 批量离线更新{#bulk-offline-update}

本节介绍有关批量离线更新的以下主题：

* **概述**
* **使用批量离线更新**

>[!CAUTION]
>
>仅当您安装了AEM 6.3功能包3或AEM 6.4 Screens功能包1时，才提供此AEM Screens功能。
>
>要获取此功能包，您必须联系 Adobe 支持人员并申请访问权限。您获得权限后，就可以从“包共享”下载它。

## 概述 {#overview}

批量离线更新，允许您批量更新所有渠道。 它避免了导航到特定渠道和更新内容的麻烦。 相反，您可以在一个瞬间更新特定项目的渠道中的所有内容。

您还可以安排此活动的时间，使网络流量降低。

>[!NOTE]
>
>“批量离线更新”功能经过优化，可仅更新已修改的渠道。

## 使用批量离线更新{#using-bulk-offline-update}

您可以从用户界面(UI)中手动使用批量离线更新，或计划从OSGi服务进行批量更新。

### 使用AEM Screens用户界面{#using-aem-screens-user-interface}

请按照以下步骤对AEM Screens项目使用批量离线更新：

1. 导航到您的AEM Screens项目。
1. 选择项目，然后单击操作栏中的&#x200B;**更新离线内容**&#x200B;以手动更新渠道内容。

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience Manager Web控制台配置{#adobe-experience-manager-web-console-configuration}

请按照以下步骤对AEM Screens项目使用批量离线更新：

1. Adobe Experience Manager Web控制台配置。
1. 搜索批量离线更新服务。

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 添加以下属性：

   **项目** 路径指定AEM Screens项目的路径。路径通常为`/content/screens/<Name of your project>`。

   *例如*、  `/content/screens/we-retail`。您可以通过选择AEM Screens下的任何项目（请勿单击图标），在URL中找到此路径。

   >[!NOTE]
   >
   >指定与渠道相关的项目路径。

   **计** 划频度指定时间，例如，下午5:00或17:00，此服务应在该时间更新离线内容。

1. 单击&#x200B;**Save**&#x200B;以保存您的设置，您的内容将在指定时间更新。
