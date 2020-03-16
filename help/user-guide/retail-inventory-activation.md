---
title: 零售库存定向激活
seo-title: 零售库存定向激活
description: 此“用例”显示三种不同颜色的血汗衫的零售库存。 根据Google Sheets中记录的库存中可用的运动衫数量，屏幕上将显示编号最高的图像（红色、绿色或蓝色运动衫）。
seo-description: 此“用例”显示三种不同颜色的血汗衫的零售库存。 根据Google Sheets中记录的库存中可用的运动衫数量，屏幕上将显示编号最高的图像（红色、绿色或蓝色运动衫）。
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
translation-type: tm+mt
source-git-commit: a7d3ec582dde83ed6efb08a6c3c6a75cc0820970

---


# 零售库存定向激活 {#retail-inventory-targeted-activation}

以下用例根据Google工作表中的值演示了三个不同的图像。

## 描述 {#description}

此“用例”显示三种不同颜色的血汗衫的零售库存。 根据Google Sheets中记录的库存中可用的运动衫数量，屏幕上将显示编号最高的图像（红色、绿色或蓝色运动衫）。

对于此用例，红色、绿色或蓝色毛衣将根据可用毛衣数量的最高值显示在屏幕上。

## 先决条件 {#preconditions}

在开始实施零售库存定位激活之前，您必须了解如何在AEM Screens项目中设置 ***Data Store***、 ***Audience Segmentation*** and ****** Enable Targeting for Channels。

有关详细 [信息，请参阅在AEM Screens中配置ContextHub](configuring-context-hub.md) 。

## 基本流程 {#basic-flow}

请按照以下步骤实施“零售库存激活”用例：

1. **填充Google工作表**

   1. 导航到ContextHubDemo Google工作表。
   1. 添加三列（红色、绿色和蓝色），并为三个不同的运动衫添加相应的值。
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **根据要求配置受众**

   1. 导航到受众中的区段(请参 ***阅步骤2:有关更多详细信息*** ，请 **[在“AEM Screens”页面中配置ContextHub](configuring-context-hub.md)**，设置受众细分。)

   1. 添加三个 **新段For_Red**、 **For_Green**&#x200B;和 **For_Blue**。

   1. 选 **择For_Red** ，然后单 **击操作栏中的** “编辑”。

   1. 拖放比 **较：属性** -编辑器的属性，然后单击配置图标以编辑属性。
   1. 从“ **第一个属性名称”的下拉菜单中选择“****工具表／值/1/2”**

   1. 从下 **拉菜** 单中选择 **“大于”(Greater** -than)运算符

   1. 选择数 **据类型** ，作为 **数字**

   1. 从“ **第二个属性名称** ”的下拉菜单中选择 **googlesheets/value/1/1**。

   1. 拖放另一 **个比较：属性** -编辑器的属性，然后单击配置图标以编辑属性。
   1. 从 **“首个属性名称”的下拉菜单中选择** googlesheets/value/1/2 ****。

   1. 从下 **拉菜** 单中选择 **“大于”(Greater** -than)运算符

   1. 选择数 **据类型** ，作为 **数字**

   1. 从“ **第二个属性名称** ”的下拉菜单中选择 **googlesheets/value/1/0**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同样，编辑比较属性规则并将其添加到 **For_Blue段** ，如下图所示：

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同样，编辑比较属性规则并将其添加到** For_Green **区段，如下图所示：

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >您会注意到，对于区段 **For_Green** 和 **For_Green**，无法在编辑器中解析数据，因为目前仅第一个比较有效，与Google工作表中的值相同。

1. 导航并选择您的 **DataDrivenRetail** 渠道（序列渠道），然后单击操 **作栏中的编辑** 。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >您应该已使用“ **Properties** Properties **—********** Personalization Chub”选项卡设置ContextHub配置。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   要在启动定位流 **程时正确列** 出活动 **** ，您必须选择品牌和区域。

1. **添加默认图像**

   1. 将默认图像添加到渠道，然后单击定 **位**。
   1. 从下 **拉菜单中选择品** 牌 **和活动** ，然后单击开始 **定位**。

   1. 单击&#x200B;**开始定位**。
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   在开始定位之前，必须通过单击侧边栏中的&#x200B;**+ Add Experience Targeting来添加区段(** For_Green **、** For_Red **和** For_Blue **** )，如下图所示。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 将图像添加到所有三个不同的屏幕，如下所示。

   ![retail_targeting](assets/retail_targeting.gif)

1. **检查预览**

   1. 单击“ **预览”。** 此外，打开Google工作表并更新其值。
   1. 更改所有三个不同列的值，您会注意到显示图像会根据库存中的最高值进行更新。
   ![retail_result](assets/retail_result.gif)

