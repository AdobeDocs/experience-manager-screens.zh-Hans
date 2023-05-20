---
title: 多區域到單一區域轉換使用案例
description: 請依照本頁瞭解MultiZone to SingleZone Transitions使用案例。
seo-description: MultiZone to SingleZone Transitions use case.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 3%

---

# 多區域到單一區域轉換 {#multizone-to-singlezone-use-case}


## 使用案例說明 {#use-case-description}

本節說明使用案例範例，著重說明如何設定與單一區域版面配置管道交替的多區域版面配置管道。 多區域管道有排序影像/視訊資產，並顯示如何設定從多區域切換為單一區域（或反之）的專案。

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

1. 建立名為的AEM Screens專案 **TakeoverLoop**，如下所示。

   ![资产](assets/mz-to-sz1.png)


1. **建立多區域畫面頻道**

   1. 選取 **頻道** 資料夾並按一下 **建立** 從動作列開啟精靈以建立頻道。
   1. 選取 **左側L列拆分畫面頻道** 並從精靈建立標題為 **MultiZoneLayout**.
   1. 新增內容至頻道。 將資產拖放至每個區域。 下列範例顯示 **MultiZoneLayout** 由影片、影像和文字橫幅組成的頻道（以內嵌順序顯示），如下所示。

   ![资产](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >若要進一步瞭解如何在您的頻道中建立多區域版面配置，請參閱 [多區域配置](multi-zone-layout-aem-screens.md).


1. 建立另一個標題為的頻道 **TakeoverChannel** 至您的 **頻道** 資料夾。

   ![资产](assets/mz-to-sz3.png)

1. 按一下 **編輯** 以新增內容至此頻道。 新增 **頻道** 您要切換至此頻道的元件和影像資產，如下圖所示：

   ![资产](assets/mz-to-sz4.png)

1. 開啟Channel元件的設定，並將其指向 **MultiZoneLayout** 您在中建立的管道 *步驟2*.

   ![资产](assets/mz-to-sz5.png)

1. 設定持續時間，從 **序列** 欄位至 **10000毫秒**.

   ![资产](assets/mz-to-sz6.png)

1. 同樣地，請開啟影像（您新增的資產）的設定，並從以下專案設定其持續時間： **序列** 欄位至 **3000毫秒**.

   ![资产](assets/mz-to-sz7.png)

## 檢查預覽 {#checking-the-preview}

您可以從播放器檢視所需的輸出，或只要按一下 **預覽** 從編輯器中。

輸出將示範如何播放多區域配置 *10000毫秒* 然後切換至播放持續時間的單一區域版面 *3000毫秒* 然後切換回多區域配置。

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>您可以根據需求自訂管道轉變（從多區域到單區域配置，反之亦然）。
