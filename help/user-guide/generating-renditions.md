---
title: 视频演绎版
seo-title: Video Renditions
description: 关注此页面，了解如何为屏幕项目生成全高清演绎版。
seo-description: Follow this page to learn about generating full HD renditions for your Screens project.
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# 视频演绎版 {#video-renditions}

您可以生成手动和自动全高清呈现版本。 以下部分介绍了将演绎版添加到资源的工作流。

## 自动生成全高清呈现版本  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>如果AEM Screens视频演绎版无法在您的设备上以最佳方式播放，请联系硬件供应商以了解视频的规格。 这将有助于在设备上获得最佳性能，从而创建您自己的自定义视频配置文件，您可以在其中为FFMPEG提供适当的参数来生成演绎版。 随后，使用以下步骤将自定义视频配置文件添加到配置文件列表。
>
>此外，请参阅 [视频疑难解答](troubleshoot-videos.md) 调试和排查渠道中的视频播放问题。

请按照以下步骤自动生成全高清呈现版本：

1. 选择Adobe Experience Manager链接（左上方），然后单击锤子图标以选择要选择的工具 **工作流**.

   单击 **模型** 以进入工作流模型管理。

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. 选择 **DAM更新资产** ，然后单击操作栏中的“编辑”以打开 **DAM更新资产** 窗口。

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. 双击 **FFmpeg转码** 步骤。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 选择 **进程** 选项卡以编辑进程参数。 将全高清配置文件输入列表 **参数** 作为： ***，profile:fullhd-bp,profile:fullhd-hp*** 并单击 **确定**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. 单击 **保存** 左上角的 **DAM更新资产** 屏幕。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. 导航到 **资产** 并上传新视频。 单击视频，然后打开呈现版本侧边栏，您会看到两个全高清视频。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. 打开 **演绎版** 从侧边栏上删除。

   ![步骤11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. 您将会注意到两个新的全高清呈现版本。

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## 手动生成全高清呈现版本 {#manually-generating-full-hd-renditions}

请按照以下步骤手动生成全高清呈现版本：

1. 选择Adobe Experience Manager链接（左上方），然后单击锤子图标以选择要选择的工具 **工作流**.

   单击 **模型** 以进入工作流模型管理。

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. 选择 **屏幕更新资产** 模型，然后单击 **启动工作流** 以打开 **运行工作流** 对话框。

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. 在中选择所需的视频 **有效负荷** 并单击 **运行**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. 导航到 **资产**，深入到您的资源，然后单击该资源。

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. 打开 **演绎版** 侧边栏中，您会看到新的全高清呈现版本。

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
