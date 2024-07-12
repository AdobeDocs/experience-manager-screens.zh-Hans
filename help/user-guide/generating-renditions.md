---
title: 视频演绎版
description: 了解如何为您的AEM Screens项目生成全高清呈现。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# 视频演绎版 {#video-renditions}

您可以生成手动和自动的全高清呈现。 以下部分介绍了将演绎版添加到资源的工作流。

## 自动生成全高清呈现版本 {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>如果AEM Screens视频演绎版无法在您的设备上以最佳方式播放，请联系硬件供应商以了解视频的规格。 这样做有助于在设备上获得最佳性能。 它可帮助您创建自己的自定义视频配置文件，您可以在其中为FFMPEG提供相应的参数以生成演绎版。 然后，使用以下步骤将自定义视频配置文件添加到配置文件列表。
>
>另请参阅[视频疑难解答](troubleshoot-videos.md)，以调试和解决频道中的视频播放问题。

请按照以下步骤自动生成全高清呈现：

1. 单击Adobe Experience Manager链接（左上方），然后单击锤子图标，以便您能够单击&#x200B;**工作流**。

   单击&#x200B;**模型**。

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. 在工作流模型管理中，单击&#x200B;**DAM更新资产**&#x200B;模型，然后单击操作栏中的&#x200B;**编辑**。

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. 在&#x200B;**DAM更新资产**&#x200B;窗口中，双击&#x200B;**FFmpeg转码**&#x200B;步骤。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 单击&#x200B;**进程**&#x200B;选项卡。
1. 在&#x200B;**参数**中向列表输入全高清配置文件，如下所示：
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. 单击&#x200B;**确定**。

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. 单击&#x200B;**DAM更新资产**&#x200B;屏幕左上角的&#x200B;**保存**。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. 导航到&#x200B;**Assets**&#x200B;并上传新视频。 单击视频，然后打开演绎版侧边栏。 请注意两个全高清视频。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. 从侧边栏打开&#x200B;**呈现版本**。

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. 请注意两个新的全高清呈现版本。

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## 手动生成全高清呈现版本 {#manually-generating-full-hd-renditions}

请按照以下步骤手动生成全高清呈现：

1. 单击Adobe Experience Manager链接（左上方），然后单击锤子图标，以便您可以单击“工具”并单击“**工作流**”。

   单击&#x200B;**模型**。

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. 在工作流模型管理中，单击&#x200B;**Screens更新资产**&#x200B;模型，然后单击&#x200B;**启动工作流**&#x200B;以打开&#x200B;**运行工作流**&#x200B;对话框。

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. 单击&#x200B;**有效负载**&#x200B;中所需的视频，然后单击&#x200B;**运行**。

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. 导航到&#x200B;**Assets**，深入到您的资源，然后单击该资源。

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. 打开&#x200B;**呈现形式**&#x200B;侧边栏。 请注意新的全高清呈现版本。

   ![step8_-_open_theridationssiderail](assets/step8_-_open_therenditionssiderail.png)
