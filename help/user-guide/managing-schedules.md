---
title: 建立和管理排程
seo-title: Managing Schedules
description: 請依照本頁瞭解「排程」，此排程可讓您將管道組織成可重複使用的群組，如此您就不必針對要顯示內容的每個顯示區個別重複其指派。
seo-description: Follow this page to learn about Schedules, that lets you organize channels into re-usable groups so that you do not have to repeat their assignment individually for each display on which you want to show your content.
uuid: c05328a0-620a-4597-b7b3-f4433e78d4e9
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 75ed3c42-4be9-42ae-9d76-e0343af81516
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# 建立和管理排程 {#creating-and-managing-schedules}

**時程表**(在AEM Screens中)可讓您將管道組織成可重複使用的群組，如此您就不必個別針對要顯示內容的每個顯示重複其指派。

排程結合使用 ***日時段分割***，可讓您設定在一天中的特定時間執行多個管道的全域排程，並一次重複使用該設定來顯示所有顯示器。

>[!NOTE]
>
>此AEM Screens功能僅在您已安裝AEM 6.3 Sites Feature Pack 1時可用。 若要存取此Feature Pack，您必須聯絡Adobe支援並要求存取權。 一旦您擁有許可權，就可以從「封裝共用」下載它。

## 建立排程 {#creating-a-schedule}

您可以為Screens專案建立排程，用於管理使用案例的所有活動。

請依照下列步驟，為您的頻道建立排程：

1. 選取Adobe Experience Manager連結（左上方），然後選取Screens。 或者，您可以直接前往： `http://localhost:4502/screens.html/content/screens`.
1. 導覽至畫面專案，然後按一下 **時程表**.
1. 按一下 **建立** 動作列中的。
1. 選取 **排程** 從 **建立** 精靈並按一下 **下一個**.

1. 輸入 **名稱** 和 **標題** 並按一下 **建立**.

您會在專案中看到具有指定名稱和標題的排程資料夾。


## 檢視控制面板 {#viewing-dashboard}

在專案中建立排程資料夾後，您就可以從排程儀表板檢視詳細資訊。

請依照下列步驟檢視排程控制面板。 下列範例顯示We.Retail專案的控制面板：

1. 導覽至 **時程表** Screens （例如We.Retail）專案的資料夾。

   ![chlimage_1](assets/chlimage_1.png)

1. 按一下 **儀表板** 以開啟排程的控制面板。

   您可以檢視三個不同的面板，例如 **排程資訊**， **已指派的頻道**、和 **已指派的顯示區**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **排程資訊面板** 按一下「排程資訊面板」右上角的「屬性」，以檢視/變更排程的屬性。

   **已指派的色版面板** 按一下「已指派的色版」面板右上角的+指派色版，開啟「色版指派」對話方塊。

   **指派的顯示面板** 從「指定的顯示面板」中選取任何顯示以開啟顯示圖示板。
