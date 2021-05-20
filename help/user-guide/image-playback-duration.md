---
title: 图像播放持续时间
seo-title: 图像播放持续时间
description: 可查看本页以了解有关图像播放持续时间的信息。
seo-description: 可查看本页以了解有关图像播放持续时间的信息。
contentOwner: jsyal
source-git-commit: 69a40e437fa9b19e283bcf1a1322d18e17990a49
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 4%

---


# 图像播放持续时间{#image-playback-duration}

## 概述 {#overview}

创建序列渠道并向其添加图像后，默认情况下，所有图像都将假定播放持续时间是在渠道级别配置中定义的。 任何单个图像仍可以覆盖默认值，并且其播放持续时间会有所不同，这是通过编辑特定图像组件的播放持续时间来完成的。

### 前提条件 {#prerequisites}

在开始实施此功能之前，请确保已将项目设置为开始实施此功能的先决条件。 例如，

1. 创建AEM Screens项目（在此示例中，**ChannelLevelPlayback**）

1. 在&#x200B;**Channels**&#x200B;文件夹下，创建序列渠道作为&#x200B;**PlaybackChannel**

1. 将内容添加到&#x200B;**PlaybackChannel**

## 编辑渠道级别的图像播放持续时间分配{#editing-channel-level-image-playback-duration-assignment}

以下部分介绍如何编辑AEM Screens渠道中内容的播放持续时间。

### 更新渠道{#updating-the-playback-duration-for-images-in-a-channel}中图像的播放持续时间

请按照以下步骤了解如何更新渠道级别图像播放持续时间分配：

1. 导航到序列渠道&#x200B;**PlaybackChannel**。

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 在渠道编辑器中添加两个或更多图像，如下图所示。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 选择通道中的所有图像，然后单击左上角的扳手图标（如下图所示）以打开“通道级别配置”对话框。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **** 页面对话框打开。

   >[!NOTE]
   >
   >默认情况下，渠道中的图像会设置为8秒的播放持续时间。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   编辑从8000(ms)到3000(ms)的&#x200B;**持续时间**，即3秒。 单击&#x200B;**Page**&#x200B;对话框右上角的复选标记以保存更改。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 查看结果{#viewing-the-result}

更新渠道播放持续时间（在本例中为所有三幅图像）后，您会注意到图像现在将播放3秒，而不是8秒（默认值）。

![channel_preview](assets/channel_preview.gif)

