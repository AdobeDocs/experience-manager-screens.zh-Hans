---
title: 零售库存目标激活
seo-title: 零售库存目标激活
description: 此“用例”展示三种不同颜色的运动衫的零售库存。 根据Google Sheets中记录的库存中可用的汗衫数量，屏幕上将显示数量最多的图像（红色、绿色或蓝色运动衫）。
seo-description: 此“用例”展示三种不同颜色的运动衫的零售库存。 根据Google Sheets中记录的库存中可用的汗衫数量，屏幕上将显示数量最多的图像（红色、绿色或蓝色运动衫）。
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 0%

---


# 零售库存目标激活{#retail-inventory-targeted-activation}

以下用例根据Google工作表中的值演示了三种不同的图像。

## 描述 {#description}

此“用例”展示三种不同颜色的运动衫的零售库存。 根据Google Sheets中记录的库存中可用的汗衫数量，屏幕上将显示数量最多的图像（红色、绿色或蓝色运动衫）。

对于此用例，红色、绿色或蓝色毛衣将根据可用毛衣数量的最高值显示在屏幕上。

## 先决条件{#preconditions}

在开始实施零售库存定位激活之前，您必须了解如何设置AEM Screens项目中的&#x200B;***受众商店***、***分段***&#x200B;和&#x200B;***为渠道***&#x200B;启用定位。

有关详细信息，请参阅AEM Screens](configuring-context-hub.md)中的[配置ContextHub。

## 基本流{#basic-flow}

请按照以下步骤实施Oracle Retail Inventory激活用例：

1. **填充Google工作表**

   1. 导航到ContextHubDemo Google工作表。
   1. 添加三列（红色、绿色和蓝色），并为三个不同的运动衫添加相应值。

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **根据要求配置受众**

   1. 导航到受众中的区段(请参阅&#x200B;***步骤2:在&#x200B;**[在AEM Screens](configuring-context-hub.md)**页面中配置ContextHub中设置受众分段***，了解更多详细信息)。

   1. 添加三个新区段&#x200B;**For_Red**、**For_Green**&#x200B;和&#x200B;**For_Blue**。

   1. 选择&#x200B;**For_Red**&#x200B;并单击操作栏中的&#x200B;**编辑**。

   1. 拖放&#x200B;**比较：属性 — 属性**&#x200B;指向编辑器，然后单击配置图标以编辑属性。
   1. 从&#x200B;**第一属性名称**&#x200B;的下拉菜单中选择&#x200B;**googlesheets/value/1/2**

   1. 从下拉菜单中选择&#x200B;**运算符**&#x200B;作为&#x200B;**greater-than**

   1. 选择&#x200B;**数据类型**&#x200B;作为&#x200B;**数字**

   1. 从&#x200B;**第二个属性名称**&#x200B;的下拉菜单中选择&#x200B;**googlesheets/value/1/1**。

   1. 拖放&#x200B;**另一个比较：属性 — 属性**&#x200B;指向编辑器，然后单击配置图标以编辑属性。
   1. 从&#x200B;**第一属性名称**&#x200B;的下拉菜单中选择&#x200B;**googlesheets/value/1/2**。

   1. 从下拉菜单中选择&#x200B;**运算符**&#x200B;作为&#x200B;**greater-than**

   1. 选择&#x200B;**数据类型**&#x200B;作为&#x200B;**number**

   1. 从&#x200B;**第二个属性名称**&#x200B;的下拉菜单中选择&#x200B;**googlesheets/value/1/0**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同样，编辑比较属性规则并将其添加到&#x200B;**For_Blue**&#x200B;区段，如下图所示：

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同样，编辑比较属性规则并将其添加到** For_Green **segment，如下图所示：

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >您会注意到，对于区段&#x200B;**For_Green**&#x200B;和&#x200B;**For_Green**，无法在编辑器中解析数据，因为目前只有第一个比较有效，与Google工作表中的值相同。

1. 导航并选择&#x200B;**DataDrivenRetail**&#x200B;渠道(序列渠道)，然后单击操作栏中的&#x200B;**编辑**。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >您应该已使用渠道&#x200B;**属性** —> **个性化**&#x200B;选项卡设置&#x200B;**ContextHub** **配置**。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   您必须同时选择&#x200B;**Brand**&#x200B;和&#x200B;**Area**，才能在开始定位过程时正确列出活动。

1. **添加默认图像**

   1. 向渠道添加默认图像，然后单击&#x200B;**定位**。
   1. 从下拉菜单中选择&#x200B;**品牌**&#x200B;和&#x200B;**活动**，然后单击&#x200B;**开始定位**。

   1. 单击&#x200B;**开始定位**。

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   在开始定位之前，您必须通过单击侧边栏中的&#x200B;**+添加体验定位**&#x200B;来添加区段（**For_Green**、**For_Red**&#x200B;和&#x200B;**For_Blue**），如下图所示。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 将图像添加到所有三个不同的屏幕，如下所示。

   ![retail_targeting](assets/retail_targeting.gif)

1. **检查预览**

   1. 单击&#x200B;**预览。** 此外，打开您的Google工作表并更新其值。
   1. 更改所有三个不同列的值，您会注意到显示图像会根据库存中的最高值进行更新。

   ![retail_result](assets/retail_result.gif)

