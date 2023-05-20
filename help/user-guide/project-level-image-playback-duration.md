---
title: 專案層級影像播放持續時間
seo-title: Project Level Image Playback Duration
description: 此功能可讓您在專案層級定義影像播放持續時間。
seo-description: This functionality allows you to define image playback duration at the project level.
contentOwner: jsyal
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 1%

---


# 專案層級影像播放持續時間 {#project-level-image-playback}

## 概述 {#overview}

此功能可讓您在專案層級定義影像播放持續時間。 依預設，所有影像都會繼承此播放持續時間。 如果在專案層級未定義持續時間，預設的8秒播放將會繼續。

### 前提条件 {#prerequisites}

使用此功能之前，請務必先設定專案，作為開始實作此功能的先決條件。 例如，

1. 建立AEM Screens專案(在此範例中， **專案層級播放**)

1. 建立序列管道為 **PlayBackChannel** 在 **頻道** 資料夾

1. 新增內容至 **PlayBackChannel**

   ![資產](assets/image_playback1.png)

   例如，下列影像會示範新增至 **PlayBackChannel** 編輯者：

   ![資產](assets/image_playback2.png)

## 編輯專案層級影像播放持續時間指派 {#editing-project-level-image-playback-duration-assignment}

以下章節說明如何編輯AEM Screens專案中內容的播放持續時間。

### 更新專案層級影像的播放持續時間 {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>如果您想要更新影像或頻道層級播放持續時間，請參閱 [頻道層級影像播放持續時間](channel-level-image-playback.md).

請依照下列步驟操作，瞭解如何更新專案層級的影像播放持續時間：

1. 導覽至您的專案 **專案層級播放** 並按一下 **屬性** 動作列中的。
   ![資產](assets/image_playback3.png)

1. 選取色版中的所有影像，然後按一下左上方的扳手圖示（如下圖所示）以開啟「色版層級設定」對話方塊。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **頁面** 對話方塊開啟。

   >[!NOTE]
   >
   >根據預設，頻道中的影像會設定為8秒的播放持續時間，而視訊會以其預設持續時間播放。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   編輯 **持續時間** 從8000 (ms)到3000 (ms)，即3秒。 按一下右上方的勾號 **頁面** 對話方塊以儲存變更。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 檢視結果 {#viewing-the-result}

更新頻道播放持續時間後（在此範例中是全部三個影像），您會注意到影像現在會播放3秒而不是8秒（預設值）。

![channel_preview](assets/channel_preview.gif)

