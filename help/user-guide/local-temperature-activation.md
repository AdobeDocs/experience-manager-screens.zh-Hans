---
title: 旅行中心温度激活
seo-title: 旅行中心温度激活
description: 以下用例演示了如何使用基于Google工作表中填充的值的旅行中心本地温度激活。
seo-description: 以下用例演示了如何使用基于Google工作表中填充的值的旅行中心本地温度激活。
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---


# 旅行中心温度激活 {#travel-center-temperature-activation}

以下用例演示了如何使用基于Google工作表中填充的值的旅行中心本地温度激活。

## 描述 {#description}

对于此用例，如果您的Google Sheets的值小于50，则将显示含有热饮的图像，如果该值大于或等于50，则将显示含有冷饮的图像。 如果存在其他值或没有值，播放器将显示默认图像。

## 先决条件 {#preconditions}

在开始实施旅游中心本地温度激活之前，您必须了解如何在AEM Screens ***项目中设置******数据存储、******受众细分和*** 为渠道启用定位。

有关详细 [信息，请参阅在AEM Screens](configuring-context-hub.md) 配置ContextHub。

## 基本流 {#basic-flow}

请按照以下步骤实施Travel Center Local Tempure激活用例：

1. **填充Google工作表**

   1. 导航到ContextHubDemo Google工作表。
   1. 添加一个带有标 **题1的列** ，其温度值对应。

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **根据要求在受众中配置区段**

   1. 导航到受众中的区段(请参 ***阅步骤2:在“在AEM Screens配置*** ContextHub **[”页](configuring-context-hub.md)** 面中设置受众分段，以了解更多详细信息)。

   1. 选择“ **工作表A1 1** ”并单 **击编辑**。

   1. 选择比较属性并单击配置图标以编辑属性。
   1. 从 **属性名称的下拉菜单中选择** “googlesheets/value/1/ **0”**

   1. 从下 **拉** 菜单中选 **择“运算符大于** ”或“相等”

   1. 输入 **值** 50 **。**

   1. 同样，选择“ **工作表A1 2** ”并单 **击“Edit**”。

   1. 选择“ **比较属性——值** ”，然后单击配置图标以编辑属性。
   1. 从 **属性名称的下拉菜单中选择** “googlesheets/value/1/ **0”**

   1. 从下 **拉菜** 单中选 **择运算符** “小于”

   1. 输入 **值** 50 **。**

1. 导航并选择渠道()，然后单 **击操** 作栏中的编辑。 在以下示例 **中**,DataDrivenWeather使用顺序渠道来展示该功能。

   >[!NOTE]
   >
   >您的渠道应已具有默认图像，并且应按照配置AEM ScreensContextHub中 [的说明预配置受众](configuring-context-hub.md)。

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >您应该已使用“渠道属 **性—****>个性化”选** 项卡设 **置ContextHub****** 配置。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 从 **活动编辑** 器中选择定位 **，选择品** 牌 **，从下拉菜单中** 选择 **，然后单击开始定**&#x200B;位。

   ![new_活动3](assets/new_activity3.gif)

1. **检查预览**

   1. 单击 **预览。** 此外，打开Google工作表并更新其值。
   1. 将值更改为不到50，您应该能够视图夏季饮料的图像。 如果Google Sheet中的值大于或等于50，则应该能够视图热饮图像。

   ![result3](assets/result3.gif)

