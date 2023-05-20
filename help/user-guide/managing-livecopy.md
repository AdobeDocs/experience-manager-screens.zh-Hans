---
title: 建立和管理即時副本
seo-title: Managing LiveCopy
description: 本頁說明如何建立和管理管道的即時副本。
seo-description: Follow this page to create live copy of a channel, view properties, check status, and propagate changes from a channel to its live copy.
uuid: 78ec7219-95ab-44d1-9514-1b97aded5bf4
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 84085a03-1798-4f1d-858c-6014a3f6aff6
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 4a4b3a83-2b02-42a0-86a7-fce6bbf47c7d
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 1%

---

# 建立和管理即時副本 {#creating-and-managing-a-live-copy}

本頁說明如何建立和管理管道的即時副本。

A ***即時副本*** 是特定網站內容的復本，其中與原始來源維持即時關係。 此即時關係可讓即時副本從來源繼承內容和頁面屬性。

本頁面說明如何建立管道的即時副本、檢視屬性、檢查狀態，以及將變更從管道傳播至其即時副本。


## 创建 Live Copy {#creating-a-live-copy}

請依照下列步驟，在您的專案資料夾中建立頻道的即時副本。

1. 選取Adobe Experience Manager連結（左上方），然後 **Screens**. 或者，您可以直接前往： `http://localhost:4502/screens.html/content/screens`.

1. 導覽至畫面專案，然後按一下 **頻道**.
1. 按一下 **建立** 並選取 **即時副本** 以建立頻道的即時副本。

1. 選取目的地並按一下 **下一個**.
1. 選取即時副本的存放位置。
1. 輸入 **標題** 和 **名稱** 在 **建立即時副本** 頁面。

1. 按一下 **開啟** 若要檢視新即時副本的內容，或 **完成** 以返回首頁面。

或者，您也可以參閱下列步驟，瞭解建立新頻道即時副本的視覺化呈現。

以下範例說明如何建立即時副本(***IdleLiveCopy***)表示 ***閒置頻道*** 目的地資料夾為 ***頻道***.

![chlimage_1-2](assets/chlimage_1-2.gif)

## 檢視即時副本管道的內容 {#viewing-content-of-the-live-copy-channel}

即時副本是已存在頻道的副本。

若要檢視即時副本的內容，請參閱下列步驟：

1. 導覽至Screens專案，然後按一下您最初建立即時副本的位置，如上節所示。 (在此，選擇位置為 **頻道** 資料夾)

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. 按一下 **編輯** 以檢視頻道中的內容。

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >檢視即時副本管道的內容時，您將在功能表中檢視額外專案為 **即時副本狀態**. 如需更多詳細資訊，請參閱以下章節。

### 檢視即時副本的屬性 {#viewing-properties-of-a-live-copy}

此外，您也可以檢視即時副本頻道的屬性。

1. 導覽至您的即時副本頻道，然後按一下 **屬性** 動作列中的。

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. 選取 **即時副本** 標籤以檢視您頻道的詳細資訊。

   ![chlimage_1-21](assets/chlimage_1-21.png)

### Live Copy 状态 {#live-copy-status}

模式 **即時副本狀態**&#x200B;如下圖所示，可讓您檢視管道中所有資產的關係狀態。

1. 按一下 **編輯** 以選擇 **即時副本狀態** 和檢視您的頻道內容與原始頻道（產生即時副本的來源）的關聯。

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. 選取 **即時副本狀態** 以顯示預覽頁面。

   所有具有綠色邊框的資源會顯示內容繼承自原始通道。

   ![chlimage_1-23](assets/chlimage_1-23.png)

### 中斷繼承 {#breaking-the-inheritance}

您也可以取消從LiveCopy的繼承，使內容獨立於原始分支。

下列範例顯示您在編輯模式中選取影像，然後按一下右上方的取消繼承符號。

![chlimage_1-24](assets/chlimage_1-24.png)

### 將變更傳播至即時副本頻道 {#propagating-changes-to-the-live-copy-channel}

如果您在原始頻道中進行變更/更新，您也需要將這些變更傳播到您的即時副本頻道。

請依照下列步驟操作，以確保您的變更從原始頻道傳播到即時副本頻道：

1. 選取原始頻道(***閒置頻道***)並按一下 **編輯** 動作列中的。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 對此管道內容進行編輯。 例如，從此頻道中刪除影像。

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. 選取頻道的即時副本(***IdleLiveCopy***)並按一下 **編輯** 動作列中的。 您會發現刪除的影像仍會顯示在即時副本中。

   為了傳播變更，您需要同步管道。

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. 若要將變更傳播至即時副本頻道，請導覽至AEM控制面板並選取即時副本頻道，然後按一下 **屬性** 動作列中的。

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. 選取 **即時副本** 標籤並按一下 **同步** 動作列中的。

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. 按一下 **同步** 以確認變更。 按一下 **儲存並關閉** 導覽回AEM控制面板。

   ![chlimage_1-30](assets/chlimage_1-30.png)

   您會發現影像現在也已從即時副本頻道中刪除。
