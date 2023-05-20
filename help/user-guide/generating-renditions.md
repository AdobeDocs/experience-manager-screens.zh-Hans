---
title: 視訊轉譯
seo-title: Video Renditions
description: 請依照本頁所述操作，瞭解如何為您的Screens專案產生Full HD轉譯。
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

# 視訊轉譯 {#video-renditions}

您可以產生手動和自動的Full HD轉譯。 下節將說明將轉譯新增至資產的工作流程。

## 自動產生Full HD轉譯  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>如果AEM Screens視訊轉譯無法在您的裝置上以最佳方式播放，請聯絡硬體廠商，取得視訊的規格。 這將有助於在裝置上取得最佳效能，因此可建立您自己的自訂視訊設定檔，您可以在其中提供適當的引數讓FFMPEG產生您的轉譯。 接著，使用下列步驟，將您的自訂視訊設定檔新增至設定檔清單。
>
>此外，另請參閱 [疑難排解影片](troubleshoot-videos.md) 對頻道中的視訊播放進行偵錯和疑難排解。

請依照下列步驟自動產生Full HD轉譯：

1. 選取Adobe Experience Manager連結（左上方），然後按一下槌子圖示以選取工具 **工作流程**.

   按一下 **模型** 以輸入工作流程模型管理。

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. 選取 **DAM更新資產** ，然後按一下動作列中的「編輯」以開啟 **DAM更新資產** 視窗。

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. 連按兩下 **FFmpeg轉碼** 步驟。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 選取 **程式** 索引標籤來編輯程式引數。 輸入Full HD設定檔至清單 **引數** 作為： ***，profile:fullhd-bp,profile:fullhd-hp*** 並按一下 **確定**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. 按一下 **儲存** 左上角 **DAM更新資產** 畫面。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. 導覽至 **資產** 並上傳新影片。 按一下視訊並開啟「轉譯」側邊欄，您會發現兩部Full HD視訊。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. 開啟 **轉譯** 從側邊欄移除。

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. 您會發現兩個新的Full HD轉譯。

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## 手動產生Full HD轉譯 {#manually-generating-full-hd-renditions}

請依照下列步驟手動產生Full HD轉譯：

1. 選取Adobe Experience Manager連結（左上方），然後按一下槌子圖示以選取工具 **工作流程**.

   按一下 **模型** 以輸入工作流程模型管理。

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. 選取 **畫面更新資產** 模型，然後按一下 **開始工作流程** 以開啟 **執行工作流程** 對話方塊。

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. 在「 」中選取所需的影片 **裝載** 並按一下 **執行**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. 導覽至 **資產**，深入研究您的資產，然後按一下它。

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. 開啟 **轉譯** 側邊欄，您會注意到新的Full HD轉譯。

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
