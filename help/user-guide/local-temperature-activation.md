---
title: 行程中心温度激活
seo-title: Travel Center Temperature Activation
description: 以下用例演示了如何根据Google Sheets中填充的值激活旅行中心本地温度。
seo-description: The following use case demonstrates the usage of travel center local temperature activation based on the values populated in Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# 行程中心温度激活 {#travel-center-temperature-activation}

以下用例演示了如何根据Google Sheets中填充的值激活旅行中心本地温度。

## 描述 {#description}

对于此用例，如果Google工作表的值小于50，将显示热饮图像，如果该值大于或等于50，将显示冷饮图像。 如果存在其他值或没有值，播放器将显示默认图像。

## 前提条件 {#preconditions}

在开始实施旅行中心本地温度激活之前，您必须了解如何设置 ***数据存储***， ***受众分段*** 和 ***为渠道启用定位*** 在AEM Screens项目中。

请参阅 [在AEM Screens中配置ContextHub](configuring-context-hub.md) 以了解详细信息。

## 基本流量 {#basic-flow}

按照以下步骤实施Travel Center Local Template Activation用例：

1. **填充Google工作表**

   1. 导航到ContextHubDemo Google工作表。
   1. 添加列 **标题1** 具有相应温度的值。

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **根据要求在受众中配置区段**

   1. 导航到受众中的区段(请参阅 ***步骤2：设置受众分段*** 在 **[在AEM Screens中配置ContextHub](configuring-context-hub.md)** 页面（了解更多详细信息）。

   1. 选择 **工作表A1 1** 并单击 **编辑**.

   1. 选择比较属性，然后单击配置图标以编辑属性。
   1. 选择 **google表/value/1/0** 从的下拉菜单中 **属性名称**

   1. 选择 **运算符** 作为 **大于或等于** 从下拉菜单中

   1. 输入 **值** 作为 **50**

   1. 同样，选择 **工作表A1 2** 并单击 **编辑**.

   1. 选择 **比较属性 — 值** ，然后单击配置图标以编辑属性。
   1. 选择 **google表/value/1/0** 从的下拉菜单中 **属性名称**

   1. 选择 **运算符** 作为 **小于** 从下拉菜单中

   1. 输入 **值** 作为 **50**

1. 导航并选择您的渠道()并单击 **编辑** 从操作栏中。 在以下示例中， **DataDrivenWeather**，顺序渠道用于展示功能。

   >[!NOTE]
   >
   >您的渠道应已具有默认图像，并且受众应已预配置，如中所述 [在AEM Screens中配置ContextHub](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >您应该设置您的 **ContextHub** **配置** 使用渠道 **属性** > **个性化** 选项卡。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 选择 **定位** 从编辑器中选择 **品牌** 和 **活动** 从下拉菜单中单击 **开始定位**.

   ![new_activity3](assets/new_activity3.gif)

1. **检查预览**

   1. 单击 **预览。** 此外，打开您的Google工作表并更新其值。
   1. 将该值更改为小于50，您应该能够查看夏季饮料的图像。 如果Google工作表中的值大于或等于，则应该能够查看热饮的图像。

   ![result3](assets/result3.gif)
