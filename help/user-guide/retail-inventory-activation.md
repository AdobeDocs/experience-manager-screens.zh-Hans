---
title: 零售库存目标激活
description: 了解这个AEM Screens用例，该用例展示了三种不同颜色运动衫的零售库存量。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# 零售库存目标激活 {#retail-inventory-targeted-activation}

以下用例演示了基于Google工作表中的值的三个不同图像。

## 描述 {#description}

此用例展示了三种不同颜色运动衫的零售库存库存。 根据Google工作表中记录的可用库存运动衫数量，将显示数量最高的图像（红色、绿色或蓝色运动衫）。

红色、绿色或蓝色毛衣根据可用毛衣数量的最大值显示。

## 前提条件 {#preconditions}

在开始实施零售库存定位激活之前，了解如何在AEM Screens项目中设置&#x200B;***数据存储区***、***受众分段***&#x200B;和&#x200B;***为渠道启用定位***。

有关详细信息，请参阅[在AEM Screens中配置ContextHub](configuring-context-hub.md)。

## 基本流量 {#basic-flow}

执行以下步骤以实施零售库存激活用例：

1. **填充Google工作表**

   1. 导航到ContextHubDemo Google工作表。
   1. 为三件不同的运动衫添加三列（红色、绿色和蓝色）以及相应的值。

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **根据要求配置受众**

   1. 导航到受众中的区段(有关更多详细信息，请参阅&#x200B;**[在AEM Screens中配置ContextHub](configuring-context-hub.md)**&#x200B;页面中的&#x200B;***步骤2：设置受众分段***)。

   1. 添加三个新区段&#x200B;**For_Red**、**For_Green**&#x200B;和&#x200B;**For_Blue**。

   1. 单击&#x200B;**For_Red**，然后单击操作栏中的&#x200B;**编辑**。

   1. 将&#x200B;**比较：属性 — 属性**&#x200B;拖放到编辑器中。
   1. 单击&#x200B;**配置**&#x200B;图标。
   1. 从&#x200B;**First Property name**&#x200B;中的下拉列表中单击&#x200B;**Googlesheets/value/1/2**。
   1. 从下拉菜单中单击&#x200B;**运算符**，并作为&#x200B;**大于**。
   1. 单击&#x200B;**数据类型**，并作为&#x200B;**数字**。
   1. 从&#x200B;**第二个属性名称**&#x200B;中的下拉列表中单击&#x200B;**googleHeets/value/1/1**。
   1. 将&#x200B;**另一个比较：属性 — 属性**&#x200B;拖放到编辑器并单击&#x200B;**配置**&#x200B;图标。
   1. 从&#x200B;**First Property name**&#x200B;中的下拉列表中单击&#x200B;**Googlesheets/value/1/2**。
   1. 从下拉菜单中单击&#x200B;**运算符**，并作为&#x200B;**大于**。
   1. 单击&#x200B;**数据类型**，并作为&#x200B;**数字**。
   1. 从&#x200B;**第二个属性名称**&#x200B;中的下拉列表中单击&#x200B;**Googlesheets/value/1/0**。

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同样，编辑比较属性规则并将其添加到&#x200B;**For_Blue**&#x200B;区段，如下图所示：

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同样，编辑比较属性规则并将其添加到&#x200B;**For_Green**&#x200B;区段，如下图所示：

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >请注意，对于区段&#x200B;**For_Green**&#x200B;和&#x200B;**For_Green**，无法在编辑器中解析数据，因为根据Google工作表中的值，目前只有第一次比较有效。

1. 导航并单击您的&#x200B;**DataDrivenRetail**&#x200B;渠道（序列渠道）。
1. 单击操作栏中的&#x200B;**编辑**。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >您应该已经使用渠道&#x200B;**属性** > **Personalization**&#x200B;选项卡设置了&#x200B;**ContextHub** **配置**。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >在启动定位流程时，单击&#x200B;**品牌**&#x200B;和&#x200B;**区域**&#x200B;以使活动正确列出。

1. **添加默认图像**

   1. 将默认图像添加到您的频道，然后单击&#x200B;**定位**。
   1. 从下拉菜单中单击&#x200B;**品牌**&#x200B;和&#x200B;**活动**，然后单击&#x200B;**开始定位**。
   1. 单击&#x200B;**开始定位**。

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >在开始定位之前，通过从侧边栏中选择&#x200B;**+添加体验定位**&#x200B;来添加区段（**For_Green**、**For_Red**&#x200B;和&#x200B;**For_Blue**），如下图所示。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 将图像添加到所有三种不同的方案中，如下所示。

   ![零售定位](assets/retail_targeting.gif)

1. **正在检查预览**

   1. 单击&#x200B;**预览。**&#x200B;此外，打开您的Google工作表并更新其值。
   1. 更改所有三个不同列的值。 请注意显示图像会根据清单中的最高值更新。

   ![retail_result](assets/retail_result.gif)
