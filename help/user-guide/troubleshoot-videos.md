---
title: 視訊播放設定和疑難排解
seo-title: Troubleshooting Videos
description: 請詳閱本頁面，瞭解如何在頻道中針對播放的視訊進行除錯和疑難排解。
seo-description: Follow this page to learn how to troubleshoot videos. When you upload a video to the DAM and add it your channel, you might encounter issues that video might not play in Screens player and this section describes how to debug and troubleshoot video playing in your channel.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 0%

---

# 視訊播放設定和疑難排解 {#video-playback-configuration-and-troubleshooting}

當您上傳影片至DAM並將其新增至您的頻道時，可能會遇到影片無法在Screens播放器中播放的問題。

以下小節說明如何在您的頻道中對播放的視訊進行偵錯和疑難排解。

## DAM轉譯 {#dam-renditions}

上傳視訊至頻道後，AEM應開始為其建立一些轉譯。 您可以在「資產」下檢視您的影片。

若要觀看影片：

1. 導覽至您的影片，例如 `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. 按一下視訊並展開左上角功能表，然後按一下 **轉譯**.

應該有不同的轉譯（MP4或M4V）。

如果沒有轉譯，請確認您在執行AEM的作業系統上已安裝ffmpeg。

>[!CAUTION]
>
>如果沒有轉譯，請確認您在執行AEM的作業系統上已安裝ffmpeg。
>
>按一下 [此處](https://www.ffmpeg.org/download.html) 以安裝ffmpeg。

## 視訊資產 {#video-assets}

如果您在視訊底下沒有看到來源屬性，可能是視訊未經過轉碼處理。 如果視訊已正確轉碼，它就會顯示在控制面板中，如下圖所示。

檢查是否已安裝ffmpeg及視訊設定檔。

![chlimage_1-2](assets/chlimage_1-2.png)

### 檢查視訊設定檔 {#checking-video-profile}

1. 導覽至 **視訊設定檔**，也就是說， `http://localhost:4502/etc/dam/video.html` 並按一下 **上傳測試視訊**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. 上傳測試視訊並按一下 **確定** 以開始轉碼。

   如果轉碼失敗，請展開ffmpeg輸出來瞭解ffmpeg主控台輸出中的任何錯誤。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   此外，如果視訊轉碼成功，也可以下載轉碼檔案。

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >在新增視訊至任何管道之前，請務必留出足夠的時間將視訊轉碼（應顯示新的標籤而不是處理中）。

### 使用視訊元件檢查設定檔 {#checking-profile-with-a-video-component}

如果視訊元件未正確設定，請從頁面設計檢查設定檔清單。

1. 導覽至您的頻道，然後選取 **設計** 模式。

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 選取視訊並開啟 **編輯** 對話方塊。 開啟 **設定檔** 標籤。

   >[!NOTE]
   >選取不同的設定檔（至少應有「高品質H.264」設定檔）。

### 在網頁播放器中檢查視訊 {#checking-the-video-in-the-web-player}

使用 **網頁播放器** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` 驗證瀏覽器（Chrome和Safari）中的播放。 Chrome用於Android裝置，而Safari則用於OSX和iOS瀏覽器。

如果影片未在Safari上執行，則無法在OSX和iOS播放器中執行。 這可能是編碼問題，必須對視訊重新編碼。

請依照下列步驟，使用DAM工作流程來建立FullHD轉譯：

1. 導覽至 *工作流程模型管理員*，即 `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. 選取 **畫面更新資產** 模型。
1. 按一下 **開始工作流程** 從動作列開啟 **執行工作流程** 對話方塊。

1. 在「 」中選取您的視訊資產 **裝載**.
1. 按一下 **執行**.

>[!NOTE]
>
>請稍候建立轉譯，但在幾秒/分鐘後（視視訊大小而定），在Safari上重新載入網頁播放器。

#### 疑難排解自動播放原則標幟 {#troubleshooting-autoplay-policy-flag}

如果AEM Screens播放器擷取視訊但並未顯示，您必須疑難排解自動播放原則標幟。

請依照下列步驟，針對Google的自動播放原則標幟問題進行疑難排解：

1. 導覽至 ***chrome://flags/#autoplay-policy***
1. 變更 **自動播放原則** 從 **預設** 至 **不需要使用者手勢**

1. 重新啟動網頁瀏覽器並更新播放器

>[!NOTE]
>
>若要進一步瞭解透過Chrome中的新自動播放原則提供良好使用者體驗的最佳實務，請參閱以下檔案： *自動播放原則變更*，也就是說， `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### 跨多個播放器同步視訊 {#syncing-video-across-multiple-players}

若要在多部裝置間同步播放視訊，您應該對視訊所屬順序使用絕對策略。

#### 要求 {#requirements}

* 相同的2+個播放器
* 理想類似的硬體
* 相同的網路拓撲（播放器會連線至與其內部系統時鐘一致的NTP伺服器）

#### 設定絕對策略 {#setting-up-the-absolute-strategy}

絕對策略：

* 計算錨記時間（當天午夜）
* 計算序列的持續時間（其所有專案的持續時間總和）
* 在任何時間點，它會透過求解序列_remaining_time = (current_time - anchor_time) % sequence_duration來計算目前應該播放哪個專案以及下一個專案。

請依照下列步驟設定絕對策略：

1. 導覽至您的管道作者，然後選取順序元件，如下圖所示。
1. 開啟其設定對話方塊。
1. 編輯 **策略** 並加入absolute。

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >播放器的作業系統必須有相同的時鐘。

**在OS X上對齊時鐘** 請依照下列步驟調整OSX的時鐘：

1. 開啟 **日期與時間** 每個OSX方塊的偏好設定
1. Check **自動設定日期和時間**
1. 在下拉式清單中貼上值0.pool.ntp.org、1.pool.ntp.org、2.pool.ntp.org、3.pool.ntp.org、time.apple.com或直接執行 *sudo ntpdate -u -v 0.pool.ntp.org*
1. 啟動2個以上的播放器

播放器開始新的對齊序列可能需要一些時間。
