---
title: 套用轉變
seo-title: Applying Transitions
description: 請依照本頁面的說明操作，瞭解如何將轉變套用至您的Screens專案。
seo-description: Follow this page to learn how to apply transitions to your Screens projects.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 1%

---

# 套用轉變 {#applying-transitions}

本節說明如何套用 **轉變** 不同資產（影像和影片）之間的元件，以及管道中的內嵌順序。


>[!CAUTION]
>
>詳細瞭解 **轉變** 元件，請參閱 [轉變](adding-components-to-a-channel.md#transition).

## 在管道中新增轉變元件至資產 {#adding-transition}

請依照下列步驟，將轉變元件新增至您的AEM Screens專案：

>[!NOTE]
>
>**前提条件**
>
>建立AEM Screens專案 **TestProject** 使用管道 **TestTransition**. 此外，設定位置和顯示以檢視輸出。

1. 導覽至頻道 **TestTransition** 並按一下 **編輯** 動作列中的。

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >此 **TestTransition** 頻道中已有少量資產（影像和影片）。 例如， **TestTransition** 頻道包含三個影像和兩個影片，如下所示：

   ![image2](assets/transitions2.png)


1. 拖放 **轉變** 元件至您的編輯器。
   >[!CAUTION]
   >
   >將轉變新增至管道中的資產之前，請務必不要在循序管道中的第一個資產之前新增轉變。 管道中的第一個專案必須是資產，而不是轉變。

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >依預設，轉變元件的屬性，例如 **型別** 設為 **淡化** 和 **持續時間** 設為 *1600毫秒*.  此外，不建議將過渡持續時間設定為長於套用到的資產。

1. 此外，如果您新增 **內嵌順序** 元件（包括順序頻道）至此頻道編輯器，您可以在結尾新增轉變元件，以便內容依序播放，如下圖所示：

   ![image3](assets/transitions5.png)
