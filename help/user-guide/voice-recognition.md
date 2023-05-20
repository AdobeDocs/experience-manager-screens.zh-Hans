---
title: AEM Screens中的語音辨識
description: 本頁說明AEM Screens的語音辨識功能。
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 6cf0aa9f-7bac-403f-a113-51727c1f5374
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 3%

---

# AEM Screens中的語音辨識 {#voice-recognition}

>[!IMPORTANT]
>
>**重要隱私權資訊**
>
>使用語音辨識功能時，請遵循您所在地區適用的所有法律和道德准則（包括但不限於向使用者提供播放器正在使用語音辨識的可見通知）。 Adobe Inc不會接收、儲存或處理任何語音相關資訊。 AEM Screens播放器使用內建在瀏覽引擎中的標準網路語音API。 在幕後，此API會將您語音的波形傳送至Google的伺服器，以進行從語音到文字的轉換，而此文字會由播放器根據設定的關鍵字進行比對。
>
>請參閱 [網頁語音API上的Google隱私權白皮書](https://www.google.com/chrome/privacy/whitepaper.html#speech) 以取得更多詳細資料。


語音辨識功能可讓您在由語音互動驅動的AEM Screens頻道中變更內容。

內容作者可以將顯示器設定為啟用語音。 此功能的目的是讓客戶利用語音作為與顯示器互動的方法。 類似的使用案例包括在商店中尋找產品推薦、在用餐者和餐廳訂購功能表專案。 此功能可提升使用者的協助工具，並可大幅提升客戶體驗。

>[!NOTE]
>播放器硬體必須支援語音輸入，例如麥克風。

## 實作語音辨識 {#implementing}

>[!IMPORTANT]
> 語音辨識功能僅適用於Chrome作業系統和Windows播放器。

若要在您的AEM Screens專案中實作語音辨識，您必須啟用顯示器的語音辨識，並將每個頻道與唯一標籤建立關聯，以觸發頻道轉換。

下節說明如何在AEM Screens專案中啟用和使用語音辨識功能。

## 以全熒幕或拆分畫面頻道切換檢視內容 {#sequence-channel}

使用語音辨識功能之前，請確定您擁有專案和頻道，且已為專案設定內容。

1. 以下範例示範專案 **VoiceDemo** 和三個序列頻道 **主要**， **冷飲**、和 **熱飲**，如下圖所示。

   ![图像](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >若要瞭解如何建立管道或新增內容至管道，請參閱 [建立和管理管道](/help/user-guide/managing-channels.md)

   或者,

   您可以建立三個序列色版 **主要**， **冷飲**、和 **熱飲**&#x200B;以及額外的1x2拆分畫面頻道 **SplitScreen** 如下圖所示。

   ![图像](assets/voice-recognition/vr-emb-1.png)

1. 導覽至每個管道並新增內容。 例如，導覽至 **VoiceDemo** —> **頻道** —> **主要** 並選取頻道。 按一下 **編輯** 以開啟編輯器，並根據需求新增內容（影像/影片）。 同樣地，將內容新增至兩者 **冷飲** 和 **熱飲** 頻道。

   管道現在包含資產（影像），如下圖所示。

   **主要**:

   ![图像](assets/voice-recognition/vr-4.png)

   **冷飲**：

   ![图像](assets/voice-recognition/vr-3.png)

   **熱飲**：

   ![图像](assets/voice-recognition/vr-2.png)

   如果您已將拆分畫面頻道新增至專案，請導覽至 **SplitScreen** 和拖放兩個內嵌序列並將路徑新增至 **冷飲** 和 **熱飲** 頻道，如下圖所示。
   ![图像](assets/voice-recognition/vr-emb-6.png)


### 設定管道標籤 {#setting-tags}

新增內容至管道後，您需要導覽至每個管道，並新增可觸發語音識別的適當標籤。

請依照下列步驟，將標籤新增至您的頻道：

1. 導覽至每個管道並新增內容。 例如，導覽至 **VoiceDemo** —> **頻道** —> **主要** 並選取頻道。

1. 按一下 **屬性** 動作列中的。

   ![图像](assets/voice-recognition/vr-5.png)

1. 導覽至 **基本知識** 標籤並選取已存在的標籤 **標籤** 欄位或建立新欄位。

   您可以輸入標籤和點選的新名稱來建立新標籤 `return` 鍵，如下圖所示：

   ![图像](assets/voice-recognition/vr-6.png)

   或者,

   您也可以預先從專案的AEM例項建立標籤，然後選取那些標籤。 依照中說明的步驟操作後， [建立標籤](#creating-tags)，您可以從位置選取標籤並將其新增至您的頻道，如下圖所示：

   ![图像](assets/voice-recognition/vr-tag1.png)

1. 同樣地，新增標題為 **熱** 至 **熱飲** 頻道。

1. 如果您使用「拆分畫面」頻道，請新增兩個標籤(**熱** 和 **冷**)重新命名為 **SplitScreen** 頻道屬性，如下圖所示。

   ![图像](assets/voice-recognition/vr-emb-7.png)

1. 按一下 **儲存並關閉** 完成後。


### 建立標籤 {#creating-tags}

請依照下列步驟建立標籤：

1. 導覽至您的AEM執行個體。

1. 按一下工具圖示 — > **標籤**.
   ![图像](assets/voice-recognition/vr-7.png)

1. 按一下 **建立** —> **建立名稱空間**.
   ![图像](assets/voice-recognition/vr-tag3.png)

1. 輸入專案名稱，例如， **VoiceDemo** 並按一下 **建立**.

1. 選取 **VoiceDemo** 專案並按一下 **建立標籤** 動作列中的。
   ![图像](assets/voice-recognition/vr-tag4.png)

1. 輸入標簽名稱，然後按一下 **提交**.
   ![图像](assets/voice-recognition/vr-tag5.png)

現在，您可以在AEM Screens專案中使用這些標籤。

### 指定頻道給顯示器並啟用語音辨識 {#channel-assignment}

1. 在中建立顯示區 **位置** 資料夾，如下圖所示。

   ![图像](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >若要瞭解如何將管道指派給顯示區，請參閱 [建立和管理顯示區](/help/user-guide/managing-displays.md).

1. 指派管道 **主要**， **冷飲**、和 **熱飲** 至您的 **LobbyDisplay**. 此外，如果您使用 **SplitScreen** 您專案的頻道，請確定您將其也指派給顯示區。

   >[!NOTE]
   >如果您已建立拆分畫面頻道，請指派 **SplitScreen** 頻道也到您的顯示區。

1. 指派管道時，為每個管道設定下列屬性。

   | **渠道名称** | **优先级** | **支持的事件** |
   |---|---|---|
   | 主要 | 2 | 初始載入、閒置畫面、計時器 |
   | 熱飲 | 1 | 用户交互 |
   | 冷飲 | 1 | 用户交互 |
   | SplitScreen | 1 | 用户交互 |

   >[!NOTE]
   >
   >若要瞭解如何將管道指派給顯示區，請參閱 [建立和管理顯示區](/help/user-guide/managing-displays.md).

1. 將管道指派給顯示區後，請導覽至 **LobbyDisplay** 並選取顯示區。 選取 **屬性** 動作列中的。

1. 導覽至 **顯示** 標籤並啟用 **啟用語音** 下的選項 **內容**.

   ![图像](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >必須從顯示器啟用語音辨識功能。

### 在Chrome播放器中檢視內容 {#viewing-content}

完成上述步驟後，您可以註冊Chrome裝置以檢視輸出。

>[!NOTE]
>請參閱 [裝置註冊](device-registration.md) 以瞭解如何在AEM Screens播放器上註冊裝置。

**序列頻道的所需輸出**

此 **主要** 頻道正在播放其內容，但當您使用具有關鍵字的字詞時 **熱** 例如 *我想要一杯熱飲*，頻道會開始播放 **熱飲** 頻道。

同樣地，如果您使用具有關鍵字的文字 **冷** 例如 *我想喝點冷飲*，頻道會開始播放 **冷飲** 頻道。

**分割畫面頻道的所需輸出**

此 **主要** 頻道正在播放其內容，但當您使用具有關鍵字的字詞時 **熱** 和 **冷** 共同使用，例如 *我想看看熱飲和冷飲的選單*，頻道會開始播放 **SplitScreen** 頻道。 如果您說 *返回主功能表*，則會切換回主要通道。
