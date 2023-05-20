---
title: Kickstart指南
seo-title: Kickstart Guide
description: 請依照本頁面的說明建立示範AEM Screens專案。 它可協助您建立數位看板體驗，從安裝和設定新專案開始，一直到在AEM Screens播放器中檢視您的內容。
feature: Overview, Digital Signage
role: User
level: Beginner
exl-id: 9b7c7f50-2846-4727-a0ec-0220b4cd52c4
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 2%

---

# Kickstart指南 {#kickstart-guide}

AEM Screens快速入門示範如何設定和執行AEM Screens專案。 它會逐步帶您設定基本的數位看板體驗，以及將資產和/或視訊等內容新增至每個管道，並進一步將內容發佈至AEM Screens播放器。

>[!NOTE]
>開始處理專案詳細資料之前，請確定您已安裝AEM Screens的最新Feature Pack。 您可以從以下網址下載最新的Feature Pack： [軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。

## 前提条件 {#prerequisites}

請依照下列步驟，為AEM Screens建立範例專案，並進一步將內容發佈至Screens播放器。

>[!NOTE]
>下列教學課程會示範如何在Chrome作業系統播放器中播放管道的內容。

>[!IMPORTANT]
>**OSGi組態設定**
>您必須啟用空白反向連結，以允許裝置將資料發佈至伺服器。 例如，如果停用空白反向連結屬性，裝置就無法張貼熒幕擷圖。 目前，其中部分功能僅在OSGi設定中啟用Apache Sling反向連結篩選允許空白時才能使用。 儀表板可能會顯示警告，指出安全性設定可能會阻止這些功能的部分功能運作。
>請依照下列步驟啟用 ***Apache Sling反向連結篩選器允許空白***：


## 允許空的反向連結請求 {#allow-empty-referrer-requests}

1. 導覽至 **Adobe Experience Manager Web主控台設定** 透過AEM執行個體 — >槌子圖示 — > **作業** —> **網頁主控台**.

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web主控台設定** 隨即開啟。 搜尋Sling反向連結。

   若要搜尋Sling查閱者屬性，請按 **Command+F** 的 **Mac** 和 **Control+F** 的 **Windows**.

1. 檢查 **允許空白** 選項，如下圖所示。

   ![图像](assets/config/empty-ref2.png)

1. 按一下 **儲存** 以啟用Apache Sling反向連結篩選允許空白。

## 在5分鐘內建立數位看板體驗 {#creating-a-digital-signage-experience-in-minutes}

### 建立AEM Screens專案 {#creating-project}

第一步是建立AEM Screens專案。

1. 導覽至您的Adobe Experience Manager (AEM)執行個體，然後按一下 **Screens**. 或者，您可以直接從 `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. 按一下 **建立畫面專案** 以建立新的畫面專案。 輸入標題為 **DemoScreens** 並按一下 **儲存**.

   ![图像](assets/kickstart/demo-1.png)

   >[!NOTE]
   >建立專案後，您會回到「畫面專案」首頁。 您現在可以選取專案。 在專案中，有5個標題為 **應用**， **頻道**， **裝置**， **位置**、和 **時程表**.

### 建立頻道 {#creating-channel}

建立AEM Screens專案後，您需要建立一個管理內容的新管道。

請依照下列步驟，為您的專案建立新管道：

1. 建立專案後，選取 **DemoScreens** 專案並選取 **頻道** 資料夾，如下圖所示。 按一下 **+建立** 動作列中的。

   ![图像](assets/kickstart/demo-2.png)

1. 選擇 **序列頻道** 從精靈中並按一下 **下一個**.
   ![图像](assets/kickstart/demo-3.png)

1. 輸入 **標題** 作為 **TestChannel** 並按一下 **建立**.

   ![图像](assets/kickstart/demo-4.png)

   此 **TestChannel** 現在已新增至您的管道資料夾，如下圖所示。

   ![图像](assets/kickstart/demo-5.png)

### 新增內容至頻道 {#adding-content}

頻道準備就緒後，您需要將AEM Screens播放器顯示的內容新增到頻道。

請依照下列步驟，將內容新增至頻道(**TestChannel**)中：

1. 導覽至 **示範專案** 您已建立並選取 **TestChannel** 從 **頻道** 資料夾。

1. 按一下 **編輯** （請參閱下圖）。 的編輯器 **TestChannel** 隨即開啟。

   ![图像](assets/kickstart/demo-6.png)

1. 按一下可切換動作列左側側面板的圖示，開啟資產和元件。

1. 拖放您要新增至頻道的元件。

   ![图像](assets/kickstart/demo-7.png)

### 建立位置 {#creating-location}

管道備妥後，您需要建立位置。

>[!NOTE]
>***位置*** 劃分您的各種數位看板體驗，並根據各種熒幕的位置包含顯示器的設定。

請依照下列步驟，為您的專案建立新位置：

1. 導覽至 **示範專案** 您已建立並選取 **位置** 資料夾。

1. 按一下 **+建立** 動作列中的。

1. 選取 **位置** 從精靈中並按一下 **下一個**.

1. 輸入 **名稱** （輸入標題為） **TestLocation**)並按一下 **建立**.

此 **TestLocation** 已建立並新增至您的 **位置** 資料夾。


### 建立位置顯示 {#creating-display}

建立位置後，您需要為位置建立新的顯示區。

>[!NOTE]
>***顯示*** 代表在一或多個熒幕上執行的數位體驗。

1. 導覽至 **TestLocation** 並選取它。

1. 按一下 **建立** 動作列中的。

   ![图像](assets/kickstart/demo-disp1.png)

1. 選取 **顯示** 從 **建立** 精靈並按一下 **下一個**.

   ![图像](assets/kickstart/demo-disp2.png)

1. 輸入 **標題** 作為 **LobbyDisplay** 並按一下 **建立**.

   ![图像](assets/kickstart/demo-disp3.png)

   標題為的新顯示 **TestDisplay** 現在已新增至您的位置 **TestLocation**，如下圖所示。

   ![图像](assets/kickstart/demo-disp4.png)

### 指派管道 {#assigning-channel}

專案設定完成後，您必須將頻道指派給顯示區，才能檢視內容。

1. 瀏覽至所需顯示區，從 **DemoScreens** —> **位置** —> **TestLocation** —> **LobbyDisplay**.

1. 點選/按一下 **指派頻道** 動作列中的。

   ![图像](assets/kickstart/demo-assign1.png)

   或者,

   點選/按一下 **儀表板** ，然後按一下 **+指派頻道** 從 **已指派的管道和排程** 面板。

   ![图像](assets/kickstart/demo-assign2.png)

1. 此 **頻道指定任務** 對話方塊開啟。

1. 從 **設定** 選項，選擇頻道 **依路徑**  和 **支援的事件** 作為 **初始載入** 和 **閒置畫面**.

   >[!NOTE]
   >
   >此 **頻道角色**， **優先順序**、和 **中斷方法** 預設會填入所有內容。 另請參閱 [管道屬性](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) 區段，以進一步瞭解頻道指派屬性。

   ![图像](assets/kickstart/demo-assign3.png)

   此外，您也可以選取 **啟用期間** 和 **遞回排程**.

   >[!NOTE]
   >此 *遞回排程* 可讓您設定頻道的週期性排程。 您可以為管道設定多個週期排程。
   >另請參閱 [遞回排程](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) 以取得更多詳細資料。

1. 按一下 **儲存** 設定您的偏好設定後。

### 註冊裝置並指派裝置給顯示器 {#registering-device}

您必須使用AEM儀表板註冊裝置。

>[!IMPORTANT]
>Chrome作業系統播放器可在開發人員模式下安裝為Chrome瀏覽器外掛程式，而不需要實際的Chrome播放器裝置。 若要進行安裝，請遵循下列步驟：
>
>1. 按一下 [此處](https://download.macromedia.com/screens/) 以下載最新的Chrome Player。
>1. 解壓縮並儲存在磁碟上。
>1. 開啟Chrome瀏覽器並選取 **擴充功能** 或直接導覽至「 」 ***chrome://extensions***.
>1. 切換至 **開發人員模式** 從右上角。
>1. 按一下 **載入已解壓縮** 從左上角，並載入解壓縮的Chrome Player。
>1. Check **AEM Screens Chrome Player** 外掛程式（如果可在擴充功能清單中取得）。
>1. 開啟新標籤，然後按一下 **應用程式** 圖示瀏覽，或直接導覽至 ***chrome://apps***.
>1. 按一下 **AEM Screens** 啟動Chrome Player的外掛程式。 依預設，播放器會以全熒幕模式啟動。 按下 **esc** 以結束全熒幕模式。


開啟Chrome作業系統播放器後，請依照下列步驟註冊Chrome裝置。

1. 導覽至 **裝置** 從AEM執行個體取得專案的資料夾。

1. 點選/按一下 **裝置管理員** 動作列中的。

   ![图像](assets/kickstart/demo-register1.png)

1. 點選/按一下 **裝置註冊** 從右上角。

1. 選取所需的裝置，然後點選/按一下 **註冊裝置**.

   ![图像](assets/kickstart/demo-register2.png)

1. 等候裝置傳送其註冊代碼，同時檢查 **註冊代碼** 從您的Chrome裝置。
   ![图像](assets/kickstart/demo-register3.png)

1. 如果 **註冊代碼** 在這兩部電腦上相同，請點選/按一下 **驗證** 在AEM中。

1. 將所需的名稱設為 **ChromeDeviceforDemo** ，然後按一下 **註冊**.

   ![图像](assets/kickstart/demo-register4.png)

1. 按一下 **指派顯示區** 從 **裝置註冊成功** 對話方塊。

   ![图像](assets/kickstart/demo-register5.png)

1. 選取要顯示為 **DemoScreens** —> **位置** —> **TestLocation** —> **LobbyDisplay** 並按一下 **指派**.

   ![图像](assets/kickstart/demo-device6.png)

1. 成功指派裝置後，您將會看到以下確認。

   ![图像](assets/kickstart/demo-register8.png)

1. 點選/按一下 **完成** 以完成註冊程式。 您應該可以從顯示儀表板檢視已註冊的裝置。

   ![图像](assets/kickstart/demo-register9.png)

### 在Chrome播放器中檢視內容 {#viewing-content-output}

您頻道中的所有資產現在都會在Chrome作業系統播放器上播放。

恭喜您現在在AEM Screens頻道中播放內容！

![图像](assets/kickstart/demo-video-screens.gif)
