---
title: 项目级图像播放持续时间
seo-title: 项目级图像播放持续时间
description: '此功能允许您在项目级别定义图像回放持续时间。 '
seo-description: '此功能允许您在项目级别定义图像回放持续时间。 '
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---


# 项目级图像播放持续时间{#project-level-image-playback}

## 概述 {#overview}

此功能允许您在项目级别定义图像回放持续时间。 默认情况下，所有图像都继承此播放持续时间。 如果在项目级别未定义持续时间，则默认播放时间为8秒。

### 前提条件 {#prerequisites}

在使用此功能之前，请确保将项目设置为开始实施此功能的先决条件。 例如，

1. 创建AEM Screens项目（在本例中，**ProjectLevelPlayback**）

1. 在&#x200B;**渠道**&#x200B;文件夹下创建一个序列渠道，作为&#x200B;**PlayBackChannel**

1. 向&#x200B;**PlayBackChannel**&#x200B;添加内容

   ![资产](assets/image_playback1.png)

   例如，以下图像显示添加到&#x200B;**PlayBackChannel**&#x200B;编辑器的图像：

   ![资产](assets/image_playback2.png)

## 编辑项目级图像播放持续时间分配{#editing-project-level-image-playback-duration-assignment}

以下部分介绍如何编辑AEM Screens项目中内容的播放持续时间。

### 更新项目级别{#updating-the-playback-duration-for-images-in-a-project}的图像的播放持续时间


>[!NOTE]
>
>如果要更新图像或渠道级回放持续时间，请参阅[渠道级图像回放持续时间](channel-level-image-playback.md)。

请按照以下步骤了解如何更新项目级图像播放持续时间：

1. 导航到项目&#x200B;**ProjectLevelPlayback**，然后单击操作栏中的&#x200B;**属性**。
   ![资产](assets/image_playback3.png)

1. 选择渠道中的所有图像，然后单击左上角的扳手图标（如下图所示）以打开渠道级别配置对话框。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **页面** 对话框打开。

   >[!NOTE]
   >
   >默认情况下，渠道中的图像设置为8秒的播放持续时间，而视频以其默认持续时间播放。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   编辑从8000(ms)到3000(ms)的&#x200B;**持续时间**，即3秒。 单击&#x200B;**页面**&#x200B;对话框右上方的复选标记以保存更改。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 查看结果{#viewing-the-result}

更新渠道播放持续时间（在本例中为所有三幅图像）后，您会注意到图像现在将播放3秒，而不是8秒（默认值）。

![渠道_预览](assets/channel_preview.gif)

