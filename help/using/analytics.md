---
title: Analytics與AEM Screens
seo-title: Analytics with AEM Screens
description: 本頁說明使用AEM Screens進行Analytics
seo-description: The page describes the analytics with AEM Screens
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Analytics與AEM Screens {#analytics-screens}

>[!NOTE]
>
>此活動的一般利害關係人為行銷/業務策略專家。

AEM Screens提供在本機擷取每個播放器裝置執行的每個可追蹤事件的功能。 此資料將會儲存在本機，直到可以上傳至雲端以進行處理為止。 除了所有事件資料外，也會新增deviceID和timestamp。 這可確保來自一個播放器的資料可與另一個播放器區分，並且可視需要單獨評估在一天中不同時間執行的資料。

我們擷取此資料有兩個基本原因。

第一個涉及 **回饋回圈與機器學習** 而第二個涉及 **建立圖表、控制面板和報告** 供人類使用。

在回饋回圈使用案例中，我們並不在乎視覺報表或控制面板，而是想要定義AEM可針對內容修改執行的規則。 我們會使用及處理特定時段內的所有Screens播放器事件資料，藉此定義評估image1與image2效能的規則。 透過結合銷售資料與播放資料，AEM可判斷image1對銷售的影響更大，並自動指示所有播放器使用image1。

使用Analytics的第二個使用案例是透過報表和儀表板處理播放事件和使用資料，以供人類消耗。
我們可能會使用此資料來建立互動式體驗的熱度圖，以透過我們的應用程式決定偏好的歷程圖。 我們也可以選擇建立儀表板，以圖形化方式解譯消費者與應用程式互動的次數。
