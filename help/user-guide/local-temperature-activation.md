---
title: 行程中心温度激活
description: 使用AEM Screens，了解此用例如何根据Google Sheets中填充的值演示如何使用旅游中心本地温度激活。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# 行程中心温度激活 {#travel-center-temperature-activation}

以下用例演示了如何根据Google Sheets中填充的值激活旅行中心本地温度。

## 描述 {#description}

对于此用例，如果Google Sheets中的值小于50，则会显示包含热饮的图像。 如果该值大于或等于50，则会显示包含冷饮料的图像。 如果存在其他值或根本没有值，播放器将显示默认图像。

## 前提条件 {#preconditions}

在开始实施旅游中心本地温度激活之前，了解如何在AEM Screens项目中设置&#x200B;***数据存储***、***受众分段***&#x200B;和&#x200B;***启用渠道定位***。

有关详细信息，请参阅[在AEM Screens中配置ContextHub](configuring-context-hub.md)。

## 基本流量 {#basic-flow}

按照以下步骤实施Travel Center Local Template Activation用例：

1. **填充Google工作表**

   1. 导航到ContextHubDemo Google工作表。
   1. 添加具有&#x200B;**`Heading1`**&#x200B;的列，该列具有对应的温度值。

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **根据要求配置受众中的区段**

   1. 导航到受众中的区段(有关更多详细信息，请参阅&#x200B;**[在AEM Screens中配置ContextHub](configuring-context-hub.md)**&#x200B;页面中的&#x200B;***步骤2：设置受众分段***)。

   1. 单击&#x200B;**工作表A1 1**，然后单击&#x200B;**编辑**。

   1. 单击比较属性，然后单击配置图标。
   1. 从&#x200B;**属性名称**&#x200B;中的下拉列表中单击&#x200B;**Googlesheets/value/1/0**

   1. 从下拉菜单中单击&#x200B;**运算符**&#x200B;作为&#x200B;**大于或等于**

   1. 输入&#x200B;**值**&#x200B;作为&#x200B;**50**

   1. 同样，选择&#x200B;**工作表A1 2**&#x200B;并单击&#x200B;**编辑**。

   1. 单击&#x200B;**比较属性 — 值**&#x200B;并选择配置图标。
   1. 从&#x200B;**属性名称**&#x200B;中的下拉列表中单击&#x200B;**Googlesheets/value/1/0**

   1. 从下拉菜单中单击&#x200B;**运算符**&#x200B;作为&#x200B;**小于**

   1. 输入&#x200B;**值**&#x200B;作为&#x200B;**50**

1. 导航并选择您的频道()，然后单击操作栏中的&#x200B;**编辑**。 在以下示例&#x200B;**DataDrivenWeather**&#x200B;中，顺序通道用于展示其功能。

   >[!NOTE]
   >
   >您的渠道应已具有默认图像，并且应按照[在AEM Screens中配置ContextHub](configuring-context-hub.md)中所述，预配置受众。

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >您应该已经设置了使用渠道&#x200B;**属性** > **Personalization**&#x200B;选项卡的&#x200B;**ContextHub** **配置**。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 在编辑器中单击&#x200B;**定位**，然后从下拉菜单中单击&#x200B;**品牌**&#x200B;和&#x200B;**活动**，然后单击&#x200B;**开始定位**。

   ![new_activity3](assets/new_activity3.gif)

1. **正在检查预览**

   1. 单击&#x200B;**预览。**&#x200B;此外，打开您的Google工作表并更新其值。
   1. 将该值更改为小于50。 您可以查看冷饮的图像。 如果Google Sheets中的值为50或更大，您应该会看到热饮的图像。

   ![结果3](assets/result3.gif)
