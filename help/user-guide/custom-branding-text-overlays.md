---
title: 套用文字覆蓋圖的自訂品牌和樣式
seo-title: Applying Custom Branding and Styling for Text Overlays
description: 請詳閱本頁面，瞭解如何套用文字覆蓋圖的自訂品牌和樣式。
seo-description: Follow this page to learn how to apply custom branding and styling for Text Overlays.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 1%

---

# 文字覆蓋圖的自訂品牌和樣式 {#creating-custom-branding-styling}

請詳閱本頁面，瞭解如何在AEM Screens管道中，將自訂品牌和樣式套用至套用至資產的文字覆蓋圖。

## 建立文字覆蓋圖的自訂品牌和樣式 {#steps-custom-branding}

請依照下列步驟，為文字覆蓋圖建立自訂品牌和樣式：

1. 建立AEM Screens專案。 此範例透過建立名為的專案來展示功能 **customstyle** 和標題為的頻道 **DemoBrand** ，如下圖所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 從編輯器拖放影像並將文字覆蓋新增至資產。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >若要瞭解如何在管道編輯器中將文字覆蓋新增至您的資產，請參閱 [文字覆蓋](/help/user-guide/text-overlay.md).

1. 從您的AEM執行個體瀏覽到CRXDE Lite—>工具 — > **CRXDE Lite**.

1. 您必須在中建立自訂設計 `/apps/settings/wcm/designs/<your-project>/`例如，在本例中，請導覽至 `/apps/settings/wcm/designs/customstyle/`

   ![图像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. 建立 *static.css* 並設定下列css規則。 亦以css規則下圖的範例顯示。

   ```shell
    //global styles
    cq-Screens-textOverlay {
    padding: 1em;
    font-size: 3rem;
    line-height: 1em;
     }
    //authoring overrides
   .aem-AuthorLayer-Edit .cq-Screens-textOverlay {
    display: none;
    padding: 0;
    font-size: 1rem;
    }
     // light text variant
    .cq-Screens-textOverlay-color--light {
     background-color: rgba(0, 0, 0, .6);
     }
     // dark text variant
     .cq-Screens-textOverlay-color--dark {
      background-color: rgba(255, 255, 255, .6);
    }
   ```

   ![图像](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. 複製專案的路徑，在此案例中，路徑將為 `/apps/settings/wcm/designs/customstyle`.

1. 導覽至標題為「 」的頻道 **DemoBrand** (在步驟(1)中建立)，然後按一下 **屬性** 從動作列選取頻道後。

1. 導覽至 **進階** 標籤並核取 **設計** 欄位。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >根據預設， **設計** 欄位會顯示指向libs資料夾中設計的路徑。

1. 更新 **設計** 包含專案資料夾路徑的欄位。 在此情況下，將會是 `/apps/settings/wcm/designs/customstyle`.

   ![图像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 按一下 **儲存並關閉** 以更新設計路徑。

   >[!IMPORTANT]
   >您可以選擇覆蓋現有的Screens範本，依預設插入您自己的設計或完全建立您自己的範本。 如需更多詳細資訊，請參閱以下步驟。

1. 若要依預設覆蓋現有的Screens範本以插入您自己的設計：

   1. 覆蓋 `/libs/screens/core/templates/sequencechannel` 在 `/apps/screens/core/templates/sequencechannel`.
   1. 修改 *cq：designPath* 中的屬性 `/apps/screens/core/templates/sequencechannel/jcr:content` 指向新設計。

1. 完全建立您自己的範本：
   1. 複製 `/libs/screens/core/templates/sequencechannel` 至 `/apps/customstyle/templates/styled-sequencechannel`.
   1. 修改 *cq：designPath* 中的屬性 `/apps/customstyle/templates/styled-sequencechannel/jcr:content` 指向新設計。


### 更新ACL {#updating-acls}

您必須更新這些設計的ACL，以便播放器可以下載它們。

1. 導覽至使用者管理員，然後選擇 `screens-<project>-devices group` 並給予其自訂設計路徑的讀取許可權。

1. 提供 `screens-<project>-administrators` 群組讀取及修改此路徑的許可權。

## 檢視結果 {#viewing-the-result}

完成上述步驟後，您可以更新 *statis.css* 檔案來源 **CRXDE Lite** 並檢視已新增至資產的文字覆蓋更新。

請依照下列步驟，檢視文字覆蓋的更新設計：

1. 導覽至您的AEM Screens專案，標題為 **customstyle** —> **頻道** —> **DemoBrand**. 選取管道並按一下 **編輯** 以開啟編輯器。

1. 由於您現在已將設計新增至 **設計** 欄位，如上所述，按一下 **預覽** 在含有文字覆蓋的影像上檢視目前的樣式。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 導覽至 *static.css* CRXDE Lite檔案，並新增字型，例如， `font-family: "Lucida Console", Courier, monospace;` 至此檔案，如下所示。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 儲存變更並重新載入預覽後，您將會看到文字覆蓋字型的更新，如下圖所示。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 此外，您也可以從中移除程式碼的最後兩個區塊 *static.css* 檔案移除文字覆蓋周圍的盒裝樣式。
   ![图像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 您將在影像中新增文字覆蓋的預覽中檢視更新的變更。

   ![图像](/help/user-guide/assets/custom-brand/custom-brand11.png)

   現在您已準備好更新您的品牌和自訂樣式，以取得新增至資產的文字覆蓋圖。
