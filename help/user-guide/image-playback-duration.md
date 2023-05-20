---
title: 影像播放持續時間
seo-title: Image Playback Duration
description: 請依照本頁面的說明了解影像播放持續時間。
seo-description: Follow this page to learn about image playback duration.
contentOwner: jsyal
source-git-commit: 69a40e437fa9b19e283bcf1a1322d18e17990a49
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 1%

---


# 影像播放持續時間 {#image-playback-duration}

## 概述 {#overview}

建立序列頻道並在其中新增影像後，根據預設，所有影像都會採用頻道層級設定中定義的播放持續時間。 任何個別影像仍可覆寫預設值，並具有不同的播放持續時間，這是透過編輯特定影像元件的播放持續時間來完成的。

### 前提条件 {#prerequisites}

開始實作此功能之前，請確定您已設定專案作為開始實作此功能的先決條件。 例如，

1. 建立AEM Screens專案(在此範例中， **ChannelLevelPlayback**)

1. 建立序列管道為 **PlaybackChannel** 在 **頻道** 資料夾

1. 新增內容至 **PlaybackChannel**

## 編輯頻道層級影像播放持續時間指派 {#editing-channel-level-image-playback-duration-assignment}

以下章節說明如何在AEM Screens頻道中編輯內容的播放持續時間。

### 更新頻道中影像的播放持續時間 {#updating-the-playback-duration-for-images-in-a-channel}

請依照下列步驟操作，瞭解如何更新頻道層級影像播放期間指派：

1. 導覽至序列頻道 **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 按一下 **編輯** 以開啟編輯器。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 在管道編輯器中新增兩個或多個影像，如下圖所示。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 選取色版中的所有影像，然後按一下左上方的扳手圖示（如下圖所示）以開啟「色版層級設定」對話方塊。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **頁面** 對話方塊開啟。

   >[!NOTE]
   >
   >根據預設，頻道中的影像會設定為8秒的播放持續時間。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   編輯 **持續時間** 從8000 (ms)到3000 (ms)，即3秒。 按一下右上方的勾號 **頁面** 對話方塊以儲存變更。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 檢視結果 {#viewing-the-result}

更新頻道播放持續時間後（在此範例中是全部三個影像），您會注意到影像現在會播放3秒而不是8秒（預設值）。

![channel_preview](assets/channel_preview.gif)

