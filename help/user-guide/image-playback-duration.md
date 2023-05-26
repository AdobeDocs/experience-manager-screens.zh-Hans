---
title: 图像播放持续时间
seo-title: Image Playback Duration
description: 关注此页面，了解图像播放持续时间。
seo-description: Follow this page to learn about image playback duration.
contentOwner: jsyal
source-git-commit: 69a40e437fa9b19e283bcf1a1322d18e17990a49
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 1%

---


# 图像播放持续时间 {#image-playback-duration}

## 概述 {#overview}

创建序列渠道并向其中添加图像后，默认情况下，所有图像都将采用渠道级别配置中定义的播放持续时间。 任何单个图像仍可以覆盖默认值，并且具有不同的播放持续时间，这是通过编辑特定图像组件的播放持续时间来实现的。

### 前提条件 {#prerequisites}

在开始实施此功能之前，请确保已将项目设置为开始实施此功能的先决条件。 例如，

1. 创建一个AEM Screens项目(在本例中， **ChannelLevelPlayback**)

1. 创建序列渠道为 **PlaybackChannel** 下 **渠道** 文件夹

1. 将内容添加到 **PlaybackChannel**

## 编辑渠道级别图像播放持续时间分配 {#editing-channel-level-image-playback-duration-assignment}

以下部分介绍了如何在AEM Screens渠道中编辑内容的播放持续时间。

### 更新渠道中图像的播放持续时间 {#updating-the-playback-duration-for-images-in-a-channel}

请按照以下步骤了解如何更新渠道级别图像播放持续时间分配：

1. 导航到序列渠道 **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 单击 **编辑** 以打开编辑器。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 在渠道编辑器中添加两个或更多图像，如下图所示。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 选择渠道中的所有图像，然后单击左上角的扳手图标（如下图所示）以打开“渠道级别配置”对话框。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **页面** 对话框打开。

   >[!NOTE]
   >
   >默认情况下，渠道中的图像设置为8秒的播放持续时间。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   编辑 **持续时间** 从8000（毫秒）到3000（毫秒），即3秒。 单击右上角的复选标记 **页面** 对话框以保存更改。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 查看结果 {#viewing-the-result}

更新频道播放持续时间后（在本例中是所有三个图像），您会注意到这些图像现在将播放3秒而不是8秒（默认值）。

![channel_preview](assets/channel_preview.gif)

