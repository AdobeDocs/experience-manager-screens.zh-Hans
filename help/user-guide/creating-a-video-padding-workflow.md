---
title: 创建视频填充工作流
seo-title: 创建视频填充工作流
description: 可查看本页以了解有关在工作流中为资产创建视频边距的信息。
seo-description: 可查看本页以了解有关在工作流中为资产创建视频边距的信息。
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---


# 创建视频填充工作流 {#creating-a-video-padding-workflow}

本节涵盖下列主题：

* **概述**
* **前提条件**
* **创建视频填充工作流**
   * **创建工作流**
   * **在AEM Screens项目中使用工作流**

* **验证工作流的输出**

## 概述 {#overview}

以下用例涉及放置视频(示例：1280 x 720)，在显示器为1920 x 1080的渠道中，将视频放置在0x0（左上方）。 不应以任何方式拉伸或修改视频，也不应在视 **频组** 件中使用封面。

视频将作为对象显示，从像素1到像素1280，从像素1到像素720，其余渠道为默认颜色。

## 前提条件 {#prerequisites}

在创建视频工作流之前，请完成以下先决条件：

1. 在AEM实例的“资 **产** ”文件夹中上传视频
1. 创建一个AEM Screens项目( **例如TestVideoRendition**)和一个名为(**VideoRending**)的渠道，如下图所示：

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## 创建视频填充工作流 {#creating-a-video-padding-workflow-1}

要创建视频填充工作流，您必须为视频创建一个工作流，然后在AEM Screens项目渠道中使用相同的工作流。

请按照以下步骤创建和使用工作流：

1. 创建工作流
1. 在AEM Screens项目中使用工作流

### 创建工作流 {#creating-a-workflow}

请按照以下步骤为视频创建工作流：

1. 导航到AEM实例，然后单击侧边栏中的工具。 选择 **工作流** —> **模型** ，以创建新模型。

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. 单击 **模型** —>创 **建** — **>创**&#x200B;建模型。 在“添 **加工作流** 模型”中输 **入“标题**”(作 **为视频再现)******&#x200B;和“名称”。 单击 **完成** ，以添加工作流模型。

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. 创建工作流模型后，选择模型(**VideoRendition**)，然后单 **击操作** 栏中的“编辑”。

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. 将命令行组 **件拖放** 到您的工作流。

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. 选择命 **令行组件** ，然后打开属性对话框。

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. 选择 **参数** 选项卡，在命令行——步 **骤属性对话框中输入字段** 。

   在Mime类 **型** ( ***视频/mp4)中输入格式，并输入命令(***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:color=black&quot; cq5dam.video.fullhd-hp.mp4**)开始“命令”字段中的***&#x200B;工作流 **** 。

   请参阅下面注 **释中有关** Mime **类型** 和命令的详细信息。

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. 选择工作流(**VideoRenditions**)，然后单击操 **作栏中的“开始工作流** ”以打开“运行工 **作流** ”对话框。

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. 在Payload中选择资产的路 **径** ( ***as***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4 **)，并将Title输入** RunVideoJadristors, **********&#x200B;作为RunVideoJadrist并单击运行。

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### 在AEM Screens项目中使用工作流 {#using-the-workflow-in-an-aem-screens-project}

请按照以下步骤使用您的AEM Screens项目中的工作流：

1. 导航到AEM Screens项&#x200B;**目(TestVideoRendition** —> **渠道****—>** VideoRendition)。

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Click **Edit** from the action bar. 拖放您最初上传到资产的视 **频**。

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. 上传视频后，单击“ **预览** ”以视图输出。

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## 验证工作流的输出 {#validating-the-output-for-the-workflow}

您可以通过以下方式验证输出：

* 检查渠道中视频的预览
* 导航到 ***CRXDE Lite中的/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** ，如下图所示：

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

