---
title: 使用Data Triggers创作
description: 详细了解如何在AEM Screens渠道中使用数据触发器进行创作。
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 1%

---

# 使用Data Triggers创作 {#authoring-with-data-triggers}

本节重点介绍如何在渠道中启用定位。

>[!IMPORTANT]
>
>在AEM Screens渠道中支持数据触发器的最低版本是AEM 6.5.3 Feature Pack 3。

## 先决条件 {#prereqs}

在执行以下步骤以在渠道中启用定位之前，请了解AEM Screens中的配置所需的[关键术语](configuring-context-hub.md)，以了解AEM Screens中的ContextHub和定位。

>[!IMPORTANT]
>
>建议您先了解并设置ContextHub配置，然后再在AEM Screens渠道中启用定位。

有关详细信息，请访问下面的链接：

1. **[设置数据存储](configuring-context-hub.md)**
1. **[设置受众分段](configuring-context-hub.md)**

完成上述步骤后，便可在渠道中启用定位。

## 使用Data Triggers创作概述 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## 在AEM Screens渠道中启用定位 {#enabling-targeting}

执行以下步骤以在渠道中启用定位。

1. 导航到某个AEM Screens渠道。 以下步骤演示了如何使用在AEM Screens渠道中创建的&#x200B;**DataDrivenRetail** *（序列渠道）*&#x200B;启用定位。

1. 单击渠道&#x200B;**DataDrivenRetail**，然后单击操作栏中的&#x200B;**属性**。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 单击&#x200B;**Personalization**&#x200B;选项卡，以便您可以设置ContextHub配置，然后单击ContextHub和区段路径。

   1. 单击&#x200B;**ContextHub路径**&#x200B;作为&#x200B;**libs** > **设置** > **cloudsettings** > **默认值** > **ContextHub配置**，然后单击&#x200B;**单击**。

   1. 单击&#x200B;**区段路径**&#x200B;作为&#x200B;**conf** > **`We.Retail`** > **设置** > **wcm** > **区段**，然后单击&#x200B;**单击**。

   1. 单击“**保存并关闭**”。

   >[!NOTE]
   >
   >使用ContextHub和区段路径，您最初是在其中保存了Context Hub配置和区段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. 导航并单击&#x200B;**DataDrivenAssets** > **渠道**&#x200B;中的&#x200B;**DataDrivenRetail**，然后单击操作栏中的&#x200B;**编辑**。 将资产拖放到渠道编辑器中。

   >[!NOTE]
   >
   >如果一切设置正确，您会在编辑器的下拉列表中看到&#x200B;**定位**&#x200B;选项，如下图所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. 单击&#x200B;**定位**。

1. 从下拉菜单中单击&#x200B;**品牌**&#x200B;和&#x200B;**活动**，然后单击&#x200B;**开始定位**。

### 了解详情：示例用例 {#learn-more-example-use-cases}

为AEM Screens项目配置ContextHub后，您可以按照不同的用例来了解数据触发的资源如何在不同的行业中发挥重要作用：

1. **[零售库存目标激活](retail-inventory-activation.md)**
1. **[旅行中心温度激活](local-temperature-activation.md)**
1. **[酒店预订激活](hospitality-reservation-activation.md)**
