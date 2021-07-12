---
title: 视频演绎版
seo-title: 视频演绎版
description: 可查看本页以了解有关为 Screens 项目生成全高清演绎版的信息。
seo-description: 可查看本页以了解有关为 Screens 项目生成全高清演绎版的信息。
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
feature: 创作屏幕
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 64%

---

# 视频演绎版 {#video-renditions}

您可以手动和自动生成全高清演绎版。以下部分介绍了将演绎版添加到资产的工作流。

## 自动生成全高清演绎版  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>如果 AEM Screens 视频演绎版在您的设备上播放效果不佳，请联系硬件供应商以获取视频的规格。这将有助于在设备上获得最佳性能，并因此创建您自己的自定义视频配置文件，您可以在该配置文件中为 FFMPEG 提供适当的参数以生成演绎版。随后，可使用以下步骤将您的自定义视频配置文件添加到配置文件列表。
>
>另外，还请参阅[对视频进行故障诊断](troubleshoot-videos.md)，以调试渠道中播放的视频并对视频问题进行故障诊断。

请按照以下步骤自动生成全高清演绎版：

1. 选择 Adobe Experience Manager 链接（左上方），然后单击锤子图标以选择工具，从而选择&#x200B;**工作流**。

   单击&#x200B;**模型**&#x200B;以进入工作流模型管理。

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. 选择&#x200B;**DAM更新资产**&#x200B;模型，然后单击操作栏中的编辑，以打开&#x200B;**DAM更新资产**&#x200B;窗口。

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. 双击 **FFmpeg 转码**&#x200B;步骤。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 选择&#x200B;**进程**&#x200B;选项卡以编辑进程参数。在&#x200B;**Arguments**&#x200B;的列表中输入全高清配置文件，如下所示：***,profile:fullhd-bp,profile:fullhd-hp***&#x200B;并单击&#x200B;**确定**。

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. 单击 **DAM 更新资产**&#x200B;屏幕左上方的&#x200B;**保存**。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. 导航到&#x200B;**资产**，然后上传一个新视频。单击视频并打开演绎版侧边栏，此时您会注意到这两个全高清视频。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. 从侧边栏中打开&#x200B;**演绎版**。

   ![step11_-_open_therenditionssiadreg](assets/step11_-_open_therenditionssiderail.png)

1. 您将发现两个新的全高清演绎版。

   ![step12_-_2_new_renditionsadededtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## 手动生成全高清演绎版 {#manually-generating-full-hd-renditions}

请按照以下步骤手动生成全高清演绎版：

1. 选择 Adobe Experience Manager 链接（左上方），然后单击锤子图标以选择工具，从而选择&#x200B;**工作流**。

   单击&#x200B;**模型**&#x200B;以进入工作流模型管理。

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. 选择&#x200B;**屏幕更新资产**&#x200B;模型，然后单击&#x200B;**启动工作流**&#x200B;以打开&#x200B;**运行工作流**&#x200B;对话框。

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. 在&#x200B;**Payload**&#x200B;中选择所需的视频，然后单击&#x200B;**Run**。

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. 导航到&#x200B;**资产**，向下展开您的资产，然后单击它。

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. 打开&#x200B;**演绎版**&#x200B;侧边栏，此时您将发现新的全高清演绎版。

   ![step8_-_open_therendissiarget](assets/step8_-_open_therenditionssiderail.png)
