---
title: Feature Pack 202103發行說明
description: 「請詳閱本頁，瞭解2021年3月5日發行的AEM Screens Feature Pack 202103相關資訊。」
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# Feature Pack 202103發行說明 {#release-notes-for-feature-pack}

>[!CAUTION]
>建議您升級至最新版Adobe Experience Manager (AEM)。 Screens提供AEM 6.3 Screens平台的維護支援。

## 可用性 {#availability}

AEM Screens已發行AEM 6.5 Feature Pack 7。

您可以從以下網站下載AEM Screens 6.5.7版的最新Feature Pack： [軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。 導覽至 **Adobe Experience Manager** 標籤並搜尋 **Screens** 以取得標題為 **AEM 6.5 Screens FP7**.

## 发布日期 {#release-date}

AEM Screens Feature Pack 202103的發行日期為2021年3月5日。

### 新增功能 {#what-is-new}

* **AEM Screens自動註冊播放器**

   手動大量註冊數千個播放器非常麻煩，而且會增加時間和成本。 為簡化此程式，自動註冊播放器功能可讓您在AEM中指定預先共用金鑰，並可透過設定檔案或行動裝置管理(MDM)解決方案將其布建至播放器。

   請參閱 [自動註冊播放器](/help/user-guide/auto-registration-players.md) 以取得更多詳細資料。


* **使用企業行動管理大量布建Android Player**

   大量部署Android播放器時，手動向AEM註冊每個單一播放器會變得繁瑣。 強烈建議使用EMM （企業行動管理）解決方案，例如VMWare Airwatch、MobileIron或Samsung Knox，從遠端布建和管理您的部署。 AEM Screens Android播放器支援業界標準的EMM AppConfig，以允許遠端布建。

   請參閱 [使用企業行動管理大量布建Android Player](/help/user-guide/implementing-android-player.md#implementation) 以取得更多詳細資料。


### 错误修复 {#bug-fixes}

* 提升運算效能 `clientlib` 和 `asset hashes`.

* 如果快取未失效，SmartSync移轉會中斷播放器。

* 離線快取並未建立，如果「工作分派」具有 *OfflineConfig*.

* 因不支援反向連結原則strict-origin-when-cross-origin而中斷的Tizen播放器更新。

* 變更指派的管道排程 *重複* 欄位中斷UI。

* 更新離線內容失敗，發生查詢例外。

* 互動式體驗互動期間，轉換之間的時間延遲現在已修正。

* 失敗的設定更新要求造成空白畫面。

### 已發行的AEM Screens Players {#released-aem-screens-players}

下列AEM Screens Player已針對AEM 6.5 Feature Pack 7發行：

* Chrome作業系統
* Windows
* Linux

#### AEM Screens播放器下載  {#aem-screens-player-downloads}

若要下載最新的AEM Screens播放器並深入瞭解錯誤修正，請參閱 **[AEM Screens播放器下載](https://download.macromedia.com/screens/index.html)**.
