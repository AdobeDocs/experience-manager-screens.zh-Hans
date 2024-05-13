---
title: 项目级图像播放持续时间
description: 了解如何在项目级别定义图像播放持续时间。
contentOwner: jsyal
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 1%

---


# 项目级图像播放持续时间 {#project-level-image-playback}

## 概述 {#overview}

此功能允许您在项目级别定义图像播放持续时间。 默认情况下，所有图像都将继承此播放持续时间。 如果在项目级别未定义持续时间，则默认播放8秒将继续进行。

### 先决条件 {#prerequisites}

在使用此功能之前，请将项目设置为开始实施此功能的先决条件。 例如，

1. 创建一个AEM Screens项目(在此示例中， **ProjectLevelPlayback**)。
1. 创建序列渠道为 **PlayBackChannel** 在 **渠道** 文件夹。
1. 将内容添加到 **PlayBackChannel**.

   ![资产](assets/image_playback1.png)

   例如，下图显示了添加到 **PlayBackChannel** 编辑者：

   ![资产](assets/image_playback2.png)

## 编辑项目级别图像播放持续时间分配 {#editing-project-level-image-playback-duration-assignment}

以下部分介绍如何在AEM Screens项目中编辑内容的播放持续时间。

### 在项目级别更新图像的播放持续时间 {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>如果要更新图像或渠道级别的播放持续时间，请参阅 [渠道级别图像播放持续时间](channel-level-image-playback.md).

请按照以下步骤了解如何更新项目级图像播放持续时间：

1. 导航到您的项目 **ProjectLevelPlayback** 并单击 **属性** 从操作栏中。
   ![资产](assets/image_playback3.png)

1. 单击渠道中的所有图像，然后单击左上角的扳手图标（如下图所示），以打开“渠道级别配置”对话框。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. 此 **页面** 对话框打开。

   >[!NOTE]
   >
   >默认情况下，渠道中的图像被设置为8秒的播放持续时间，并且视频以其默认持续时间播放。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   编辑 **持续时间** 从8000（毫秒）到3000（毫秒），即3秒。 选择右上角的复选标记 **页面** 对话框，以保存更改。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 查看结果 {#viewing-the-result}

更新渠道播放持续时间（在本例中是所有三个图像）后，请注意，现在播放图像的时间是3秒而不是8秒（默认值）。

![channel_preview](assets/channel_preview.gif)

