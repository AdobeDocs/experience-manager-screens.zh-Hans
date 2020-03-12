---
title: 使用数据触发器进行创作
seo-title: 使用数据触发器进行创作
description: 可查看本页以了解如何使用数据触发器进行创作。
translation-type: tm+mt
source-git-commit: 24fda825220c6c2863fd76098a2f06209d9e0190

---


# 使用数据触发器进行创作 {#authoring-with-data-triggers}

本节重点介绍如何在渠道中启用定位。

>>[!I重要]信息：支持AEM Screens渠道中的数据触发器的最低版本为AEM 6.4.3功能包3。
>

## 前提条件 {#prereqs}

在按照以下步骤在渠道中启用定位之前，您必须先阅读在AEM Screens中配置中的关键术语 [](configuring-context-hub.md) ，了解AEM Screens中的ContextHub和定位。

>[!I重要]
> 建议您先了解并设置ContextHub配置，然后再在AEM Screens渠道中启用定位。

请访问以下链接以了解更多信息：

1. **[设置数据存储](configuring-context-hub.md)**
1. **[设置受众细分](configuring-context-hub.md)**

完成上述步骤后，您便可以在渠道中启用定位。

## 使用数据触发器进行创作概述 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## 在AEM Screens渠道中启用定位 {#enabling-targeting}

按照以下步骤在您的渠道中启用定位。

1. 导航到其中一个AEM Screens渠道。 以下步骤演示了如何使用在AEM Screens渠道中创 **建的DataDrivenRetail***（序列渠道）* ，启用定位。

1. 选择渠道 **DataDrivenRetail** ，然后 **单击操作栏中的** “属性”。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 选择“个 **性化** ”选项卡以设置ContextHub配置。

   1. 选择“ **Hub Path** ”作 **为** Libs **>** > Settings > DefaultHub **>DefaultHob Context Configurations(Libs**************> Settings > DefaultHub Context And Click SelectCloveCt”。

   1. 选择“路径 **”** >“会议” **>“零售”****>“零售”** >“Wcm **”**************>“Adobe ClickSelectSelectDign”的段。

   1. 单击 **保存并关闭**。
   >[!NOTE]
   使用ContextHub和“区段”路径，您最初在该路径中保存了Context Hub配置和区段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. 导航并从DataDrivenAssets > **Channels中选择** DataDriven Retail **，然后单击** ActionBar中 ******** 的EditRetail。

   >[!NOTE]
   如果您正确设置了所有内容，您将在编辑器的下拉框中看到 **Targeting** （定位）选项，如下图所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   为渠道配置ContextHub配置后，如果您希望遵循以下所有使用案例，请确保对其他三个序列渠道也遵循前面的步骤（从1到4）。

### 了解更多：示例用例 {#learn-more-example-use-cases}

在为AEM Screens项目配置ContextHub后，您可以按照不同的使用案例了解数据触发资产如何在不同行业中扮演关键角色：

1. **[零售库存定向激活](retail-inventory-activation.md)**
1. **[旅行中心温度激活](local-temperature-activation.md)**
1. **[酒店预订激活](hospitality-reservation-activation.md)**

