---
title: 使用資料觸發器製作
seo-title: Authoring with Data Triggers
description: 請詳閱本頁面，瞭解如何使用資料觸發器進行創作。
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---

# 使用資料觸發器製作 {#authoring-with-data-triggers}

本節著重說明如何在您的管道中啟用目標定位。

>[!IMPORTANT]
>
>AEM Screens管道中支援資料觸發器的最低版本為AEM 6.5.3 Feature Pack 3。

## 前提条件 {#prereqs}

在依照下列步驟啟用管道中的目標定位之前，您必須瞭解 [在AEM Screens中設定的重要條款](configuring-context-hub.md) 瞭解AEM Screens中的ContextHub和鎖定目標所需。

>[!IMPORTANT]
>
>在AEM Screens頻道中啟用鎖定目標之前，建議您先瞭解並設定ContextHub設定。

如需詳細資訊，請前往下列連結：

1. **[設定資料存放區](configuring-context-hub.md)**
1. **[設定對象細分](configuring-context-hub.md)**

完成上述步驟後，您就可以在管道中啟用目標定位。

## 使用Data Triggers製作概述 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## 在AEM Screens頻道中啟用鎖定目標 {#enabling-targeting}

請依照下列步驟，在您的管道中啟用目標定位。

1. 導覽至其中一個AEM Screens頻道。 下列步驟示範如何使用啟用鎖定目標 **DataDrivenRetail** *（順序頻道）* 在AEM Screens頻道中建立。

1. 選取頻道 **DataDrivenRetail** 並按一下 **屬性** 動作列中的。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 選取 **個人化** 索引標籤以設定ContextHub設定，並選取ContextHub和區段路徑。

   1. 選取 **ContextHub路徑** 作為 **程式庫** > **設定** > **雲端設定** > **預設** > **ContextHub設定** 並按一下 **選取**.

   1. 選取 **區段路徑** 作為 **conf** > **We.Retail** > **設定** > **wcm** > **區段** 並按一下 **選取**.

   1. 单击“**保存并关闭**”。
   >[!NOTE]
   >
   >使用ContextHub和區段路徑，您最初儲存您的Context Hub設定和區段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. 瀏覽並選取 **DataDrivenRetail** 從 **DataDrivenAssets** > **頻道** 並按一下 **編輯** 動作列中的。 在管道編輯器中拖放資產。

   >[!NOTE]
   >
   >如果您已正確設定所有內容，您將會看到 **目標定位** 選項下拉式清單中的下拉式清單，如下圖所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. 按一下 **目標定位**.

1. 選取 **品牌** 和 **活動** 從下拉式功能表，然後按一下 **開始定位**.

### 深入瞭解：範例使用案例 {#learn-more-example-use-cases}

為AEM Screens專案設定ContextHub後，您可以依照不同的使用案例來瞭解資料觸發的資產如何在不同的產業中扮演重要角色：

1. **[零售詳細目錄目標啟動](retail-inventory-activation.md)**
1. **[旅行中心溫度啟用](local-temperature-activation.md)**
1. **[Hospality Reservation Activation](hospitality-reservation-activation.md)**
