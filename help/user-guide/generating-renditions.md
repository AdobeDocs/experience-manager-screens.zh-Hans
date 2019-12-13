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
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

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

   Click **Models** to enter the workflow models management.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Select the **DAM Update Asset** model and click Edit from the action bar to open the **DAM Update Asset** window.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. 双击 **FFmpeg 转码**&#x200B;步骤。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 选择&#x200B;**进程**&#x200B;选项卡以编辑进程参数。Enter the full HD profiles to the list in **Arguments** as: ***,profile:fullhd-bp,profile:fullhd-hp*** and click **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. 单击 **DAM 更新资产**&#x200B;屏幕左上方的&#x200B;**保存**。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. 导航到&#x200B;**资产**，然后上传一个新视频。单击视频并打开演绎版侧边栏，您会注意到这两个全高清视频。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Open **Renditions** from the side rail.

   ![step11_-_open_therenditionssiagre](assets/step11_-_open_therenditionssiderail.png)

1. 您将发现两个新的全高清演绎版。

   ![step12_-_2_new_renditionsaded to thevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## 手动生成全高清演绎版 {#manually-generating-full-hd-renditions}

请按照以下步骤手动生成全高清演绎版：

1. 选择 Adobe Experience Manager 链接（左上方），然后单击锤子图标以选择工具，从而选择&#x200B;**工作流**。

   Click **Models** to enter the workflow models management.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Select the **Screens Update Asset** model, and click the **Start Workflow** to open the **Run Workflow** dialog box.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Select the desired video in the **Payload** and click **Run**.

   ![step6_-_select_thedesignedvideo](assets/step6_-_select_thedesiredvideo.png)

1. 导航到&#x200B;**资产**，向下展开您的资产，然后单击它。

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. 打开&#x200B;**演绎版**&#x200B;侧边栏，此时您将发现新的全高清演绎版。

   ![step8_-_open_therenditionssiagret](assets/step8_-_open_therenditionssiderail.png)

