---
title: 批量脱机更新
seo-title: 批量脱机更新
description: 可查看本页以了解如何批量更新所有渠道。
seo-description: 可查看本页以了解如何批量更新所有渠道。
uuid: 9b52c5e7-aa6d-4f55-b23c-8bd923723552
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 5d4ca652-d918-4b2b-b239-a2be9255ef0d
noindex: true
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 8%

---


# 批量脱机更新{#bulk-offline-update}

本节介绍有关批量脱机更新的以下主题：

* **概述**
* **使用批量脱机更新**

>[!CAUTION]
>
>此AEM Screens功能仅在您安装了AEM 6.3功能包3或AEM 6.4屏幕功能包1时可用。
>
>要获取此功能包，您必须联系 Adobe 支持人员并申请访问权限。您获得权限后，就可以从“包共享”下载它。

## 概述 {#overview}

批量脱机更新允许您批量更新所有渠道。 它避免了导航到特定渠道并更新内容的麻烦。 相反，您可以在一分钟内为一个特定项目更新渠道中的所有内容。

您还可以计划此活动一段较低的网络流量。

>[!NOTE]
>
>“批量脱机更新”功能经过优化，可仅更新已修改的渠道。

## 使用批量脱机更新{#using-bulk-offline-update}

您可以从用户界面(UI)中手动使用批量脱机更新，或从OSGi服务中计划批量更新。

### 使用AEM Screens用户界面{#using-aem-screens-user-interface}

请按照以下步骤对AEM Screens项目使用批量脱机更新：

1. 导航到您的AEM Screens项目。
1. 选择项目，然后单击操作栏中的&#x200B;**更新脱机内容**&#x200B;以手动更新渠道内容。

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience Manager Web控制台配置{#adobe-experience-manager-web-console-configuration}

请按照以下步骤对AEM Screens项目使用批量脱机更新：

1. Adobe Experience Manager Web控制台配置。
1. 搜索批量脱机更新服务。

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 添加以下属性：

   **项** 目路径指定AEM Screens项目的路径。路径通常为`/content/screens/<Name of your project>`。

   *例如*,  `/content/screens/we-retail`。通过在AEM Screens下选择任何项目（不要单击该图标），可以在URL中找到此路径。

   >[!NOTE]
   >
   >指定相对于您的渠道的项目路径。

   **计划** 频率指定此服务应更新脱机内容的时间，例如，下午5:00或17:00。

1. 单击&#x200B;**保存**&#x200B;以保存您的设置，您的内容将在指定时间更新。

