---
title: 旅行中心溫度啟用
seo-title: Travel Center Temperature Activation
description: 下列使用案例示範如何根據Google Sheets中填入的值，使用旅行中心當地溫度啟動。
seo-description: The following use case demonstrates the usage of travel center local temperature activation based on the values populated in Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 旅行中心溫度啟用 {#travel-center-temperature-activation}

下列使用案例示範如何根據Google Sheets中填入的值，使用旅行中心當地溫度啟動。

## 描述 {#description}

針對此使用案例，如果您的Google工作表值小於50，則會顯示含有熱飲的影像，而如果值大於或等於50，則會顯示含有冷飲的影像。 如果有其他值或沒有值，播放器會顯示預設影像。

## 先決條件 {#preconditions}

在開始實作旅行中心當地溫度啟動之前，您必須瞭解如何設定 ***資料存放區***， ***對象細分*** 和 ***啟用頻道目標定位*** 在AEM Screens專案中。

請參閱 [在AEM Screens中設定ContextHub](configuring-context-hub.md) 詳細資訊。

## 基本流量 {#basic-flow}

請依照下列步驟，實作Travel Center Local Template Activation使用案例：

1. **填入Google工作表**

   1. 導覽至ContextHubDemo Google工作表。
   1. 新增欄，使用 **標題1** 有對應的溫度值。

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **根據需求在Audiences中設定區段**

   1. 導覽至您對象中的區段(請參閱 ***步驟2：設定對象細分*** 在 **[在AEM Screens中設定ContextHub](configuring-context-hub.md)** 頁面（以取得更多詳細資料）。

   1. 選取 **工作表A1 1** 並按一下 **編輯**.

   1. 選取比較屬性，然後按一下設定圖示以編輯屬性。
   1. 選取 **Googlesheets/value/1/0** 從的下拉式清單 **屬性名稱**

   1. 選取 **運運算元** 作為 **大於或等於** 從下拉式功能表

   1. 輸入 **值** 作為 **50**

   1. 同樣地，選取 **工作表A1 2** 並按一下 **編輯**.

   1. 選取 **比較屬性 — 值** 並按一下「設定」圖示以編輯屬性。
   1. 選取 **Googlesheets/value/1/0** 從的下拉式清單 **屬性名稱**

   1. 選取 **運運算元** 作為 **小於** 從下拉式功能表

   1. 輸入 **值** 作為 **50**

1. 導覽並選取您的頻道()然後按一下 **編輯** 動作列中的。 在以下範例中， **DataDrivenWeather**，循序頻道可用來展示此功能。

   >[!NOTE]
   >
   >您的頻道應已有預設影像，且對象應已預先設定，如所述 [在AEM Screens中設定ContextHub](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >您應已設定您的 **ContextHub** **設定** 使用管道 **屬性** —> **個人化** 標籤。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 選取 **目標定位** 從編輯器中，然後選取 **品牌** 和 **活動** 從下拉式功能表，然後按一下 **開始定位**.

   ![new_activity3](assets/new_activity3.gif)

1. **檢查預覽**

   1. 按一下 **預覽。** 此外，請開啟Google工作表並更新其值。
   1. 將值變更為小於50，您應該就能檢視夏季飲料的影像。 如果「Google工作表」中的值大於或等於50，則應能夠檢視熱飲影像。
   ![result3](assets/result3.gif)
