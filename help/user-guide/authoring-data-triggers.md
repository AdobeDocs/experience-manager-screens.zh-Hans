---
title: 使用数据触发器进行创作
seo-title: 使用数据触发器进行创作
description: 可查看本页以了解如何使用数据触发器进行创作。
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---


# 使用数据触发器进行创作 {#authoring-with-data-triggers}

本节重点介绍如何在渠道中启用定位。

>[!IMPORTANT]
>
>在AEM Screens渠道中支持数据触发器的最低版本为AEM 6.5.3 Feature Pack 3。

## 前提条件 {#prereqs}

在执行以下步骤以启用渠道定位之前，您必须了解在 [中配置AEM Screens中的关键术语](configuring-context-hub.md) ，以便在AEM Screens中了解ContextHub和定位。

>[!IMPORTANT]
>
>建议您先了解并设置ContextHub配置，然后在AEM Screens渠道中启用定位。

请访问以下链接以了解更多信息：

1. **[设置数据存储](configuring-context-hub.md)**
1. **[设置受众分段](configuring-context-hub.md)**

完成上述步骤后，您便可以在渠道中启用定位。

## 使用数据触发器进行创作概述 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## 在AEM Screens渠道中启用定位 {#enabling-targeting}

按照以下步骤在您的渠道中启用定位。

1. 导航到某个AEM Screens渠道。 以下步骤演示如何通过使用在渠道 **渠道中创建** 的DataDrivenRetail ** (序列AEM Screens)，启用定位。

1. 选择渠道 **DataDriven** Retail，然 **后单击操** 作栏中的属性。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 选择“个 **性化** ”选项卡以设置ContextHub配置，然后选择ContextHub和“区段”路径。

   1. 选择ContextHub路 **径** , **作为****>设置** > **设置** >默认设置 ************>默认>中集配置和上下文和单击选择列。

   1. 选择“路径” **段** “会 **议”** >“零 **售”** >“” **>“”**************>“”>区段和点按。

   1. Click **Save &amp; Close**.
   >[!NOTE]
   >
   >使用ContextHub和“区段”路径，您最初在其中保存了Context Hub配置和区段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. 从“数据驱动资 **产”** >“渠道” **中导航并选** 择数据驱动 **的零售，然** 后单击操 **作栏中的“编** 辑”。 在渠道编辑器中拖放资产。

   >[!NOTE]
   >
   >如果您正确设置了所有内容，您将在 **编辑器** 的下拉框中看到“定位”选项，如下图所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. 单击 **定位**。

1. 从 **下拉** 菜 **单中选** 择品牌 **和活动**，然后单击开始定位。

### 了解更多： 示例使用案例 {#learn-more-example-use-cases}

为AEM Screens项目配置ContextHub后，您可以按照不同的使用案例了解数据触发资产在不同行业中如何发挥重要作用：

1. **[零售库存目标激活](retail-inventory-activation.md)**
1. **[旅行中心温度激活](local-temperature-activation.md)**
1. **[酒店预订激活](hospitality-reservation-activation.md)**

