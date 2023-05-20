---
title: 在AEM Screens中使用最適化轉譯
description: 本頁說明如何在AEM Screens中使用最適化轉譯。
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: cd26f77b9b41a5854aaa1f936abed3b410533684
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# 在AEM Screens中使用最適化轉譯 {#adaptive-renditions}

## 简介 {#introduction}

最適化轉譯可讓裝置根據客戶定義的規則，自動為裝置選取最佳轉譯。 裝置會根據這些規則，自動下載並播放資產的最適當轉譯，讓客戶僅能專注於設計 *主要* 體驗。

## 目标 {#objective}

身為AEM Screens內容作者，您現在可以將裝置特定的資產轉譯設定為自動下載和播放，而不需要手動建立所有內容變化。
開發人員新增轉譯對應屬性和規則後，您現在就可以將轉譯對應套用至資產，並隨後將這些資產納入AEM Screens頻道。

>[!IMPORTANT]
>開始使用最適化轉譯之前，建議您先在AEM Screens管道中瞭解此功能的架構概觀和設定。 另請參閱 [最適化轉譯：架構概觀和設定](/help/user-guide/adaptive-renditions.md) 以取得更多詳細資料。

## 在頻道中使用最適化轉譯 {#using-adaptive-renditions}

>[!NOTE]
>新增後 [轉譯對應屬性至畫面專案](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) 和 [轉譯對應規則](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)，身為內容作者，您現在可以將轉譯套用至資產。

### 將轉譯套用至資產 {#apply-renditions-assets}

請依照下列步驟，將轉譯套用至您要用於導覽Screens頻道的資產：

1. 導覽至 **資產** AEM資料夾。

1. 建立更適合招牌顯示的資產版本，例如， `seahorse.jpg`.

1. 選擇轉譯命名模式，例如，`landscape`，類似於中定義的 **圖樣** 中的屬性 **CRXDE Lite**. 請參閱 [新增轉譯對應規則](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) 以取得更多詳細資料。

1. 按一下 **新增轉譯** 上傳轉譯，如下圖所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. 選取重新命名的資產檔案。 您新增的轉譯必須包含模式（在步驟3中定義），例如， `seahorse-landscape.png`.

1. 新增資產後，請選取資產並按一下 **管理發布** 以發佈資產。

   ![图像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >請參閱 [隨選內容更新](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content.html?lang=en) 以進一步瞭解如何管理出版物以及將內容更新從作者傳送至發佈裝置。


## 移轉策略 {#migration-strategy}

>[!IMPORTANT]
>對於大型網路，建議逐步進行移轉，以降低風險，因為功能將會變更資訊清單和檔案儲存格式。 新增 `sling:configRef` 整個專案涉及將所有播放器更新至Feature Pack 6.5.9。如果您更新了部分播放器，則需要新增 `sling:configRef` 僅限所有播放器皆更新至Feature Pack 6.5.9的顯示器、位置或頻道資料夾。

下圖說明大型網路的移轉策略：

![图像](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

若要啟用此功能，請至少新增一個對應規則，並確認轉譯對應設定在顯示和管道的上下文中可解析。 請依照下列步驟進行移轉：

1. 新增 [節目對應規則](/help/user-guide/adaptive-renditions.md).
1. 為新頻道建立資料夾，並新增指向轉譯對應設定的參考。
1. 建立新管道來取代舊管道，並上傳轉譯。
1. 重新指派顯示區給新色版。
1. 新增參考至移轉的顯示區或指向轉譯對應設定的位置。
1. 對所有其餘的色版和顯示器重複步驟3、4和5。

   >[!NOTE]
   >完成移轉後，請務必移除頻道、顯示區和位置中的所有設定參照，並將單一設定參照新增至專案內容節點。
