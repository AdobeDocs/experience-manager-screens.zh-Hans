---
title: 内容更新即服务
seo-title: Content Update As a Service
description: 按照本页了解Content Update As a Service。
seo-description: Follow this page to learn about Content Update As a Service.
uuid: c73126ca-18d0-45b4-bdde-a3653082bfc4
contentOwner: Jyotika syal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: de9f669b-9ce7-4d70-99b4-0b69ef3c1af5
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# 内容更新即服务 {#content-update-as-a-service}

本节介绍了有关更新content-as-a-service的以下主题：

* **概述**
* **使用批量脱机更新**

>[!CAUTION]
>
>此AEM Screens功能仅在安装了AEM 6.3 Feature Pack 3或AEM 6.4 Screens Feature Pack 1时才可用。
>
>要访问此功能包，您必须联系Adobe支持部门并请求获取访问权限。 一旦您拥有权限，就可以从包共享下载它。

## 概述 {#overview}

批量脱机更新允许您批量更新所有渠道。 它避免了导航到特定渠道和更新内容的麻烦。 相反，您可以立即为一个特定项目更新渠道中的所有内容。

您也可以将此活动安排在网络流量较低的时间进行。

>[!NOTE]
>
>批量离线更新功能已得到优化，可仅更新那些已修改的渠道。

## 使用批量脱机更新 {#using-bulk-offline-update}

您可以从用户界面(UI)手动使用批量脱机更新，也可以计划从OSGi服务进行批量更新。

### 使用AEM Screens用户界面 {#using-aem-screens-user-interface}

请按照以下步骤对AEM Screens项目使用批量脱机更新：

1. 导航到您的AEM Screens项目。
1. 选择项目并单击 **更新离线内容** 以手动更新渠道内容。

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience Manager Web控制台配置 {#adobe-experience-manager-web-console-configuration}

请按照以下步骤对AEM Screens项目使用批量脱机更新：

1. Adobe Experience Manager Web控制台配置。
1. 搜索批量脱机更新服务。

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 添加以下属性：

   **项目路径** 指定AEM Screens项目的路径。 路径通常为 `/content/screens/<Name of your project>`.

   *例如*， `/content/screens/we-retail`. 您可以通过选择AEM Screens下的任何项目（不要单击图标），在URL中找到此路径。

   >[!NOTE]
   >
   >指定相对于渠道的项目路径。

   **计划频率** 指定时间，例如，下午5:00或17:00，此服务应在该时间更新离线内容。

1. 单击 **保存** 以保存设置，您的内容将在指定的时间更新。
