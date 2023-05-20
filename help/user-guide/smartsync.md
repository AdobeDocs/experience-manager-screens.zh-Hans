---
title: 從ContentSync轉換為SmartSync
seo-title: Transitioning from ContentSync to SmartSync
description: 請依照本頁瞭解SmartSync功能，以及如何從ContentSync轉換到SmartSync。
seo-description: Follow this page to learn about SmartSync feature and how you can transition from ContentSync to SmartSync.
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b8d0c089-af79-403e-870f-fb46b66fecd3
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 1%

---

# 從ContentSync轉換為SmartSync {#transitioning-from-contentsync-to-smartsync}

本節提供SmartSync功能的概觀，並說明如何最小化伺服器負載/儲存及網路流量，以降低成本。

## 概述 {#overview}

SmartSync是AEM Screens使用的最新機制。 它取代目前用來快取離線頻道並將它們傳送給播放器的方法。

它會在伺服器端和使用者端執行。

**在伺服器端**：

* 管道的內容（包括資產）會快取到 */var/contentsync*.
* 快取會透過資訊清單向播放器公開，資訊清單會說明可供顯示的內容。

**使用者端**：

* 播放器會根據上述產生的資訊清單更新其內容。

### 使用SmartSync的好處 {#benefits-of-using-smartsync}

SmartSync功能可為您的AEM Screens專案提供許多優點。 它允許

* 大幅降低網路流量與伺服器端儲存需求
* 只有在資產遺失或變更時，播放器才會智慧地下載資產
* 伺服器端和使用者端儲存最佳化

>[!NOTE]
>
>Adobe強烈建議對AEM Screens專案使用SmartSync。

## 從ContentSync移轉至SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>如果您已安裝AEM 6.3 Feature Pack 5和AEM 6.4 Feature Pack 3，您可以啟用資產的SmartSync來改善磁碟空間使用量。 若要啟用SmartSync，請遵循以下章節，從ContentSync轉變為SmartSync，進而啟用SmartSync。
>
>SmartSync適用於支援伺服器AEM 6.4.3 FP3的Screens Player。
>
>請參閱 [AEM Screens播放器下載](https://download.macromedia.com/screens/) 以下載最新的播放器。 下表說明每個平台所需的最低播放器版本：

| **Platform** | **最低支援的播放器版本** |
|---|---|
| Android | 3.3.72 |
| Chrome作業系統 | 1.0.136 |
| Windows | 1.0.136 |

請依照下列步驟，從ContentSync轉變為SmartSync：

1. 從ContentSync移轉至SmartSync時，必須先清除ContentSync快取，才能啟動SmartSync。

   使用連結從您的執行個體導覽至ContentSync主控台 ***https://localhost:4502/libs/cq/contentsync/content/console.html*** 並按一下 **清除快取**，如下圖所示：

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >第一次使用SmartSync之前，必須清除所有內容快取。

1. 導覽至 **Adobe Experience Manager Web主控台設定** 透過AEM執行個體 — >槌子圖示 — > **作業** —> **網頁主控台**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience Manager Web主控台設定** 隨即開啟。 搜尋 *offlinecontentservice*.

   用於搜尋 **Screens離線內容服務** 屬性，按下 **Command+F** 的 **Mac** 和 **Control+F** 的 **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 按一下 **儲存** 以啟用 **Screens離線內容服務** 屬性，因此使用AEM Screens的SmartSync。
1. 啟用SmartSync後，您必須導覽至專案並按一下 **更新離線內容** *（從動作列），* 如下圖所示。

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)
