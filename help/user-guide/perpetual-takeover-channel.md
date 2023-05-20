---
title: 永久接管管道
seo-title: Perpetual TakeOver Channel
description: 請依照此使用案例建立永久接管管道。
seo-description: Follow this Use Case on setting up a project that creates a Perpetual TakeOver channel that plays for a specific time day and time continuously.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 5d112f33-a7cf-415e-9ea7-dc18a0356a8d
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 1%

---

# 永久接管管道 {#perpetual-takeover-channel}

以下頁面將展示一個使用案例，著重於設定專案，說明如何建立持續在特定日子和時間播放的永久TakeOver管道。

## 使用案例說明 {#use-case-description}

此使用案例說明如何建立符合以下條件的管道： *接管* 來自顯示器或顯示器群組的正常播放頻道。 接管將持續在特定日期和時間發生。
例如，有一個永續接管頻道，每個星期五上午9點至上午10點播放。 在此期間，不應播放其他頻道。 以下範例說明如何建立永續接管頻道，讓內容在每週三的2:00 pm到4:00 pm播放2小時。

### 先決條件 {#preconditions}

在開始此使用案例之前，請確定您瞭解如何：

* **[建立和管理頻道](managing-channels.md)**
* **[建立和管理位置](managing-locations.md)**
* **[建立和管理時程表](managing-schedules.md)**
* **[设备注册](device-registration.md)**

### 主要執行者 {#primary-actors}

内容作者

## 设置项目 {#setting-up-the-project}

請依照下列步驟設定專案：

**設定頻道和顯示**

1. 建立標題為的AEM Screens專案 **PerpetualTakeOver**，如下所示。

   ![资产](assets/p_usecase1.png)

1. 建立 **MainAdChannel** 在 **頻道** 資料夾。

   ![资产](assets/p_usecase2.png)

1. 選取 **MainAdChannel** 並按一下 **編輯** 動作列中的。 將部分資產（影像、影片、內嵌序列）拖放至您的頻道。

   ![资产](assets/p_usecase3.png)


   >[!NOTE]
   >此 **MainAdChannel** 在此範例中，會示範持續播放內容的順序頻道。

1. 建立 **接管** 接收內容的頻道 **MainAdChannel** 並將在每週三下午2:00至4:00之間播放。

1. 選取 **接管** 並按一下 **編輯** 動作列中的。 將部分資產拖放至您的頻道。 下列範例示範新增至此頻道的單一區域影像。

   ![资产](assets/p_usecase4.png)

1. 設定管道的位置和顯示。 例如，下列位置 **MainLobby** 和顯示 **MainLobbyDisplay** 已針對此專案設定。

   ![资产](assets/p_usecase5.png)

**將頻道指派給顯示區**

1. 選取顯示區 **MainLobbyDisplay** 從 **位置** 資料夾。 按一下 **指派頻道** 從動作列開啟 **頻道指定任務** 對話方塊。

   >[!NOTE]
   >若要瞭解如何將管道指派給顯示區，請參閱 **[頻道指定任務](channel-assignment.md)**.

1. 填入欄位(**頻道路徑**， **優先順序**、和 **支援的事件**)從 **頻道指定任務** 對話方塊並按一下 **儲存** 以指派 **MainAdChannel** 至您的顯示區。

   * **頻道路徑**：選取的路徑 **MainAdChannel** 頻道
   * **優先順序**：將此頻道的優先順序設為1。
   * **支援的事件**：選取 **初始載入** 和 **閒置畫面**.

   ![资产](assets/p_usecase6.png)

1. 選取顯示區 **接管** 從 **位置** 資料夾。 按一下 **指派頻道** 以指派接管管道。

1. 若要指派 **接管** 在排程的時間進入您的顯示區，並填入以下欄位： **頻道指定任務** 對話方塊並按一下 **儲存**：

   * **頻道路徑**：選取的路徑 **接管** 頻道
   * **優先順序**：將此頻道的優先順序設定大於 **MainAdChannel**. 例如，在此範例中設定的優先順序為8。
   * **支援的事件**：選取 **閒置畫面** 和 **計時器**.
   * **排程**：輸入您希望此頻道執行顯示的排程文字。 此文字位於 **排程** 此範例中提及的是 *星期三14:00後到16:00之前*.

      >[!NOTE]
      >若要進一步瞭解可新增至的運算式 **排程**，請參閱 [範例運算式](#example-expressions) 區段底下。
   * **啟用開始日期**：開始日期和時間。
   * **啟用結束日期**：結束日期和時間。

      例如，文字位於 **排程** 和 **啟用開始日期** 和 **啟用結束日期** 此處的日期和時間可讓內容從每週三下午2:00播放到下午4:00。


      ![资产](assets/p_usecase7.png)

      瀏覽至顯示區，從 **接管** —> **位置** —> **MainLobby** —> **MainLobbyDisplay** 並按一下 **儀表板** 從動作列檢視指派的管道及其優先順序，如下所示。

      >[!NOTE]
      >強制將接管管道的優先順序設定為最高。

      ![資產](assets/p_usecase8.png)
現在， **接管** 頻道將接管 **MainAdChannel** 每週三下午2:00播放兩個小時至下午4:00，並從2020年1月9日到2020年1月31日播放其內容。

## 範例運算式 {#example-expressions}

下表總結列出一些範例運算式，您可以在指派管道給顯示區時將其新增到排程。

| **表达式** | **解譯** |
|---|---|
| 上午8:00之前 | 此頻道每天上午8:00之前播放 |
| 下午2:00以後 | 頻道每天下午2:00後播放 |
| 12:15之後及12:45之前 | 該頻道每天下午12:15後播放30分鐘 |
| 12:15之前以及12:45之後 | 該頻道每天下午12:15之前播放，之後又在下午12:45之後播放 |
| 1月1日下午2:00後亦即1月2日凌晨3:00前，亦即1月3日 | 頻道在1月1日下午2:00之後開始播放，並持續播放1月2日的一整天，直到1月3日凌晨3:00 |
| 1月1-2日下午2:00後亦即1月2-3日凌晨3:00前 | 頻道在1月1日下午2:00之後開始播放程式，繼續播放至1月2日凌晨3:00，然後於1月2日下午2:00重新開始並繼續播放至1月3日凌晨3:00 |

>[!NOTE]
>
>您也可以使用 _軍事時間_ 表示法（亦即14:00），而非 *上午/下午* 表示法（亦即，下午2:00）。
