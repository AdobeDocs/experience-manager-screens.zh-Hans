---
title: 旅行中心温度激活
seo-title: 旅行中心温度激活
description: 以下用例演示了如何使用基于Google Sheets中填充的值的旅游中心本地温度激活。
seo-description: 以下用例演示了如何使用基于Google Sheets中填充的值的旅游中心本地温度激活。
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 旅行中心温度激活 {#travel-center-temperature-activation}

以下用例演示了如何使用基于Google Sheets中填充的值的旅游中心本地温度激活。

## 描述 {#description}

对于此“用例”，如果您的Google Sheets的“值”小于50，则将显示含有热饮的图像，如果该值大于或等于50，则将显示含有冷饮的图像。 如果存在其他值或没有值，播放器将显示默认图像。

## 先决条件 {#preconditions}

在开始实施旅游中心本地温度激活之前，您必须了解如何在AEM Screens项目中设置 ***Data Store***、 ***Audience Segmentation********* 和Enable Targeting for Channels。

有关详细 [信息，请参阅在AEM Screens中配置ContextHub](configuring-context-hub.md) 。

## 基本流程 {#basic-flow}

请按照以下步骤实施“Travel Center Local Tempure Activation”（差旅中心本地温度激活）用例：

1. **填充Google工作表**

   1. 导航到ContextHubDemo google工作表。
   1. 添加一个带有 **Heading1的列** ，其中具有相应的温度值。
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **根据要求在受众中配置区段**

   1. 导航到受众中的区段(请参 ***阅步骤2:有关更多详细信息*** ，请 **[在“AEM Screens”页面中配置ContextHub](configuring-context-hub.md)** ，设置受众细分。)

   1. 选择“ **工作表A1 1** ”，然后单 **击编辑**。

   1. 选择比较属性，然后单击配置图标以编辑属性。
   1. 从 **属性名称的下拉菜单中选择“Googlesheets/value/1/0** ”( **Property name)**

   1. 从下 **拉菜单中** ，将运算符选为**greater-than-or-equal **

   1. 输入 **值** 50 **。**

   1. 同样，选择**工作表A1 2 **并单击“编 **辑”**。

   1. 选择比 **较属性——值** ，然后单击配置图标以编辑属性。
   1. 从 **属性名称的下拉菜单中选择“Googlesheets/value/1/0** ”( **Property name)**

   1. 从下 **拉菜单中选择运算符** **less-than **

   1. 输入 **值** 50 **。**

1. 导航并选择渠道()，然后单击操 **作栏** 中的编辑。 在以下示例中， **DataDrivenWeather**，使用顺序通道来展示该功能。

   >[!NOTE]
   >
   >您的渠道应已具有默认图像，并且应按照AEM Screens中的配置ContextHub中的 [说明预配置受众](configuring-context-hub.md)。

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >您应该已使用“ **Properties** Properties **—********** Personalization Chub”选项卡设置ContextHub配置。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 从编 **辑器中选择** “定位”，从 **Brand** （品牌）和 **Activity** （活动）下拉菜单中选择，然后单击“开始定 ****&#x200B;位”。

   ![new_activity3](assets/new_activity3.gif)

1. **检查预览**

   1. 单击“ **预览”。** 此外，打开Google工作表并更新其值。
   1. 将值更改为小于50，您应该能够查看夏季饮料的图像。 如果Google Sheet中的值大于或等于50，则应该能够查看热饮图像。
   ![result3](assets/result3.gif)

