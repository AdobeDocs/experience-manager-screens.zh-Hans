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
TQID: https://experienceleague.adobe.com/4xxCtO5lD71kiS-dSbTjTgycZDiWkQlHPdJOCVDrv38
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 424
ht-degree: 0%

---

# 视频演绎版 {#video-renditions}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

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
1. 在&#x200B;**参数**&#x200B;中向列表输入全高清配置文件，如下所示：
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
