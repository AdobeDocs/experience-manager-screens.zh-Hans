---
title: Hospality Reservation Activation
seo-title: Hospitality Reservation Activation
description: 下列使用案例示範如何根據Google工作表填入的值，啟用醫院預訂的功能。
seo-description: The following use case demonstrates the usage of hospital reservation activation based on the values populated in Google Sheets.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Hospality Reservation Activation {#hospitality-reservation-activation}

下列使用案例示範如何根據Google工作表填入的值，啟用醫院預訂的功能。

## 描述 {#description}

對於此使用案例，Google工作表會填入兩個餐廳的預訂百分比 **餐廳1** 和 **餐廳2**. 根據Restaurant1和Restaurant2的值套用公式，並根據公式，將值1或2指派給 **adtarget** 欄。

如果 **餐廳1** > **餐廳2**，則 **AdTarget** 已指派值 **1** 否則 **adtarget** 已指派值 **2**. 值1產生 *牛排食品* 選項和值2會顯示 *泰國菜* 選項。

## 先決條件 {#preconditions}

在開始實施預訂啟動之前，您必須瞭解如何設定 ***資料存放區***， ***對象細分*** 和 ***啟用頻道目標定位*** 在AEM Screens專案中。

請參閱 [在AEM Screens中設定ContextHub](configuring-context-hub.md) 詳細資訊。

## 基本流量 {#basic-flow}

請依照下列步驟，為您的AEM Screens專案實作旅館預訂啟用使用案例：

1. **填入Google工作表並新增公式。**

   例如，將公式套用至第三欄 **adtarget**，如下圖所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根據需求在Audiences中設定區段**

   1. 導覽至您對象中的區段(請參閱 ***步驟2：設定對象細分*** 在 **[在AEM Screens中設定ContextHub](configuring-context-hub.md)** 頁面（以取得更多詳細資料）。

   1. 選取 **工作表A1 1** 並按一下 **編輯**.

   1. 選取比較屬性，然後按一下設定圖示以編輯屬性。
   1. 選取 **Googlesheets/value/1/2** 從的下拉式清單 **屬性名稱**

   1. 選取 **運運算元** 作為 **等於** 從下拉式功能表

   1. 輸入 **值** 作為 **1**

   1. 同樣地，選取 **工作表A1 2** 並按一下 **編輯**.

   1. 選取比較屬性，然後按一下設定圖示以編輯屬性。
   1. 選取 **Googlesheets/value/1/2** 從的下拉式清單 **屬性名稱**

   1. 選取 **運運算元** 作為 **2**

1. 導覽並選取您的頻道()然後按一下 **編輯** 動作列中的。 在以下範例中， **DataDrivenRestaurant**，循序頻道可用來展示此功能。

   >[!NOTE]
   >
   >您的頻道應已有預設影像，且對象應已預先設定，如所述 [在AEM Screens中設定ContextHub](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >您應已設定您的 **ContextHub** **設定** 使用管道 **屬性** —> **個人化** 標籤。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 選取 **目標定位** 從編輯器中，然後選取 **品牌** 和 **活動** 從下拉式功能表，然後按一下 **開始定位**.
1. **檢查預覽**

   1. 按一下 **預覽。** 此外，請開啟Google工作表並更新其值。
   1. 更新中的值 **餐廳1** 和 **餐廳2** 欄。 若 **餐廳1** > **餐廳2** 您應該能夠檢視 *牛排* 其他食物， *泰文* 食物影像會顯示在熒幕上。
   ![result5](assets/result5.gif)
