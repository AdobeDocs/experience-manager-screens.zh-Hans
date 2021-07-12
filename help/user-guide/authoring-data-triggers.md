---
title: 使用数据触发器进行创作
seo-title: 使用数据触发器进行创作
description: 请阅读本页以了解如何使用数据触发器进行创作。
feature: 创作屏幕
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 1%

---

# 使用数据触发器进行创作 {#authoring-with-data-triggers}

本节重点介绍如何在渠道中启用定位。

>[!IMPORTANT]
>
>在AEM Screens渠道中，支持数据触发器的最低版本为AEM 6.5.3 Feature Pack 3。

## 前提条件 {#prereqs}

在按照以下步骤在渠道中启用定位之前，您必须了解在AEM Screens中配置](configuring-context-hub.md)中的[关键术语，这是了解AEM Screens中的ContextHub和定位所需的。

>[!IMPORTANT]
>
>在AEM Screens渠道中启用定位之前，建议您了解并设置ContextHub配置。

有关更多信息，请访问以下链接：

1. **[设置数据存储](configuring-context-hub.md)**
1. **[设置受众分段](configuring-context-hub.md)**

完成上述步骤后，即可在渠道中启用定位。

## 使用数据触发器创作概述 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## 在AEM Screens渠道中启用定位 {#enabling-targeting}

按照以下步骤在渠道中启用定位。

1. 导航到其中一个AEM Screens渠道。 以下步骤演示了如何使用在AEM Screens渠道中创建的&#x200B;**DataDrivenRetail** *(sequence channel)*&#x200B;启用定位。

1. 选择渠道&#x200B;**DataDrivenRetail**，然后单击操作栏中的&#x200B;**属性**。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 选择&#x200B;**Personalization**&#x200B;选项卡以设置ContextHub配置并选择ContextHub和区段路径。

   1. 选择&#x200B;**ContextHub路径**&#x200B;作为&#x200B;**libs** > **设置** > **cloudsettings** > **默认** > **ContextHub配置**&#x200B;并单击&#x200B;**选择**。

   1. 选择&#x200B;**区段路径**&#x200B;作为&#x200B;**conf** > **We.Retail** > **设置** > **wcm** > **区段**，然后单击&#x200B;**选择**。

   1. 单击&#x200B;**保存并关闭**。
   >[!NOTE]
   >
   >使用ContextHub和区段路径，您最初在其中保存了ContextHub配置和区段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. 从&#x200B;**DataDrivenAssets** > **渠道**&#x200B;中导航并选择&#x200B;**DataDrivenRetail**，然后单击操作栏中的&#x200B;**编辑**。 在渠道编辑器中拖放资产。

   >[!NOTE]
   >
   >如果已正确设置所有内容，您将在编辑器的下拉菜单中看到&#x200B;**定位**&#x200B;选项，如下图所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. 单击&#x200B;**定位**。

1. 从下拉菜单中选择&#x200B;**Brand**&#x200B;和&#x200B;**Activity**，然后单击&#x200B;**开始定位**。

### 了解更多：用例示例 {#learn-more-example-use-cases}

为AEM Screens项目配置ContextHub后，您可以按照不同的用例了解数据触发资产如何在不同行业中发挥关键作用：

1. **[零售库存目标激活](retail-inventory-activation.md)**
1. **[旅行中心温度激活](local-temperature-activation.md)**
1. **[酒店预订激活](hospitality-reservation-activation.md)**
