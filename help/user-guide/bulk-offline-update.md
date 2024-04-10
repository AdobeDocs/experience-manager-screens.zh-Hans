---
title: 批量脱机更新
description: 了解如何批量更新所有渠道。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d0a0b065-798e-4108-86ac-0a1f4e211cfc
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# 批量脱机更新 {#bulk-offline-update}

本节介绍有关批量脱机更新的以下主题：

* **概述**
* **使用批量脱机更新**

<!-- OBSOLETE VERSIONS
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, you must contact Adobe Support and request access. Once you have permissions you can download it from Package Share. -->

## 概述 {#overview}

批量脱机更新允许您批量更新所有渠道。 它可避免导航到特定渠道并更新内容的麻烦。 相反，您可以立即为一个特定项目更新渠道中的所有内容。

您也可以将此活动安排在网络流量较低的时间进行。

>[!NOTE]
>
>批量离线更新功能已得到优化，可仅更新那些已修改的渠道。

## 使用批量脱机更新 {#using-bulk-offline-update}

您可以从用户界面(UI)手动使用批量脱机更新，也可以计划从OSGi服务进行批量更新。

### 使用AEM Screens用户界面 {#using-aem-screens-user-interface}

请按照以下步骤对AEM Screens项目使用批量离线更新：

1. 导航到您的AEM Screens项目。
1. 选择项目，然后选择 **更新离线内容** 以手动更新渠道内容。

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience Manager Web控制台配置 {#adobe-experience-manager-web-console-configuration}

请按照以下步骤对AEM Screens项目使用批量离线更新：

1. Adobe Experience Manager Web控制台配置。
1. 搜索批量脱机更新服务。

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 添加以下属性：

   **项目路径** 指定AEM Screens项目的路径。 路径通常为 `/content/screens/<Name of your project>`.

   *例如*， `/content/screens/we-retail`. 您可以通过选择AEM Screens下的任何项目（不单击图标），在URL中找到此路径。

   >[!NOTE]
   >
   >指定相对于渠道的项目路径。

   **计划频率** 指定一个时间，例如5:00 P.M.或17:00，此服务应在此时间更新离线内容。

1. 选择 **保存** 以保存您的设置。 您的内容将在指定时间更新。
