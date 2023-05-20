---
title: 零售詳細目錄目標啟動
seo-title: Retail Inventory Targeted Activation
description: 此使用案例顯示三種不同顏色運動衫的零售存貨量。 根據Google Sheets中記錄的可用庫存運動衫數量，畫面上會顯示數量最高的影像（紅色、綠色或藍色運動衫）。
seo-description: This Use Case showcases the retail inventory stock for three different colored sweatshirts. Depending on the number of sweatshirts available in stock that is recorded in Google Sheets, the image (red, green, or blue sweatshirt) with highest number is displayed on the screen.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# 零售詳細目錄目標啟動 {#retail-inventory-targeted-activation}

下列使用案例會根據Google工作表中的值，示範三種不同的影像。

## 描述 {#description}

此使用案例顯示三種不同顏色運動衫的零售存貨量。 根據Google Sheets中記錄的可用庫存運動衫數量，畫面上會顯示數量最高的影像（紅色、綠色或藍色運動衫）。

在此使用案例中，紅色、綠色或藍色毛衣會根據可用毛衣數量上限顯示在熒幕上。

## 先決條件 {#preconditions}

開始實作零售詳細目錄目標定位啟用之前，您必須瞭解如何設定 ***資料存放區***， ***對象細分*** 和 ***啟用頻道目標定位*** 在AEM Screens專案中。

請參閱 [在AEM Screens中設定ContextHub](configuring-context-hub.md) 詳細資訊。

## 基本流量 {#basic-flow}

請依照下列步驟實作「零售庫存啟用」使用案例：

1. **填入Google工作表**

   1. 導覽至ContextHubDemo Google工作表。
   1. 為三件不同運動衫新增具有對應值的三欄（紅色、綠色和藍色）。

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **依需求設定對象**

   1. 導覽至您對象中的區段(請參閱 ***步驟2：設定對象細分*** 在 **[在AEM Screens中設定ContextHub](configuring-context-hub.md)** 頁面（以取得更多詳細資料）。

   1. 新增三個新區段 **For_Red**， **For_Green**、和 **For_Blue**.

   1. 選取 **For_Red** 並按一下 **編輯** 動作列中的。

   1. 拖放 **比較：屬性 — 屬性** 至編輯器，然後按一下「設定」圖示以編輯屬性。
   1. 選取 **Googlesheets/value/1/2** 從的下拉式清單 **第一個屬性名稱**

   1. 選取 **運運算元** 作為 **大於** 從下拉式功能表

   1. 選取 **資料型別** 作為 **數字**

   1. 選取 **Googlesheets/value/1/1** 從的下拉式清單 **第二個屬性名稱**.

   1. 拖放 **其他比較：屬性 — 屬性** 至編輯器，然後按一下「設定」圖示以編輯屬性。
   1. 選取 **Googlesheets/value/1/2** 從的下拉式清單 **第一個屬性名稱**.

   1. 選取 **運運算元** 作為 **大於** 從下拉式功能表

   1. 選取 **資料型別** 作為 **數字**

   1. 選取 **Googlesheets/value/1/0** 從的下拉式清單 **第二個屬性名稱**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同樣地，編輯比較屬性規則並將其新增至 **For_Blue** 區段，如下圖所示：

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同樣地，編輯比較屬性規則並將其新增到** For_Green **segment，如下圖所示：

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >您會注意到，針對區段 **For_Green** 和 **For_Green**，資料無法在編輯器中解析，因為根據Google工作表中的值，目前只有第一次比較有效。

1. 瀏覽並選取 **DataDrivenRetail** 管道（循序管道）並按一下 **編輯** 動作列中的。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >您應已設定您的 **ContextHub** **設定** 使用管道 **屬性** —> **個人化** 標籤。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   您必須同時選取 **品牌** 和 **區域** ，以便在您啟動鎖定目標程式時可正確列出活動。

1. **新增預設影像**

   1. 新增預設影像至您的色版，然後按一下 **目標定位**.
   1. 選取 **品牌** 和 **活動** 從下拉式功能表，然後按一下 **開始定位**.

   1. 按一下 **開始定位**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   開始鎖定目標之前，您必須新增區段(**For_Green**， **For_Red**、和 **For_Blue**)，方法是按一下 **+新增體驗鎖定目標** 從側邊欄移除，如下圖所示。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 將影像新增至所有三個不同的熒幕，如下所示。

   ![retail_targeting](assets/retail_targeting.gif)

1. **檢查預覽**

   1. 按一下 **預覽。** 此外，請開啟Google工作表並更新其值。
   1. 變更所有三個不同欄的值，您會注意到顯示影像已根據詳細目錄中的最高值更新。
   ![retail_result](assets/retail_result.gif)
