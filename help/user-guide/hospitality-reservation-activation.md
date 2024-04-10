---
title: Hospitality Reservation Activation
seo-title: Hospitality Reservation Activation
description: 以下用例演示了如何根据Google工作表中填充的值激活医院预订。
seo-description: The following use case demonstrates the usage of hospital reservation activation based on the values populated in Google Sheets.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Hospitality Reservation Activation {#hospitality-reservation-activation}

以下用例演示了如何根据Google工作表中填充的值激活医院预订。

## 描述 {#description}

对于此用例，Google工作表中填入了两个餐厅的预订百分比 **Restaurant1** 和 **Restaurant2**. 根据Restaurant1和Restaurant2的值应用一个公式，并根据该公式，将值1或2指定给 **Adtarget** 列。

如果值 **Restaurant1** > **Restaurant2**，则 **AdTarget** 已分配值 **1** 否则 **Adtarget** 已分配值 **2**. 值1生成 *牛排食品* 选项和值2导致显示 *泰国菜* 选项。

## 前提条件 {#preconditions}

在开始实施预订激活之前，您必须了解如何设置 ***数据存储***， ***受众分段*** 和 ***为渠道启用定位*** 在AEM Screens项目中。

请参阅 [在AEM Screens中配置ContextHub](configuring-context-hub.md) 以了解详细信息。

## 基本流量 {#basic-flow}

请按照以下步骤为您的AEM Screens项目实施服务预订激活用例：

1. **填充Google工作表并添加公式。**

   例如，将公式应用于第三列 **Adtarget**，如下图所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根据要求在受众中配置区段**

   1. 导航到受众中的区段(请参阅 ***步骤2：设置受众分段*** 在 **[在AEM Screens中配置ContextHub](configuring-context-hub.md)** 页面（了解更多详细信息）。

   1. 选择 **工作表A1 1** 并单击 **编辑**.

   1. 选择比较属性，然后单击配置图标以编辑属性。
   1. 选择 **google表/value/1/2** 从的下拉菜单中 **属性名称**

   1. 选择 **运算符** 作为 **等于** 从下拉菜单中

   1. 输入 **值** 作为 **1**

   1. 同样，选择 **工作表A1 2** 并单击 **编辑**.

   1. 选择比较属性，然后单击配置图标以编辑属性。
   1. 选择 **google表/value/1/2** 从的下拉菜单中 **属性名称**

   1. 选择 **运算符** 作为 **2**

1. 导航并选择您的渠道()并单击 **编辑** 从操作栏中。 在以下示例中， **DataDrivenRestaurant**，顺序渠道用于展示功能。

   >[!NOTE]
   >
   >您的渠道应已具有默认图像，并且受众应已预配置，如中所述 [在AEM Screens中配置ContextHub](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >您应该设置您的 **ContextHub** **配置** 使用渠道 **属性** > **个性化** 选项卡。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 选择 **定位** 从编辑器中选择 **品牌** 和 **活动** 从下拉菜单中单击 **开始定位**.
1. **检查预览**

   1. 单击 **预览。** 此外，打开您的Google工作表并更新其值。
   1. 更新中的值 **Restaurant1** 和 **Restaurant2** 列。 如果 **Restaurant1** > **餐厅2** 您应该能够查看以下项目的图像 *牛排* 食物， *泰语* 食品图像显示在屏幕上。

   ![结果5](assets/result5.gif)
