---
title: 创建视频内边距工作流
seo-title: 创建视频内边距工作流
description: 可查看本页以了解有关在工作流中为资产创建视频内边距的信息。
seo-description: 可查看本页以了解有关在工作流中为资产创建视频内边距的信息。
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
feature: 创作屏幕
role: Administrator, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# 创建视频内边距工作流{#creating-a-video-padding-workflow}

本节涵盖以下主题：

* **概述**
* **前提条件**
* **创建视频内边距工作流**
   * **创建工作流**
   * **在AEM Screens项目中使用工作流**

* **验证工作流的输出**

## 概述 {#overview}

以下用例涉及放置视频(示例：1280 x 720)，其中显示器为1920 x 1080，并且视频被放置在0x0（左上方）。 不应以任何方式拉伸或修改视频，并且不应在视频组件中使用&#x200B;**Cover**。

视频将作为对象显示，从像素1到像素1280，从像素1到像素720向下显示，而通道的其余部分将是默认颜色。

## 前提条件 {#prerequisites}

在创建视频工作流之前，请完成以下先决条件：

1. 在AEM实例的&#x200B;**Assets**&#x200B;文件夹中上传视频
1. 创建AEM Screens项目（例如，**TestVideoRendition**）和名为(**VideoRendering**)的渠道，如下图所示：

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## 创建视频内边距工作流{#creating-a-video-padding-workflow-1}

要创建视频填充工作流，您必须为视频创建工作流，然后在AEM Screens项目渠道中使用该工作流。

请按照以下步骤创建和使用工作流：

1. 创建工作流
1. 在AEM Screens项目中使用工作流

### 创建工作流{#creating-a-workflow}

请按照以下步骤为视频创建工作流：

1. 导航到您的AEM实例，然后单击侧边栏中的工具。 选择&#x200B;**工作流** —> **模型**&#x200B;以创建新模型。

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. 单击&#x200B;**模型** —> **创建** —> **创建模型**。 在&#x200B;**添加工作流模型**&#x200B;中输入&#x200B;**标题**（作为&#x200B;**VideoRendition**）和&#x200B;**名称**。 单击&#x200B;**完成**&#x200B;以添加工作流模型。

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. 创建工作流模型后，选择模型(**VideoRendition**)，然后单击操作栏中的&#x200B;**编辑**。

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. 将&#x200B;**命令行**&#x200B;组件拖放到工作流中。

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. 选择&#x200B;**命令行**&#x200B;组件并打开属性对话框。

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. 选择&#x200B;**参数**&#x200B;选项卡，以输入&#x200B;**命令行 — 步骤属性**&#x200B;对话框中的字段。

   在&#x200B;**Mime类型**（作为&#x200B;***video/mp4***）中输入格式，并在&#x200B;**命令**&#x200B;字段中输入命令(***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:color=black&quot; cq5dam.video.fullhd-hp.mp4***)中输入启动工作流的格式。

   请参阅下面注释中&#x200B;**Mime类型**&#x200B;和&#x200B;**命令**&#x200B;的详细信息。

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. 选择工作流(**VideoRenditions**)，然后单击操作栏中的&#x200B;**启动工作流**&#x200B;以打开&#x200B;**运行工作流**&#x200B;对话框。

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. 在&#x200B;**Payload**(as ***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***)中选择资产的路径，然后输入&#x200B;**Title**&#x200B;作为&#x200B;***RunVideo***，然后单击&#x200B;**Run**。

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### 在AEM Screens项目{#using-the-workflow-in-an-aem-screens-project}中使用工作流

请按照以下步骤使用您的AEM Screens项目中的工作流：

1. 导航到AEM Screens项目（**TestVideoRendition** —> **渠道** —>**VideoRendition**）。

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. 单击操作栏中的&#x200B;**编辑**。 将您最初上传到&#x200B;**Assets**&#x200B;的视频拖放到其中。

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. 上传视频后，单击&#x200B;**预览**&#x200B;以查看输出。

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## 验证工作流{#validating-the-output-for-the-workflow}的输出

您可以通过以下方式验证输出：

* 检查渠道中的视频预览
* 导航到CRXDE Lite中的&#x200B;***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4***，如下图所示：

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
