---
title: 酒店预订激活
seo-title: 酒店预订激活
description: 以下用例演示了如何根据Google工作表中填充的值激活医院预订。
seo-description: 以下用例演示了如何根据Google工作表中填充的值激活医院预订。
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# 酒店预订激活 {#hospitality-reservation-activation}

以下用例演示了如何根据Google工作表中填充的值激活医院预订。

## 描述 {#description}

对于此用例，Google Sheet填充了两家餐馆 **Restaurant1和****Restaurant2的预订百分比**。 根据Restaurant1和Restaurant2的值应用公式，并根据公式将值1或2分配给 **AdTarget** 列。

如果值为 **Restaurant1** **Restaurant2**&gt; ，则 **AdTaget** 将赋值 **AdTaget********** 11，否则为AdTagetTarget分配的值为AdTargetIs赋值2AdTarget。 Value 1生成 *牛排美食* ,Value 2在显示屏上 *显示泰式美食* 。

## 先决条件 {#preconditions}

在开始实施预订激活之前，您必须了解如何在AEM Screens项目中设置 ***Data Store***、 ***Audience Segmentation******和Enable Targeting for Channels*** 。

有关详细 [信息，请参阅在AEM Screens中配置ContextHub](configuring-context-hub.md) 。

## 基本流程 {#basic-flow}

请按照以下步骤为AEM Screens项目实施酒店预订激活用例：

1. **填充Google工作表并添加公式。**

   例如，将公式应用到第三列 **AdTarget**，如下图所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根据要求在受众中配置区段**

   1. 导航到受众中的区段(请参 ***阅步骤2:有关更多详细信息*** ，请 **[在“AEM Screens”页面中配置ContextHub](configuring-context-hub.md)** ，设置受众细分。)

   1. 选择“ **工作表A1 1** ”，然后单 **击编辑**。

   1. 选择比较属性，然后单击配置图标以编辑属性。
   1. 从 **属性名称的下拉菜单中选择Googlesheets/value/1/2****。**

   1. 从下拉 **菜单中选** 择“Operator **as** equal”（运算符为等）

   1. 输入 **值** 1 **。**

   1. 同样，选择“ **工作表A1 2** ”并单 **击编辑**。

   1. 选择比较属性，然后单击配置图标以编辑属性。
   1. 从 **属性名称的下拉菜单中选择Googlesheets/value/1/2****。**

   1. 选择运 **算符** ( **2)**

1. 导航并选择渠道()，然后单击操 **作栏** 中的编辑。 在以下示例中， **DataDrivenRestaurant**，使用顺序渠道来展示该功能。

   >[!NOTE]
   >
   >您的渠道应已具有默认图像，并且应按照AEM Screens中的配置ContextHub中的 [说明预配置受众](configuring-context-hub.md)。

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >您应该已使用“ **Properties** Properties **—********** Personalization Chub”选项卡设置ContextHub配置。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 从编 **辑器中选择** “定位”，从 **Brand** （品牌）和 **Activity** （活动）下拉菜单中选择，然后单击“开始定 ****&#x200B;位”。
1. **检查预览**

   1. 单击“ **预览”。** 此外，打开Google工作表并更新其值。
   1. 更新 **Restaurant1和****Restaurant2列中的值** 。 如果 **Restaurant1** &gt; **Restaurant2,** 则您应该能够查看牛排食品的图像，否则， *Thai*** Food食品的图像会显示在您的屏幕上。
   ![result5](assets/result5.gif)

