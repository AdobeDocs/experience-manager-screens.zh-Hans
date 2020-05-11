---
title: 多区域布局
seo-title: 多区域布局
description: 多区域布局允许您创建多个区域内容并使用各种资产，如可组合到单个屏幕中的视频、图像和文本。 可查看本页以了解更多信息。
seo-description: 多区域布局允许您创建多个区域内容并使用各种资产，如可组合到单个屏幕中的视频、图像和文本。 可查看本页以了解更多信息。
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
translation-type: tm+mt
source-git-commit: afe069d0cd297d0e2280ffb6093e0b0d129c675d
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 6%

---


# 多区域布局 {#multi-zone-layout}

以下页介绍了多区域布局的用法，并涵盖以下主题：

* 概述
* 创建多区域布局
* 前提条件
* 在一个或多个区域中使用单个资产
* 在一个或多个区域中使用排序的内容

## 概述 {#overview}

***多区域布局*** 允许您创建多个区域内容并使用各种资源，如可组合到单个屏幕中的视频、图像和文本。 您可以拖入图像、视频和文本，使其全部融合在一起，创建直观的数字体验。

根据项目要求，有时您需要在渠道中使用多个区域并将其作为一个完整的单位进行编辑。例如，具有相关社交媒体源的产品序列在单个渠道的三个单独区域中运行。

## 创建多区域布局 {#creating-multi-zone-layout}

创建渠道时，您可以使用不同的模板在渠道中创建区域。 您可以添加单个图像、视频或嵌入式渠道，该允许在序列中显示多个资产。

### 前提条件 {#prerequisites}

在开始实现此功能之前，请确保您已准备好项目作为开始实现多区域布局的先决条件。 例如，

* 创建标题为“区域”的AEM Screens项 **目**
* 在标题为MultiZoneDisplay的 **位**&#x200B;置下创建&#x200B;**显示屏**

在Zones项目中创 **建标题为** MultiZone **的** 渠道。 按照以下步骤操作：

**创建渠道**

1. 选择 Adobe Experience Manager 链接（左上方），然后选择&#x200B;**屏幕**。Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.
1. 导航到 **渠道** 文件夹，然 **后单** 击操作栏中的创建。

1. 从创 **建向导中选择左侧L** -bar分 **屏渠道** 。

1. 单 **击** “下一步 **”，然后输** 入Multi **Zone**&#x200B;标题。

1. 单击 **创建** ，以完成渠道创建。

![screen_shot_2018-12-07at120026pm](assets/screen_shot_2018-12-07at120026pm.png)

### 在一个或多个区域中使用单个资产 {#using-single-assets-in-one-or-more-zones}

您可以在所有三个不同区域中使用单个资产，如图像或视频。 请按照以下步骤实施：

1. **向渠道添加内容**

   1. 导航到 **Zones** —> **渠道**—**> MultiZone**。
   1. Select the **MultiZone** channel and click **Edit** from the action bar to open the editor.

1. **向渠道添加图像**

   要在所有三个区域中播放单个图像或视频，只需在渠道编辑器中拖放该图像。

### 在一个或多个区域中使用排序的内容 {#using-sequenced-content-in-one-or-more-zones}

如果希望区域在三个不同区域中显示图像或内容序列以及静态图像，请按照以下步骤了解详细信息。

1. **创建渠道文件夹**

   1. 导航到 **Zones** —> **MultiZone** —> **渠道，然** 后单击 **** 操作栏中的创建。
   1. Select **Channels Folder** from the **Create** wizard and click **Next**.
   1. Enter the title as **EmbeddedChannels** and click **Create**.
   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **将两个渠道添加到渠道文件夹**

   1. 导航到 **Zones** —> **渠道****—>** EmbeddedChannels **，然** 后单击操作栏中的创建。
   1. 从创 **建向导** 中选 **择序列渠道** ，以创建标题为 **Zone1的渠道**。
   1. Select **Zone1** and click **Edit** from the action bar to open the editor.
   1. 将很少的图像拖放到此渠道。
   同样，在EmbeddedChannels文件夹中创建另一个标 **题为** Zone2 **的序列** 渠道。

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   添加到Zone1序列渠道 **编辑器** 的图像如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-1.png)

   添加到Zone2序列渠道 **编辑器** 的图像如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-2.png)

1. **将嵌入式序列／组件添加到主渠道(MultiZone)**

   1. 导航到 **Zones** —> **渠道** — **>** MultiZone。
   1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。
   1. 将嵌入式序 **列组件拖** 放到两个区域。

1. **将内容添加到所有三个区域**

   1. 导航到 **Zones** —> **渠道** — **>** MultiZone。
   1. 选择其中一个区域中的嵌入式序列。
   1. 单击编 **辑器** 中某个嵌入式序列的“配置（扳手）”图标。
   1. 选择渠道路径 **作为** Zones **—>** BemdeddedChannels **—** Zone1渠道，如 ****&#x200B;下图所示。
   同样，将Zone2添 **加到** 编辑器中的另一个嵌入式序列组件。

   ![图像](/help/user-guide/assets/multi-zone/multizone-3.png)

#### 查看结果 {#viewing-the-result}

使用上述步骤实施多区域布局后，将显示以下输出，如下图所示。

单击 **预览** ，从渠道编辑器中视图以下输出，该输出在两个不同的区域中显示内容。 左侧和右侧区域（两者都使用嵌入式序列作为组件）。

>[!NOTE]
>如果尝试视图Screens播放器中的内容，请确保单击“更 **新脱机内容** ”渠道仪表板。

![new2-1](/help/user-guide/assets/multi-zone/screens-multi1.gif)


