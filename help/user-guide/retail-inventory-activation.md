---
title: 零售库存目标激活
seo-title: 零售库存目标激活
description: 此“用例”显示三种不同颜色的运动衫的零售库存。 根据Google Sheets中记录的库存中可用的血汗衫数量，屏幕上会显示数量最多的图像（红色、绿色或蓝色运动衫）。
seo-description: 此“用例”显示三种不同颜色的运动衫的零售库存。 根据Google Sheets中记录的库存中可用的血汗衫数量，屏幕上会显示数量最多的图像（红色、绿色或蓝色运动衫）。
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: 创作屏幕
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---


# 零售库存目标激活{#retail-inventory-targeted-activation}

以下用例演示了根据Google工作表中的值划分的三个不同图像。

## 描述 {#description}

此“用例”显示三种不同颜色的运动衫的零售库存。 根据Google Sheets中记录的库存中可用的血汗衫数量，屏幕上会显示数量最多的图像（红色、绿色或蓝色运动衫）。

对于此用例，在屏幕上将根据可用毛衫数量的最大值显示红色、绿色或蓝色毛衣。

## 先决条件 {#preconditions}

在开始实施零售库存定位激活之前，您必须了解如何在AEM Screens项目中设置&#x200B;***数据存储***、***受众分段***&#x200B;和&#x200B;***为渠道启用定位***。

有关详细信息，请参阅[在AEM Screens中配置ContextHub](configuring-context-hub.md) 。

## 基本流量{#basic-flow}

请按照以下步骤实施零售库存激活用例：

1. **填充Google工作表**

   1. 导航到ContextHubDemo Google工作表。
   1. 添加三列（红色、绿色和蓝色），并为三件不同的运动衫添加相应值。

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **根据要求配置受众**

   1. 导航到受众中的区段(请参阅&#x200B;***步骤2:在&#x200B;**[在AEM Screens中配置ContextHub](configuring-context-hub.md)**页面中设置受众分段***，以了解更多详细信息)。

   1. 添加三个新区段&#x200B;**For_Red**、**For_Green**&#x200B;和&#x200B;**For_Blue**。

   1. 选择&#x200B;**For_Red**，然后单击操作栏中的&#x200B;**编辑**。

   1. 拖放&#x200B;**比较：属性 — 编辑器的属性** ，然后单击配置图标以编辑属性。
   1. 从&#x200B;**First Property name**&#x200B;的下拉菜单中选择&#x200B;**googlesheets/value/1/2**

   1. 从下拉菜单中选择&#x200B;**运算符**&#x200B;作为&#x200B;**greater-than**

   1. 选择&#x200B;**数据类型**&#x200B;作为&#x200B;**数字**

   1. 从&#x200B;**Second属性名称**&#x200B;的下拉列表中选择&#x200B;**googlesheets/value/1/1**。

   1. 拖放&#x200B;**其他比较：属性 — 编辑器的属性** ，然后单击配置图标以编辑属性。
   1. 从&#x200B;**First Property name**&#x200B;的下拉菜单中选择&#x200B;**googlesheets/value/1/2**。

   1. 从下拉菜单中选择&#x200B;**运算符**&#x200B;作为&#x200B;**greater-than**

   1. 选择&#x200B;**数据类型**&#x200B;作为&#x200B;**number**

   1. 从&#x200B;**Second属性名称**&#x200B;的下拉列表中选择&#x200B;**googlesheets/value/1/0**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同样，编辑比较属性规则并将其添加到&#x200B;**For_Blue**&#x200B;区段，如下图所示：

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同样，编辑比较属性规则并将其添加到** For_Green**区段，如下图所示：

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >您会注意到，对于区段&#x200B;**For_Green**&#x200B;和&#x200B;**For_Green**，无法在编辑器中解析数据，因为只有第一个比较现在才有效，就像Google工作表中的值一样。

1. 导航并选择&#x200B;**DataDrivenRetail**&#x200B;渠道（序列渠道），然后单击操作栏中的&#x200B;**编辑**。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >您应该使用渠道&#x200B;**属性** —> **个性化**&#x200B;选项卡设置&#x200B;**ContextHub** **配置**。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   要在开始定位流程时正确列出活动，必须同时选择&#x200B;**Brand**&#x200B;和&#x200B;**Area**。

1. **添加默认图像**

   1. 向渠道中添加默认图像，然后单击&#x200B;**定位**。
   1. 从下拉菜单中选择&#x200B;**Brand**&#x200B;和&#x200B;**Activity**，然后单击&#x200B;**开始定位**。

   1. 单击&#x200B;**开始定位**。

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   在开始定位之前，必须通过单击侧边栏中的&#x200B;**+添加体验定位**，添加区段（**For_Green**、**For_Red**&#x200B;和&#x200B;**For_Blue**），如下图所示。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 将图像添加到所有三个不同的屏幕中，如下所示。

   ![retail_targeting](assets/retail_targeting.gif)

1. **检查预览**

   1. 单击&#x200B;**预览。** 此外，打开Google工作表并更新其值。
   1. 更改所有三个不同列的值，您会注意到显示图像会根据库存中的最高值进行更新。

   ![retail_result](assets/retail_result.gif)

