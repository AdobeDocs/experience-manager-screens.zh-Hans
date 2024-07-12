---
title: Hospitality Reservation Activation
description: 了解此用例如何演示如何根据Google Sheets中填充的值激活酒店预订。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Hospitality Reservation Activation {#hospitality-reservation-activation}

以下用例演示了如何根据Google工作表中填充的值激活医院预订。

## 描述 {#description}

对于此用例，Google工作表中填充了两个餐厅&#x200B;**`Restaurant1`**&#x200B;和&#x200B;**`Restaurant2`**&#x200B;上的预订百分比。 应用公式时基于`Restaurant1`和`Restaurant2`的值，并根据公式将值1或2分配给&#x200B;**AdTarget**&#x200B;列。

如果值为&#x200B;**`Restaurant1`** > **`Restaurant2`**，则&#x200B;**AdTaget**&#x200B;被赋值为&#x200B;**1**，否则&#x200B;**AdTarget**&#x200B;被赋值为&#x200B;**2**。 值1生成一个&#x200B;*牛排食品*&#x200B;选项，值2则在您的显示屏上显示&#x200B;*泰式食品*&#x200B;选项。

## 前提条件 {#preconditions}

在开始实施保留激活之前，了解如何在AEM Screens项目中设置&#x200B;***数据存储***、***受众分段***&#x200B;和&#x200B;***启用渠道定位***。

有关详细信息，请参阅[在AEM Screens中配置ContextHub](configuring-context-hub.md)。

## 基本流量 {#basic-flow}

请按照以下用例步骤为您的AEM Screens项目实施酒店预订激活：

1. **填充Google工作表并添加公式**。

   例如，将该公式应用于第三列&#x200B;**AdTarget**，如下图所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根据要求配置受众中的区段**

   1. 导航到受众中的区段(有关更多详细信息，请参阅&#x200B;**[在AEM Screens中配置ContextHub](configuring-context-hub.md)**&#x200B;页面中的&#x200B;***步骤2：设置受众分段***)。
   1. 单击&#x200B;**工作表A1 1**，然后单击&#x200B;**编辑**。
   1. 单击比较属性，然后单击&#x200B;**配置**&#x200B;图标。
   1. 从&#x200B;**属性名称**&#x200B;中的下拉列表中单击&#x200B;**googleHeets/value/1/2**。
   1. 从下拉菜单中单击&#x200B;**运算符**&#x200B;作为&#x200B;**等于**。
   1. 输入&#x200B;**值**&#x200B;作为&#x200B;**1**。
   1. 同样，单击&#x200B;**工作表A1 2**&#x200B;并单击&#x200B;**编辑**。
   1. 单击比较属性，然后单击&#x200B;**配置**&#x200B;图标。
   1. 从&#x200B;**属性名称**&#x200B;中的下拉列表中单击&#x200B;**googleHeets/value/1/2**。
   1. 单击&#x200B;**运算符**&#x200B;作为&#x200B;**2**。

1. 导航并单击您的频道()，然后单击操作栏中的&#x200B;**编辑**。 在下面的示例&#x200B;**DataDrivenRestaurant**&#x200B;中，顺序通道用于展示功能。

   >[!NOTE]
   >
   >您的渠道应已具有默认图像，并且应按照[在AEM Screens中配置ContextHub](configuring-context-hub.md)中所述，预配置受众。

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >此时应该已经设置了使用渠道&#x200B;**属性** > **Personalization**&#x200B;选项卡的&#x200B;**ContextHub** **配置**。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 在编辑器中单击&#x200B;**定位**，然后从下拉菜单中单击&#x200B;**品牌**&#x200B;和&#x200B;**活动**，然后单击&#x200B;**开始定位**。
1. **正在检查预览**

   1. 单击&#x200B;**预览。**&#x200B;此外，打开您的Google工作表并更新其值。
   1. 更新&#x200B;**`Restaurant1`**&#x200B;和&#x200B;**`Restaurant2`**&#x200B;列中的值。 如果&#x200B;**`Restaurant1`** > **`Restaurant2`，**，您应该能够查看&#x200B;*牛排*&#x200B;食物的图像，否则，屏幕上将显示&#x200B;*泰语*&#x200B;食物的图像。

   ![结果5](assets/result5.gif)
