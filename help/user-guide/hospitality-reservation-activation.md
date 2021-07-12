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
feature: 创作屏幕
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# 酒店预订激活 {#hospitality-reservation-activation}

以下用例演示了如何根据Google工作表中填充的值激活医院预订。

## 描述 {#description}

对于此用例，Google Sheet中填充了两家餐馆&#x200B;**Restaurant1**&#x200B;和&#x200B;**Restaurant2**&#x200B;的预订百分比。 根据Restaurant1和Restaurant2的值应用公式，并根据公式将值1或2分配给&#x200B;**AdTarget**&#x200B;列。

如果&#x200B;**Restaurant1** > **Restaurant2**&#x200B;的值，则为&#x200B;**AdTaget**&#x200B;分配值&#x200B;**1**，否则为&#x200B;**AdTarget**&#x200B;分配值&#x200B;**2**。 值1生成&#x200B;*牛排食品*&#x200B;选项，值2会在显示屏上显示&#x200B;*泰式食品*&#x200B;选项。

## 先决条件 {#preconditions}

在开始实施预订激活之前，您必须了解如何在AEM Screens项目中设置&#x200B;***数据存储***、***受众分段***&#x200B;和&#x200B;***启用渠道定位***。

有关详细信息，请参阅[在AEM Screens中配置ContextHub](configuring-context-hub.md) 。

## 基本流量 {#basic-flow}

请按照以下步骤为您的AEM Screens项目实施酒店预订激活用例：

1. **填充Google工作表并添加公式。**

   例如，将公式应用到第三列&#x200B;**AdTarget**，如下图所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根据要求在受众中配置区段**

   1. 导航到受众中的区段(请参阅&#x200B;***步骤2:在&#x200B;**[在AEM Screens中配置ContextHub](configuring-context-hub.md)**页面中设置受众分段***，以了解更多详细信息)。

   1. 选择&#x200B;**工作表A1 1**&#x200B;并单击&#x200B;**编辑**。

   1. 选择比较属性，然后单击配置图标以编辑属性。
   1. 从&#x200B;**属性名称**&#x200B;的下拉菜单中选择&#x200B;**googlesheets/value/1/2**

   1. 从下拉菜单中选择&#x200B;**运算符**&#x200B;作为&#x200B;**equal**

   1. 输入&#x200B;**Value**&#x200B;作为&#x200B;**1**

   1. 同样，选择&#x200B;**工作表A1 2**&#x200B;并单击&#x200B;**编辑**。

   1. 选择比较属性，然后单击配置图标以编辑属性。
   1. 从&#x200B;**属性名称**&#x200B;的下拉菜单中选择&#x200B;**googlesheets/value/1/2**

   1. 选择&#x200B;**运算符**&#x200B;作为&#x200B;**2**

1. 导航并选择渠道()，然后单击操作栏中的&#x200B;**编辑**。 在以下示例中， **DataDrivenRestaurant**&#x200B;使用顺序渠道来展示该功能。

   >[!NOTE]
   >
   >您的渠道应已具有默认图像，且应按照[在AEM Screens中配置ContextHub](configuring-context-hub.md)中所述预配置受众。

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >您应该使用渠道&#x200B;**属性** —> **个性化**&#x200B;选项卡设置&#x200B;**ContextHub** **配置**。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 从编辑器中选择&#x200B;**定位**，然后从下拉菜单中选择&#x200B;**品牌**&#x200B;和&#x200B;**活动**，然后单击&#x200B;**开始定位**。
1. **检查预览**

   1. 单击&#x200B;**预览。** 此外，打开Google工作表并更新其值。
   1. 更新&#x200B;**Restaurant1**&#x200B;和&#x200B;**Restaurant2**&#x200B;列中的值。 如果&#x200B;**Restaurant1** > **Restaurant2,**&#x200B;您应该能够查看&#x200B;*牛排*&#x200B;食品的图像，否则，屏幕上会显示&#x200B;*Thai*&#x200B;食品图像。
   ![结果5](assets/result5.gif)
