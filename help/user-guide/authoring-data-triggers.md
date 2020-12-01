---
title: 使用数据触发器进行创作
seo-title: 使用数据触发器进行创作
description: 可查看本页以了解如何使用数据触发器进行创作。
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 1%

---


# 使用数据触发器进行创作{#authoring-with-data-triggers}

本节重点介绍如何在渠道中启用定位。

>[!IMPORTANT]
>
>在AEM Screens渠道中支持数据触发器的最低版本为AEM 6.5.3 Feature Pack 3。

## 前提条件 {#prereqs}

在执行以下步骤以启用渠道定位之前，您必须了解在AEM Screens进行配置](configuring-context-hub.md)中的[关键术语，以了解在AEM Screens进行ContextHub和定位。

>[!IMPORTANT]
>
>建议您先了解并设置ContextHub配置，然后在AEM Screens渠道中启用定位。

请访问以下链接以了解更多信息：

1. **[设置数据存储](configuring-context-hub.md)**
1. **[设置受众分段](configuring-context-hub.md)**

完成上述步骤后，您便可以在渠道中启用定位。

## 使用数据触发器进行创作概述{#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## 在AEM Screens渠道{#enabling-targeting}中启用定位

按照以下步骤在您的渠道中启用定位。

1. 导航到某个AEM Screens渠道。 以下步骤演示了如何使用在AEM Screens渠道中创建的&#x200B;**DataDrivenRetail** *(序列渠道)*&#x200B;启用定位。

1. 选择渠道&#x200B;**DataDrivenRetail**&#x200B;并单击操作栏中的&#x200B;**属性**。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 选择&#x200B;**Personalization**&#x200B;选项卡以设置ContextHub配置，然后选择ContextHub和区段路径。

   1. 选择&#x200B;**ContextHub路径**&#x200B;作为&#x200B;**libs** > **设置** > **cloudsettings** > **default** > **ContextHub配置**&#x200B;并单击&#x200B;**选择**。

   1. 选择&#x200B;**区段路径**&#x200B;作为&#x200B;**conf** > **We.Retail** > **设置** **wcm****区段**，然后单击&#x200B;**选择**。

   1. 单击&#x200B;**保存并关闭**。
   >[!NOTE]
   >
   >使用ContextHub和“区段”路径，您最初在其中保存了Context Hub配置和区段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. 导航并选择&#x200B;**DataDrivenAssets** > **渠道**&#x200B;中的&#x200B;**DataDrivenRetail**，然后单击操作栏中的&#x200B;**编辑**。 在渠道编辑器中拖放资产。

   >[!NOTE]
   >
   >如果您正确设置了所有内容，您将在编辑器的下拉框中看到&#x200B;**定位**&#x200B;选项，如下图所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. 单击&#x200B;**定位**。

1. 从下拉菜单中选择&#x200B;**品牌**&#x200B;和&#x200B;**活动**，然后单击&#x200B;**开始定位**。

### 了解更多：示例用例{#learn-more-example-use-cases}

为AEM Screens项目配置ContextHub后，您可以按照不同的使用案例了解数据触发资产如何在不同行业中发挥关键作用：

1. **[零售库存目标激活](retail-inventory-activation.md)**
1. **[旅行中心温度激活](local-temperature-activation.md)**
1. **[酒店预订激活](hospitality-reservation-activation.md)**
