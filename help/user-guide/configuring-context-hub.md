---
title: 在AEM Screens中設定ContextHub
seo-title: Configuring ContextHub in AEM Screens
description: 請詳閱本頁，瞭解鎖定目標引擎中的ContextHub，以定義資料存放區，方便資料觸發內容變更。
seo-description: Follow this page to learn about ContextHub in the targeting engine to define data store for the purpose of data trigger content change.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 2%

---

# 在AEM Screens中設定ContextHub {#configuring-contexthub-in-aem-screens}

本節著重於使用資料存放區建立和管理資料導向資產變更。

## 重要條款 {#key-terms}

在我們開始瞭解在您的AEM Screens專案中建立和管理庫存導向管道的詳細資訊之前，您必須瞭解幾個重要的關鍵術語，這些術語與不同的情境相關。

**品牌** 請參閱您的高階專案說明。

**區域** 是指您的AEM Screens專案名稱，例如數位廣告招牌

**活動** 定義規則類別，例如庫存導向、天氣導向、部門可用性導向等。

**對象** 定義規則。

**區段** 參照要依指定規則播放的資產版本，例如如果溫度低於華氏50度，則畫面會顯示熱咖啡的影像，否則會顯示冷飲。

下圖以視覺化方式呈現ContextHub設定與活動、受眾和管道的一致性。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 先決條件 {#preconditions}

開始為AEM Screens專案設定Context Hub設定之前，您必須設定Google工作表（用於示範用途）。

>[!IMPORTANT]
>
>在下列範例中，Google Sheets會作為範例資料庫系統使用，其值會從中擷取，且僅供教育用途。 Adobe不認可將Google Sheets用於生產環境。
>
>如需詳細資訊，請參閱 [取得API金鑰](https://developers.google.com/maps/documentation/javascript/get-api-key) 在Google檔案中。

## 步驟1：設定資料存放區 {#step-setting-up-a-data-store}

您可以將資料存放區設定為本機I/O事件或本機資料庫事件。

下列資產層級資料觸發器範例會示範本機資料庫事件，此事件會設定資料存放區（例如Excel工作表），讓您使用ContextHub設定和AEM Screens通道的區段路徑。

正確設定Google工作表後（例如），如下所示：

![图像](/help/user-guide/assets/context-hub/context-hub1.png)

當您輸入兩個值來檢查連線時，將會檢視以下驗證。 *google工作表ID* 和 *API金鑰* 格式如下：

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![图像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>以下特定範例會展示Google工作表作為資料存放區，如果值高於100或小於50，則會觸發資產變更。

## 步驟2：設定存放區設定 {#step-setting-store-configurations}

1. **瀏覽至ContextHub**

   導覽至您的AEM執行個體，然後按一下左側邊欄中的工具圖示。 按一下 **網站** —> **ContextHub**，如下圖所示。

   ![图像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **建立新的ContextHub存放區設定**

   1. 導覽至標題為的設定容器 **畫面**.

   1. 按一下 **建立** > **建立設定容器** 並輸入標題為 **ContextHubDemo**.

      ![图像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **導覽** 至 **ContextHubDemo** > **建立** **ContentHub設定** 並按一下 **儲存**.

      >[!NOTE]
      > 在您按一下 **儲存** 您將位於 **ContextHub設定** 畫面。

   1. 從 **ContextHub設定** 熒幕，按一下 **建立** > **ContentHub存放區設定……**

      ![图像](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >在AEM 6.5 Feature Pack 4或AEM 6.4 Feature Pack 8中，客戶應更新 `/conf/screens/settings/cloudsettings` 至 `sling:Folder`.
      >
      >应遵循以下步骤：
      >
      >1. 導覽至「CRXDE Lite」，然後導覽至 `/conf/screens/settings/cloudsettings`.
      >1. 檢查 `cloudsettings jcr:primaryType` 位於 `sling:Folder`. 如果 `jcr:primaryType` 不在 `sling:folder`，請繼續進行後續步驟。
      >1. 按一下右鍵 `/conf/screens/settings` 和建立新節點，使用 *名稱*  作為 **cloudsettings1** 和 *型別* 作為 **sling：Folder** 並儲存變更。
      >1. 將所有的節點移到 `/conf/screens/settings/cloudsettings` 至 `cloudsettings1`.
      >1. 刪除 `cloudsettings` 並儲存。
      >1. 重新命名 `cloudsettings1` 至 `cloudsettings` 並儲存。
      >1. 您現在應該注意到/conf/screens/settings/cloudsettings具有 `jcr:primaryType` 作為 `sling:Folder`.

      >
      >升級之前或之後，您應該依照這些步驟在author和publish中進行。

   1. 輸入 **標題** 作為 **Google工作表**， **存放區名稱** 作為 **Google工作表**、和 **存放區型別** 作為 **contexthub.generic-jsonp** 並按一下 **下一個**.

      >[!CAUTION]
      >如果您使用Adobe Experience Manager (AEM) 6.4，請輸入 **設定標題** 作為 **Google工作表** 和 **存放區型別** 作為 **contexthub.generic-jsonp**.

      ![图像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 輸入您特定的json設定。 例如，您可以將以下json用於示範目的，然後按一下 **儲存** 而且您會看到商店設定的標題為 **Google工作表** 在ContextHub設定中。

      >[!IMPORTANT]
      >請務必將程式碼取代為 *&lt;sheet id=&quot;&quot;>* 和 *&lt;api key=&quot;&quot;>*，即您在設定Google工作表時擷取的內容。

      ```
       {
        "service": {
        "host": "sheets.googleapis.com",
        "port": 80,
        "path": "/v4/spreadsheets/<your google sheets id>/values/Sheet1",
        "jsonp": false,
        "secure": true,
        "params": {
        "key": "<your Google API key>"
       }
      },
      "pollInterval": 10000
      }
      ```

      >[!NOTE]
      在上述範常式式碼中， **pollInterval** 會定義重新整理值的頻率（以毫秒為單位）。
      將程式碼取代為 *&lt;sheet id=&quot;&quot;>* 和 *&lt;api key=&quot;&quot;>*，即您在設定Google工作表時擷取的內容。

      >[!CAUTION]
      如果您在全域資料夾之外（例如，在您自己的專案資料夾中）建立Google Sheets存放區設定，則無法立即使用目標定位。

1. **設定商店分段**

   1. 導覽至 **ContentHub存放區設定……** 並在screens設定容器中建立另一個商店設定，並將 **標題** 作為 **segmentation-contexthub**， **存放區名稱** 作為 **細分** 和 **存放區型別** 作為 **aem.segmentation**.

      ![图像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. 按一下 **下一個** 然後 **儲存**.

      >[!NOTE]
您必須跳過定義JSON的程式，並保留空白。


## 步驟3：在對象中設定區段 {#setting-up-audience}

1. **在受眾中建立區段**

   1. 從您的AEM執行個體瀏覽至 **個人化** > **受眾** > **畫面**.

   1. 按一下 **建立** > **建立內容中心區段。** 此 **新增ContextHub區段** 對話方塊開啟。

   1. 輸入 **標題** 作為 **Higherthan50** 並按一下 **建立**. 同樣地，建立另一個區段，標題為 **Lowerthan50**.

      ![图像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 選取區段 **Higherthan50** 並按一下 **屬性** 動作列中的。
      ![图像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. 選取 **個人化** 標籤從 **區段屬性**. 設定 **ContextHub路徑** 至 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` 和 **區段路徑** 至 `/conf/screens/settings/wcm/segments` 並按一下 **儲存**，如下圖所示。

      ![图像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同樣地，設定 **ContextHub路徑** 和 **區段路徑** 的 **Lowerthan50** 區段也是。

## 步驟4：設定品牌和區域 {#setting-brand-area}

請依照下列步驟，在您的活動與品牌下的區域建立品牌：

1. **在活動中建立品牌**

   1. 從您的AEM執行個體瀏覽至 **個人化** > **活動**.

   1. 按一下 **建立** > **建立品牌**.

   1. 選取 **品牌** 從 **建立頁面** 精靈並按一下 **下一個**.

   1. 輸入 **標題** 作為 **ScreensBrand** 並按一下 **建立**. 您的品牌現已建立，如下所示。

      ![图像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      已知問題：若要新增區域，請從URL移除主版，例如
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`。

1. **在您的品牌中建立區域**

   請依照下列步驟，在品牌中建立區域：

   1. 按一下 **建立** 然後 **建立區域**.

      ![图像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. 選取 **區域** 從 **建立頁面** 精靈並按一下 **下一個**.

   1. 輸入 **標題** 作為 **ScreensValue** 並按一下 **建立**.
將會在您的品牌中建立一個區域。

## 步驟5：在活動中建立區段 {#step-setting-up-audience-segmentation}

設定資料存放區並定義活動（品牌和區域）後，請依照下列步驟在活動中建立區段。

1. **在活動中建立區段**

   1. 從您的AEM執行個體瀏覽至 **個人化** > **活動** > **ScreensBrand** >**ScreensValue**.

   1. 按一下 **建立** > **建立活動。** 此 **設定活動精靈** 隨即開啟。

   1. 輸入 **標題** 作為 **ValueCheck50** 和 **名稱** 作為 **valuecheck50**. 選取 **目標定位引擎** 作為 **ContextHub (AEM)** 從下拉式清單，然後按一下 **下一個**.

      ![图像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 按一下 **新增體驗** 從 **設定活動精靈**.

   1. 從 **受眾**，選取 **Higherthan50** 並按一下 **新增體驗** 並輸入 **標題** 作為 **higherthan50** **名稱** 作為 **higherthan50**. 按一下 **確定**.

   1. 從 **受眾**，選取 **Lowerthan50** 並按一下 **新增體驗** 並輸入 **標題** 作為 **lowerthan50** **名稱** 作為 **lowerthan50**. 按一下 **確定**.

      ![图像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. 按一下 **下一個** 然後 **儲存**. **ValueCheck50** 活動現在已建立並設定。

      ![图像](/help/user-guide/assets/context-hub/context-hub16.png)

## 步驟5：編輯受眾中的區段{#editing-audience-segmentation}

1. **編輯區段**

   1. 從您的AEM執行個體瀏覽至 **個人化** > **受眾** > **畫面**.

   1. 選取區段 **Higherthan50**，然後按一下 **編輯** 動作列中的。

   1. 拖放 **比較：屬性 — 值** 元件至編輯器。

   1. 按一下扳手圖示以開啟 **比較屬性與值** 對話方塊。

   1. 選取 **Googlesheets/value/1/0** 從的下拉式清單 **屬性名稱**.

      >[!NOTE]
此 **Googlesheets/value/1/0** 參考下圖中填入google工作表中的第2列和欄：

      ![图像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 選取 **運運算元** 作為 **大於** 從下拉式功能表。

   1. 輸入 **值** 作為 **70**.

      >[!NOTE]
      AEM會將您的區段顯示為綠色，以驗證Google工作表中的資料。

      ![图像](/help/user-guide/assets/context-hub/context-hub18.png)
   同樣地，將屬性值編輯為 **Lowerthan50**.

   1. 拖放 **比較：屬性 — 值** 元件至編輯器。

   1. 按一下扳手圖示以開啟 **比較屬性與值** 對話方塊。

   1. 選取 **Googlesheets/value/1/0** 從的下拉式清單 **屬性名稱**.

   1. 選取 **運運算元** 作為 **小於** 從下拉式功能表。

   1. 輸入 **值** 作為 **50**.



## 在管道中啟用鎖定目標 {#step-enabling-targeting-in-channels}

請依照下列步驟，在您的管道中啟用目標定位。

1. 導覽至其中一個AEM Screens頻道。 下列步驟示範如何使用啟用鎖定目標 **DataDrivenChannel** 在AEM Screens頻道中建立。

1. 選取頻道 **TargetChannel** 並按一下 **屬性** 動作列中的。

   ![图像](/help/user-guide/assets/context-hub/context-hub19.png)

1. 選取 **個人化** 索引標籤以設定ContextHub設定。

   1. 設定 **ContextHub路徑** 至 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` 和 **區段路徑** 至 `/conf/screens/settings/wcm/segments` 並按一下 **儲存**.

   1. 单击“**保存并关闭**”。

      >[!NOTE]
      使用ContextHub和區段路徑，您最初儲存您的Context Hub設定和區段。

      ![图像](/help/user-guide/assets/context-hub/context-hub20.png)

   1. 瀏覽並選取 **TargetChannel** 頻道與點按 **編輯** 動作列中的。

      >[!NOTE]
      如果您已正確設定所有內容，您將會看到 **目標定位** 選項下拉式清單中的下拉式清單，如下圖所示。

      ![图像](/help/user-guide/assets/context-hub/context-hub21.png)

## 深入瞭解：範例使用案例 {#learn-more-example-use-cases}

為AEM Screens專案設定ContextHub後，您可以依照不同的使用案例來瞭解資料觸發的資產如何在不同的產業中扮演重要角色：

1. **[零售詳細目錄目標啟動](retail-inventory-activation.md)**
1. **[旅行中心溫度啟用](local-temperature-activation.md)**
1. **[Hospality Reservation Activation](hospitality-reservation-activation.md)**
