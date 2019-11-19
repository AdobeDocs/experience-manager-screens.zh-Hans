---
title: 创建视频填充工作流
seo-title: 创建视频填充工作流
description: 可查看本页以了解如何在您的资产的工作流中创建视频填充。
seo-description: 可查看本页以了解如何在您的资产的工作流中创建视频填充。
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 创建视频填充工作流 {#creating-a-video-padding-workflow}

本节涵盖以下主题：

* **概述**
* **前提条件**
* **创建视频填充工作流**
   * **创建工作流**
   * **在AEM Screens项目中使用工作流**

* **验证工作流的输出**

## 概述 {#overview}

以下用例涉及放置视频(示例：1280 x 720)，其中显示器为1920 x 1080，并且视频被放置在0x0（左上角）。 不应以任何方式拉伸或修改视频，也不应在视频组 **件中使用** “封面”。

视频将作为对象显示，从像素1到像素1280，跨像素1到像素720，通道的其余部分为默认颜色。

## 前提条件 {#prerequisites}

在创建视频工作流之前，请完成以下先决条件：

1. 在AEM实例的 **Assets** 文件夹中上传视频
1. 创建AEM Screens项目(例如， **TestVideoRendition**)和名为(**VideoRendering**)的渠道，如下图所示：

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## 创建视频填充工作流 {#creating-a-video-padding-workflow-1}

要创建视频填充工作流，您必须为视频创建工作流，然后在AEM Screens项目渠道中使用相同的工作流。

请按照以下步骤创建和使用工作流：

1. 创建工作流
1. 在AEM Screens项目中使用工作流

### 创建工作流 {#creating-a-workflow}

请按照以下步骤为视频创建工作流：

1. 导航到AEM实例，然后单击侧边栏中的工具。 选择 **工作流** —&gt; **模型** ，以创建新模型。

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. 单击“ **模型** ”(Models **)—&gt;“** 创建 **”(Create**)—&gt;“创建模型”(Create Model)。 在“工 **作流添加模型** ”中输入标题 **(** VideoRendition **)******&#x200B;和名称。 单击 **完成** ，以添加工作流模型。

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. 创建工作流模型后，选择模型(**VideoRendition**)，然后单击操 **作栏中的“编辑** ”。

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. 将**命令行**组件拖放到您的工作流中。

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. 选择命 **令行组件** ，然后打开属性对话框。

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. 选择“ **参数** ”选项卡，在“命令行——步 **骤属性”对话框中输入字段** 。

   在 **Mime类型** (作为 ***video/mp4***)中输入格式，并将命令作为(***/usr/local/Cellar/ffmpeg -i ${filename} -vf "pad=1920:height=1080:x=0:y=0:color=black" cq5dam.video.fullhd-hp.mp4***)以在“命令”字段中启动 **工作流** 。

   请参阅下面的说明 **中有关Mime类型****和命** 令的详细信息。

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. 选择工作流(**VideoRenditions**)，然后单击操作栏中的“ **启动工作流** ”以打开“运行工作流 **** ”对话框。

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. 在 **Payload** (as ***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***)中选择资产的路径，然后输入**Title *(as ***RunVideo***)并单击“ **** Run”。

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### 在AEM Screens项目中使用工作流 {#using-the-workflow-in-an-aem-screens-project}

请按照以下步骤在AEM Screens项目中使用工作流：

1. 导航到AEM Screens项目(**TestVideoRendition** —&gt;渠道 **—&gt;** VideoRendition ****)。

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Click **Edit** from the action bar. 拖放您最初上传到资产的视 **频**。

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. 上传视频后，单击“ **预览** ”以查看输出。

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## 验证工作流的输出 {#validating-the-output-for-the-workflow}

您可以通过以下方式验证输出：

* 检查渠道中视频的预览
* 导航到 ***CRXDE lite中的/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** ，如下图所示：

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

