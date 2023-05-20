---
title: 緊急通道
seo-title: Emergency Channel
description: 依照此使用案例範例瞭解如何建立和管理緊急頻道，內容作者可在有先決條件的情況下從序列頻道切換。
seo-description: Follow this use case example to learn about creating and managing an emergency channel that the content author can switch from a sequence channel in case of a precondition.
uuid: 612917c9-a832-453b-970c-f4365f7b105d
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: dbb4fae6-f3fb-496a-9bd6-1151e2862b5b
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 1%

---

# 緊急通道 {#emergency-channel}

## 使用案例說明 {#use-case-description}

本節說明一個使用案例範例，著重於建立和管理緊急通道，內容作者可以在有先決條件的情況下從順序通道切換。

### 先決條件 {#preconditions}

在開始此使用案例之前，請確定您瞭解如何：

* **[建立和管理頻道](managing-channels.md)**
* **[建立和管理位置](managing-locations.md)**
* **[建立和管理時程表](managing-schedules.md)**
* **[设备注册](device-registration.md)**

### 主要執行者 {#primary-actors}

内容作者

## 基本流程：設定專案 {#basic-flow-setting-up-the-project}

請依照下列步驟設定緊急通道：

1. 建立名為的AEM Screens專案 **緊急通道**，如下所示。

   >[!NOTE]
   >若要進一步瞭解如何在AEM Screens中建立和管理專案，請參閱建立專案。

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **建立順序頻道**

   1. 選取 **頻道** 資料夾並按一下 **建立** 以開啟精靈來建立頻道。

   1. 選取 **序列頻道** 並從精靈建立標題為 **MainAdChannel**.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **新增內容至序列頻道**

   1. 選取頻道(**MainAdChannel**)。
   1. 按一下 **編輯** 以開啟編輯器。 將幾個資產拖放至您的頻道。

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **建立緊急通道**

   1. 選取 **頻道** 資料夾。
   1. 按一下 **建立** 以開啟精靈來建立頻道。
   1. 選取 **序列頻道** 並從精靈建立標題為 **緊急通道**.

   >[!NOTE]
   >
   >一般而言，您的緊急通道會新增至您既有的生產專案。

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **新增內容至緊急頻道**

   1. 選取頻道(**緊急通道)**.
   1. 按一下 **編輯** 以開啟編輯器。 將您要在緊急情況下執行的資產拖放到您的頻道。

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **建立位置**

   1. 導覽至 **位置** 資料夾。
   1. 按一下 **建立** 並從動作列建立標題為 **儲存** 從精靈中。

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **在您的位置中建立顯示區**

   導覽至您的位置(**儲存**)並按一下 **建立** 動作列中的。 按照精靈建立兩個 **顯示區** 標題為 **StoreFront** 和 **StoreRear**.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **建立排程**

   1. 導覽至 **時程表** 資料夾。
   1. 按一下 **建立** 動作列中的。 依照精靈建立標題為的排程 **StoreSchedule**.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. 將兩個顯示指定給排程並設定優先順序

   1. 選取排程 **(StoreSchedule)** 並按一下 **儀表板** 動作列中的。

   1. 按一下 **+指派管道** 從 **已指派的頻道** 面板。

   1. 從 **頻道指定任務** 對話方塊：

      1. 選取的路徑 **MainAdChannel**
      1. 設定 **優先順序** as 2
      1. 將支援的事件設為 **初始載入** 和 **閒置畫面**.
      1. 按一下 **儲存**

      同樣地，您必須再次執行相同的步驟才能指派 **緊急通道** 並設定其 **優先順序**.
   >[!NOTE]
   >
   >「優先順序」可用來對指派進行排序，以防多個指派符合播放條件。 值最高的總是優先於較低的值。

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. 按一下 **+指派管道** 從 **已指派的頻道** 面板。

1. 從 **頻道指定任務** 對話方塊：

   1. 選取的路徑 **緊急通道**
   1. 設定 **優先順序** as 1

   1. 將支援的事件設為 **初始載入**， **閒置畫面**、和 **使用者互動**

   1. 按一下 **儲存**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   您可以從以下位置檢視指派的頻道： **StoreSchedule** 儀表板。

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **指派排程給每個顯示器**

   1. 導覽至每個顯示區，例如 **緊急通道** —> **位置** —> **儲存** —>**StoreFront**.

   1. 按一下 **儀表板** 以開啟顯示控制面板。
   1. 按一下 **...** 從 **已指派的管道和排程** 面板，然後按一下 **+指派排程**.

   1. 選取排程的路徑(例如，此處， **緊急通道** —> **時程表** —>**StoreSchedule**)。

   1. 单击“**保存**”。

   您可以從以下位置檢視指派給顯示的排程： **StoreSchedule** 儀表板。
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **设备注册**

   完成裝置註冊程式，註冊後即可在您的AEM Screens播放器上檢視下列輸出。

   ![new30](assets/new30.gif)

## 切換到緊急頻道 {#switching-to-emergency-channel}

發生緊急狀況時，請執行以下步驟：

1. 導覽至 **緊急通道** —> **時程表** —> **StoreSchedule** 並選取 **儀表板** 動作列中的。

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. 選取 **緊急通道** 從 **StoreSchedule** 儀表板並按一下 **編輯指派**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. 更新 **優先順序** 的 **緊急通道** 至 **3** 從 **頻道指定任務** 對話方塊並按一下 **儲存**.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. 管道的優先順序一更新，所有AEM Screens播放器就會顯示 **緊急通道** 內容，如下所示。

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### 結論 {#conclusion}

此 **緊急通道** 將繼續顯示其內容，直到內容作者將優先順序值重設為1。

一旦內容作者收到緊急狀態已清除的指示，他/她應更新以下專案的優先順序： **MainAdChannel** 將會導致正常播放繼續。
