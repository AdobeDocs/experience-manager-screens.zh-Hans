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
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# 视频演绎版 {#video-renditions}

您可以生成手动和自动全高清呈现版本。 以下部分介绍了将演绎版添加到资源的工作流。

## 自动生成全高清呈现版本  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>如果AEM Screens视频演绎版无法在您的设备上以最佳方式播放，请联系硬件供应商以了解视频的规格。 这有助于在设备上获得最佳性能，从而创建您自己的自定义视频配置文件，您可以在其中提供合适的FFMPEG参数来生成演绎版。 然后，使用以下步骤将自定义视频配置文件添加到配置文件列表。
>
>另请参阅 [视频疑难解答](troubleshoot-videos.md) 对渠道中的视频播放进行调试和故障排除。

请按照以下步骤自动生成全高清呈现版本：

1. 单击Adobe Experience Manager链接（左上方），然后单击锤子图标，以便 **工作流**.

   单击 **模型**.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. 在工作流模型管理中，单击 **DAM更新资产** 模型和点击 **编辑** 从操作栏中。

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. 在 **DAM更新资产** 窗口中，双击 **FFmpeg转码** 步骤。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 单击 **进程** 选项卡。
1. 将全高清配置文件输入列表 **参数** 如下所示：
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. 单击&#x200B;**确定**。

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. 单击 **保存** 左侧的 **DAM更新资产** 屏幕。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. 导航到 **资产** 并上传新视频。 单击视频，然后打开演绎版侧边栏。 请注意两个全高清视频。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. 打开 **节目** 从侧边栏移出。

   ![step11_-_open_theridationssiderail](assets/step11_-_open_therenditionssiderail.png)

1. 请注意两个新的全高清呈现版本。

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## 手动生成全高清呈现版本 {#manually-generating-full-hd-renditions}

请按照以下步骤手动生成全高清呈现版本：

1. 单击Adobe Experience Manager链接（左上方），然后单击锤子图标，以便您可以单击“tools（工具）” ，然后单击 **工作流**.

   单击 **模型**.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. 在工作流模型管理中，单击 **屏幕更新资产** 模型，然后单击 **启动工作流** 以打开 **运行工作流** 对话框。

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. 单击中的所需视频 **有效负荷** 并单击 **运行**.

   ![步骤6_-_选择_所需视频](assets/step6_-_select_thedesiredvideo.png)

1. 导航到 **资产**，深入到您的资源，然后单击该资源。

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. 打开 **节目** 侧边栏。 请注意新的全高清呈现版本。

   ![step8_-_open_theridationssiderail](assets/step8_-_open_therenditionssiderail.png)
