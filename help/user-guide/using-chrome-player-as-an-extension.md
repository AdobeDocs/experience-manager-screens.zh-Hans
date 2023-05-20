---
title: 使用Chrome播放器作為擴充功能
seo-title: Using Chrome Player as an Extension
description: 請依照本頁面的說明安裝Chrome播放器作為瀏覽器擴充功能。
seo-description: null
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# 使用Chrome播放器作為擴充功能 {#using-chrome-player}

ChromeOS播放器可在開發人員模式下安裝為Chrome瀏覽器外掛程式，而不需要實際的Chrome播放器裝置。

>[!CAUTION]
>
> 若要進行快速示範、偵錯並疑難排解客戶問題，建議使用Chrome播放器作為疑難排解擴充功能。 此機制不應用於需要資訊站模式和中央管理的生產部署。

請依照本頁面的說明安裝Chrome播放器作為瀏覽器擴充功能。

1. 按一下 [此處](https://download.macromedia.com/screens/) 以下載最新的Chrome Player。

1. 解壓縮並儲存在磁碟上。

1. 開啟Chrome瀏覽器，然後按一下3點選單並選取 **更多工具** 從 **擴充功能** 位於右上角，或直接導覽至 `chrome://extensions`.

1. 切換至 **開發人員** 模式（從右上角）。

1. 按一下 **載入已解壓縮** 從左上角，並載入解壓縮的Chrome Player。

1. 如果擴充功能清單中有提供，請檢查AEM Screens Chrome Player外掛程式。

1. 開啟新標籤，然後從左上角按一下「應用程式」圖示，或直接導覽至 `chrome://apps`.

1. 按一下 **AEM Screens外掛程式** 以啟動Chrome Player。
   >[!NOTE]
   >
   > 依預設，播放器會以全熒幕模式啟動。 按下 **esc** 以結束全熒幕模式。


## 進階偵錯提示 {#advanced-debugging-tips}

1. 播放器從本機下載內容後，您可以前往「 」，瀏覽本機下載的內容 `http://localhost:24502`.

   >[!NOTE]
   >
   > 如果上述URL無法運作，表示播放器未指派顯示區或內容未成功下載。 檢查播放器設定JSON的網路索引標籤，以檢視播放器是否取得正確的詳細資料，以及是否有任何下載中的網路問題。

1. 您可以按一下滑鼠右鍵並檢查Chrome播放器的三個圖層
   **偵錯內容**：以滑鼠右鍵按一下內容並加以檢查，針對執行中的內容進行偵錯(內容功能表中應會有名為「Inspect」的單一專案)

   **偵錯韌體**：開啟管理員UI，然後按一下滑鼠右鍵並檢查以偵錯韌體（播放器）代碼（應該會有一個選項來檢查和檢查背景頁面，並模擬瀏覽器重新啟動）

   **偵錯背景頁面**：開啟管理員UI，然後按一下右鍵並檢查背景頁面（適用於http伺服器等背景服務）

## 升級播放器擴充功能 {#upgrading-player}

如果發行新版本的播放器，請依照下列步驟升級播放器擴充功能。 您也可以依照下列指示測試升級案例：

1. 關閉任何執行中的Chrome和播放器執行個體
1. 使用播放器檔案重新命名舊資料夾
1. 在與舊資料夾相同的位置解壓縮新zip
1. 啟動Chrome並瀏覽至 `chrome://extensions`
1. 檢查播放器圖示，然後按一下重新整理或重新載入按鈕
