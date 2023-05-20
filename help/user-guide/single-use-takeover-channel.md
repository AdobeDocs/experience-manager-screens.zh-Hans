---
title: 單次使用接管管道
seo-title: Single Use TakeOver Channel
description: 請依照此使用案例來建立單一「使用接管管道」。
seo-description: Follow this Use Case for creating a Single Use TakeOver Channel.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3317f07a-784f-4c4a-93ea-c84f4e42e9f2
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 2%

---

# 單次使用接管管道 {#single-use-takeover-channel}

以下頁面會展示使用案例，著重於設定專案，說明如何建立只在特定時間播放一次的Single TakeOver頻道。


## 使用案例說明 {#use-case-description}

此使用案例說明如何建立符合以下條件的管道： *接管* 來自顯示器或顯示器群組的正常播放頻道。 接管只會發生一次，並持續一段特定時間。
例如，有一個Single TakeOver頻道，在星期五上午9點至上午10點播放。 在此期間，不應播放其他頻道。 在這段時間之前和之後，將不播放單次使用接管頻道。 以下範例說明如何建立單一接管管道，並播放該管道，讓內容在12月31日凌晨12:00前播放達2分鐘，直到中午12:01。

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

1. 建立標題為的AEM Screens專案 **SingleUseTover**，如下所示。

   ![资产](assets/single-takeover1.png)

1. 建立 **MainAdChannel** 在 **頻道** 資料夾。

   ![资产](assets/single-takeover2.png)

1. 選取 **MainAdChannel** 並按一下 **編輯** 動作列中的。 將部分資產（影像、影片、內嵌序列）拖放至您的頻道。

   ![资产](assets/single-takeover2.png)


   >[!NOTE]
   >此 **MainAdChannel** 在此範例中，會示範持續播放內容的順序頻道。

   ![资产](assets/single-takeover3.png)

1. 建立 **接管** 接收內容的頻道 **MainAdChannel** 和只會播放特定日期和時間。

1. 選取 **接管** 並按一下 **編輯** 動作列中的。 將部分資產拖放至您的頻道。 下列範例示範新增至此頻道的單一區域影像。

   ![资产](assets/single-takeover4.png)

1. 設定管道的位置和顯示。 例如，下列位置 **大廳** 和顯示 **MainLobbyDisplay** 已針對此專案設定。

   ![资产](assets/single-takeover5.png)

**將頻道指派給顯示區**

1. 選取顯示區 **MainLobbyDisplay** 從 **位置** 資料夾。 按一下 **指派頻道** 動作列中的。

   ![资产](assets/single-takeover6.png)

   >[!NOTE]
   >若要瞭解如何將管道指派給顯示區，請參閱 **[頻道指定任務](channel-assignment.md)**.

1. 填入欄位(**頻道路徑**， **優先順序**、和 **支援的事件**)從 **頻道指定任務** 對話方塊並按一下 **儲存**. 您現在已指派 **MainAdChannel** 至您的顯示區。

   ![资产](assets/single-takeover7.png)

1. 選取顯示區 **接管** 從 **位置** 資料夾。 按一下 **指派頻道** 從動作列指派單次使用接管管道。

1. 若要指派 **接管** 在排程的時間進入您的顯示區，並填入以下欄位： **頻道指定任務** 對話方塊並按一下 **儲存**：

   * **頻道路徑**：選取接管管道的路徑
   * **優先順序**：將此頻道的優先順序設定大於 **MainAdChannel**. 例如，在此範例中設定的優先順序為8。

      >[!NOTE]
      >優先順序可以是高於正常播放頻道之優先順序值的任何值。
   * **支援的事件**：選取 **閒置畫面** 和 **計時器**.
   * **排程**：輸入您希望此頻道執行顯示的排程文字。 例如，此處的文字可讓內容在12月31日凌晨12:00前的2分鐘播放至凌晨12:01。
此文字位於 **排程** 此範例中提及的是 *23:58之後的12月31日，以及00.01之前的1月1日*.

      ![资产](assets/single-takeover8.png)

      瀏覽至顯示區，從 **SingleUseTover** —> **位置** —> **大廳** —> **MainLobbyDisplay** 並按一下 **儀表板** 從動作列檢視指派的管道及其優先順序，如下所示。

      >[!NOTE]
      >強制將接管管道的優先順序設定為最高。

      ![资产](assets/single-takeover9.png)

>[!NOTE]
>
>最佳實務是在播放後刪除「單次使用TakeOver」管道。
