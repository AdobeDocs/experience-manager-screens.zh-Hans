---
title: 内容更新为服务
seo-title: 内容更新为服务
description: 可查看本页以了解“内容更新为服务”。
seo-description: 可查看本页以了解“内容更新为服务”。
uuid: c73126ca-18d0-45b4-bdde-a3653082bfc4
contentOwner: Jyotika syal
translation-type: tm+mt
source-git-commit: 323e2df2419cc65de7bfe88648ffd1dbd3a91aec
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 7%

---


# 内容更新为服务{#content-update-as-a-service}

本节介绍有关将content-as-a-service更新的以下主题：

* **概述**
* **使用批量脱机更新**

>[!CAUTION]
>
>仅当您安装了AEM 6.3功能包3或AEM 6.4屏幕功能包1时，此AEM Screens功能才可用。
>
>要获取此功能包，您必须联系 Adobe 支持人员并申请访问权限。您获得权限后，就可以从“包共享”下载它。

## 概述 {#overview}

批量脱机更新允许您批量更新所有渠道。 它避免了导航到特定渠道并更新内容的麻烦。 相反，您可以在一分钟内更新某个特定项目的渠道中的所有内容。

您还可以计划此活动一段时间，降低网络流量。

>[!NOTE]
>
>“批量脱机更新”功能经过优化，仅更新已修改的渠道。

## 使用批量脱机更新{#using-bulk-offline-update}

您可以从用户界面(UI)手动使用批量脱机更新，或从OSGi服务计划批量更新。

### 使用AEM Screens用户界面{#using-aem-screens-user-interface}

请按照以下步骤对AEM Screens项目使用批量脱机更新：

1. 导航到您的AEM Screens项目。
1. 选择项目，然后单击操作栏中的&#x200B;**更新脱机内容**&#x200B;以手动更新渠道内容。

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience ManagerWeb控制台配置{#adobe-experience-manager-web-console-configuration}

请按照以下步骤对AEM Screens项目使用批量脱机更新：

1. Adobe Experience ManagerWeb控制台配置。
1. 搜索批量脱机更新服务。

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 添加以下属性：

   **项目** 路径指定您的AEM Screens项目的路径。路径通常为`/content/screens/<Name of your project>`。

   *例如*, `/content/screens/we-retail`。通过选择“AEM Screens”下的任何项目（不要单击该图标），可以在URL中找到此路径。

   >[!NOTE]
   >
   >指定相对于渠道的项目路径。

   **计划** 频率指定此服务应更新脱机内容的时间，例如下午5:00或17:00。

1. 单击&#x200B;**保存**&#x200B;以保存设置，您的内容将在指定时间更新。

