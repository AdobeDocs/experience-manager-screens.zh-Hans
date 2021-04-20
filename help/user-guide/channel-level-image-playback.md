---
title: 渠道级批量图像播放持续时间
seo-title: 渠道级批量图像播放持续时间
description: 本页介绍如何编辑特定图像组件的播放持续时间。
seo-description: 本页介绍如何编辑特定图像组件的播放持续时间。
uuid: 4ebb00a9-b04d-4dfe-9fee-2348a2e2c142
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: df3cf999-0c8d-4754-8b58-5c6ced2c8ca5
docset: aem65
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 4%

---


# 渠道级批量图像播放持续时间{#channel-level-bulk-image-playback-duration}

## 概述 {#overview}

在创建序列渠道并向序列渠道添加图像后，默认情况下，所有图像都将采用在序列级别配置中定义的播放持续时间。 任何单个图像仍然可以覆盖默认图像，并具有不同的播放持续时间，这可通过编辑特定图像组件的播放持续时间来实现。

### 前提条件 {#prerequisites}

在开始实现此功能之前，请确保已将项目设置为实现此功能的开始的先决条件。 例如，

1. 创建AEM Screens项目示例，**ChannelLevelPlayback**。

1. 在&#x200B;**渠道**&#x200B;文件夹下创建一个序列渠道，作为&#x200B;**PlaybackChannel**。

1. 将内容添加到&#x200B;**PlaybackChannel**。

## 编辑渠道级图像播放持续时间分配{#editing-channel-level-image-playback-duration-assignment}

以下部分介绍如何在AEM Screens渠道中编辑内容的播放持续时间。

### 更新渠道{#updating-the-playback-duration-for-images-in-a-channel}中图像的播放持续时间

请按照以下步骤了解如何更新渠道级图像播放持续时间分配：

1. 导航到序列渠道&#x200B;**PlaybackChannel**。

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 在渠道编辑器中添加两个或更多图像，如下图所示。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 选择渠道中的所有图像，然后单击左上角的扳手图标（如下图所示）以打开渠道级配置对话框。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **页面** 对话框打开。

   >[!NOTE]
   >默认情况下，渠道中的图像设置为8秒的播放持续时间。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   编辑从8000(ms)到3000(ms)的&#x200B;**持续时间**，即3秒。 单击&#x200B;**页面**&#x200B;对话框右上方的复选标记以保存更改。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 查看结果{#viewing-the-result}

更新渠道播放持续时间（在此示例中，所有三张图像）后，您会注意到图像现在将播放3秒而不是8秒（默认值）。

![渠道_预览](assets/channel_preview.gif)

