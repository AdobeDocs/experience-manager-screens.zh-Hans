---
title: 文本覆盖
seo-title: Text Overlay
description: 文字覆蓋是AEM Screens中提供的功能，可讓您透過在影像上方提供標題或說明，在序列頻道中建立引人入勝的體驗。 請詳閱本頁以瞭解更多資訊。
seo-description: Text Overlay is a feature available in AEM Screens that allows you to create a compelling experience in a Sequence Channel by providing a title or a description overlaid on top of an image. Follow this page to learn more.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 2%

---

# 文本覆盖 {#text-overlay}

本節涵蓋下列主題：

* **概述**
* **使用文字覆蓋**
* **瞭解文字覆蓋屬性**
* **在文字覆蓋中使用ContextHub值**

>[!CAUTION]
>
>此 **文字覆蓋** 功能僅在您已安裝AEM 6.3 Feature Pack 5或AEM 6.4 Feature Pack 3時可用。

## 概述 {#overview}

文字覆蓋是AEM Screens中提供的功能，可讓您透過在影像上方提供標題或說明，在序列頻道中建立引人入勝的體驗。

若要瞭解如何建立自己的自訂元件，請參閱 **延伸AEM Screens元件**.

本節僅展示如何在AEM Screens專案中使用和套用海報元件，以及如何將其用作其中一個序列管道中的文字覆蓋。

## 使用文字覆蓋 {#using-text-overlay}

下節將說明如何在AEM Screens專案中使用文字覆蓋。

**前提条件**

開始實作此功能之前，請確定您已設定專案作為開始實作文字覆蓋的先決條件。 例如，

* 建立AEM Screens專案(在此範例中， **TextOverlayDemo**)

* 建立標題為的順序頻道 **文字範例** 在 **頻道** 資料夾

* 將內容新增至 **文字範例** 頻道

下圖顯示 **TextOverlayDemo** 專案與 **文字範例** 中的頻道 **頻道** 資料夾。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

請依照下列步驟，在AEM Screens頻道中使用文字覆蓋：

1. 導覽至 **TextOverlayDemo** —> **頻道** —> **文字範例** 並按一下 **編輯** 以開啟編輯器。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 選取影像並按一下 **設定** （扳手圖示）以開啟「屬性」對話方塊。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 選取 **文字覆蓋** 選項，如下圖所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 瞭解文字覆蓋屬性 {#understanding-text-overlay-properties}

您可以使用「文字覆蓋」屬性，將文字新增至畫面專案中的任何元件。 下節提供文字覆蓋中可用屬性的概觀：

![文本](assets/text.gif)

您可以將文字新增至文字方塊，並新增印刷強調文字，例如粗體、斜體和底線。

**顏色變體** 此選項允許文字為深色（黑色文字）或淺色（白色文字）。

**大小調整與定位** 此選項可讓使用者水平或垂直對齊文字，或是使用微調工具對齊文字。

>[!NOTE]
>
>若要正確使用微調工具，請務必以(px)做為尾碼（例如200畫素）來識別正確的畫素位置。 此運算式的結果是從起點算起200畫素。

## 在文字覆蓋中使用ContextHub值 {#using-text-overlay-context-hub}

下節說明資料存放區中值的使用方式，例如，文字覆蓋元件中的google sheets 。

**前提条件**

為您的AEM Screens專案設定ContextHub設定。

若要瞭解如何使用資料存放區來設定和管理資料導向資產變更，請參閱 [在AEM Screens中設定ContextHub](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

設定專案所需的設定後，請依照下列步驟使用Google工作表中的值：

1. 導覽至 **TextOverlayDemo** —> **頻道** —> **文字範例** 並按一下 **屬性** 動作列中的。

1. 選取 **個人化** 索引標籤以設定ContextHub設定。

   1. 選取 **ContextHub路徑** 作為 **程式庫** > **設定** > **雲端設定** > **預設** > **ContextHub設定** 並按一下 **選取**.

   1. 選取 **區段路徑** 作為 **conf** > **畫面** > **設定** > **wcm** > **區段** 並按一下 **選取**.

   1. 单击“**保存并关闭**”。

      >[!NOTE]
      >
      >使用ContextHub和區段路徑，您最初儲存您的Context Hub設定和區段。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 導覽至 **TextOverlayDemo** —> **頻道** —> **文字範例** 並按一下 **編輯** 以開啟編輯器。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 將影像和文字覆蓋元件新增至您的影像，如所述 [使用文字覆蓋](/help/user-guide/text-overlay.md#using-text-overlay) 區段。

1. 按一下 **設定** （扳手圖示）開啟 **影像** 對話方塊。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 導覽至 **ContextHub** 標籤從 **影像** 對話方塊。 按一下 **新增**.

   >[!NOTE]
   >如果您尚未設定ContextHub設定，專案的此選項會停用。

1. 輸入 **值** 在 **預留位置** 欄位。 選取您要從Google工作表取得值的資料列 **contexthub變數**. 在此情況下，值會從Google工作表中從列2和欄1擷取。 現在輸入 **預設值** 作為 **20**，如下圖所示。 完成後，按一下核取記號。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >下列影像會示範從Google工作表擷取的值，以供您參考：

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 導覽回至 **文字覆蓋** 標籤並新增文字 *目前溫度{Value}*，如下圖所示。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 按一下 **預覽** 以檢視所需的輸出。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
