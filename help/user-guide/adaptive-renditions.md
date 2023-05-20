---
title: 最適化轉譯架構概觀和設定
description: 本頁面說明AEM Screens中最適化轉譯之CRXDE Lite的架構概觀和設定。
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: e5da55eeb5da3d0ef9f21bd47bfec75d660a6a1e
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 3%

---

# 最適化轉譯：架構概觀和設定 {#adaptive-renditions}

## 简介 {#introduction}

最適化轉譯可讓裝置根據客戶定義的規則，自動為裝置選取最佳轉譯。 裝置會根據這些規則，自動下載並播放資產的最適當轉譯，讓客戶僅能專注於設計 *主要* 體驗。

## 目标 {#objective}

身為AEM Screens開發人員，您現在可以將裝置特定的資產轉譯設定為自動下載和播放，而不需要手動建立所有內容變化。 您必須先設定最適化轉譯，內容作者才能在AEM Screens頻道中使用此功能。

## 架构概述 {#architectural-overview}

最適化轉譯是根據特定命名慣例命名多個資產轉譯的構想。 播放特定轉譯的決定是透過評估只能在具有預期功能的裝置上解析的媒體查詢運算式而做出的。

具有關聯轉譯命名模式的功能會定義轉譯對應規則，例如直向或橫向，如下圖所示。 計算所有可用運算式後，Screens播放器會收集對應至相符規則的命名模式。 在連續播放期間，會透過在轉譯名稱中尋找模式來使用模式尋找正確的轉譯。

![图像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## 將轉譯對應屬性新增至畫面專案 {#rendition-mapping-new}

若要啟用「最適化轉譯」功能，下列對應規則應該存在，而且上下文感知(CA)設定應該可解析用於頻道和顯示器。

>[!NOTE]
>若要進一步瞭解內容感知設定，請參閱 [此處](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

請依照下列步驟進行設定：

1. 導覽至 **CRXDE Lite**. 檢查，如果 **轉譯 — 對應** 設定存在於 `/conf/screens/sling:configs/rendition-mapping`，如下圖所示。

   >![图像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >如果您已安裝最新的Feature Pack 202109，您將會看到 **轉譯 — 對應** 節點結構預先填入 `/conf/screens/sling:configs/rendition-mapping` 在CRXDE Lite中。 另請參閱 [Feature Pack 202109發行說明](/help/user-guide/release-notes-fp-202109.md) 以取得最新feature pack的詳細資訊。
   >對於現有專案，請確定Screens專案具有 **轉譯 — 對應** 相關設定。 另請參閱 [新增轉譯對應至現有專案](#rendition-mapping-existing) 區段以瞭解更多資訊。

### 新增轉譯對應屬性至現有專案 {#rendition-mapping-existing}

1. 導覽至 **CRXDE Lite**.

1. 透過新增來明確定義轉譯對應關聯 `sling:configRef` 屬性指向 `/conf/screens` 至專案內容節點，如下圖所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## 新增轉譯對應規則 {#add-rendition-mapping-rules}

請依照下列步驟，在「轉譯對應」下新增節點：

1. 導覽至此路徑 `/conf/screens/sling:configs/rendition-mapping` 從 **CRXDE Lite**.

1. 在下建立節點 **轉譯 — 對應**. 按一下右鍵 **轉譯 — 對應** 並按一下 **建立** —> **建立節點**，如下圖所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. 輸入 **名稱** 對應規則的其他引數，例如 **rule1** 和節點 **型別** 作為 **nt：unstructured** 在 **建立節點** 對話方塊。 按一下 **確定**.

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. 您需要使用包含查詢運算式的值來新增運算式屬性。

   >[!NOTE]
   >請參閱 [使用媒體查詢語法](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) 以深入瞭解。

   按一下 **rule1** ，並輸入 **運算式** 在 **名稱** 和 **(orientation：landscape)** 在 **值**，如下所示。 按一下 **新增**.

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. 使用包含轉譯命名模式的值新增pattern屬性。

   >[!NOTE]
   >模式屬性中定義的值會與新資產轉譯相符，如果運算式評估為true，則會加以選取。

   若要新增模式屬性，請按一下 **rule1** ，並輸入 **圖樣** 在 **名稱** 和 **橫向** 在 **值**，如下所示。 按一下 **新增**.

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. 按一下 **全部儲存** 而且您會在您建立的節點下看到屬性 **轉譯 — 對應**.

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## 后续步骤 {#next-steps}

新增轉譯對應屬性和規則後，身為內容作者，您可以設定資產以使用最適化轉譯，並移轉大型網路的裝置，以便在AEM Screens管道中使用此功能。 另請參閱 [在AEM Screens中使用最適化轉譯](/help/user-guide/using-adaptive-renditions.md) 以取得更多詳細資料。
