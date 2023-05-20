---
title: 隨選內容更新
seo-title: On-Demand Content Update
description: 請依照本頁面的說明了解隨選內容更新。
seo-description: Follow this page to learn about On-Demand Content Update.
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 9ffdb1eb-a1ba-42ac-a30f-260004e5b165
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# 隨選內容更新 {#on-demand}

本節說明管理出版物的隨選內容。

## 管理發布：將內容更新從作者傳送至發佈至裝置 {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

您可以從AEM Screens發佈和取消發佈內容。 「管理發布」功能可讓您傳遞內容更新，從作者更新至發佈至裝置。 您可以為整個AEM Screens專案或僅限其中一個頻道、位置、裝置、應用程式或排程發佈/取消發佈內容。

### 管理AEM Screens專案的發佈 {#managing-publication-for-an-aem-screens-project}

請依照下列步驟，針對AEM Screens專案，將內容更新從作者傳送至發佈裝置：

1. 導覽至您的AEM Screens專案。
1. 按一下 **管理發布** 從動作列將專案發佈到發佈例項。

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. 此 **管理發布** 精靈開啟。 您可以選取 **動作** 以及將發佈時間排程為現在或以後。 单击&#x200B;**下一步**。

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 核取方塊以從中選取整個專案 **管理發布** 精靈。

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. 按一下 **+包含子項** ，然後取消勾選所有選項以發佈專案中的所有模組，然後按一下 **新增** 以發佈。

   >[!NOTE]
   >
   >依預設，所有方塊都會勾選，您必須手動取消勾選方塊才能發佈專案中的所有模組。

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **瞭解包含子系對話方塊**

   上述步驟說明如何發佈整個內容。 如果您要使用其他三個可用的替代方案，則必須核取該特定選項。
例如，下列影像可讓您僅管理和更新專案中已修改的頁面：
   ![图像](assets/author-publish-manage.png)

   請依照下列說明了解可用的選項：

   1. **僅包括直接子項**：此選項可讓您僅管理專案結構中子節點的更新。
   1. **僅包含已修改的頁面**：此選項可讓您僅管理在專案結構中發現變更之專案已修改頁面的更新。
   1. **僅包含已發佈的頁面**：此選項允許僅管理對之前已發佈頁面的更新。


1. 按一下 **發佈** 從 **管理出版物精靈。**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >等候幾秒鐘/分鐘，讓內容到達發佈執行個體。
   >
   >
   >    1. 如果專案中沒有變更，工作流程將無法運作。 **更新離線內容**.
   >    1. 如果作者在按一下「 」後未完成復寫程式（內容仍在上傳到發佈執行個體），工作流程將無法運作。 **發佈** 管理工作流程中的按鈕。


   >[!CAUTION]
   >如果您是作者或內容建立者，且想檢視附加至作者執行個體的裝置變更，請按一下 **更新離線內容** 從頻道控制面板或透過選取專案。 在此情況下，更新離線內容只會在Author例項中執行。

1. 導覽至專案並按一下 **更新離線內容** 動作列中的。 此動作會將相同命令轉送至發佈執行個體，以便離線壓縮程式碼也建立在發佈執行個體上。

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >完成管理發布工作流程後，如果存在指向作者執行個體的播放器，您必須在作者中觸發更新離線內容，該操作將在作者執行個體上離線建立更新。

   >[!CAUTION]
   >
   >如果您已將播放器註冊到作者伺服器，則必須觸發作者例項中的更新離線內容。 註冊至發佈執行個體的播放器不需要更新離線內容。

### 管理管道的發佈 {#managing-publication-for-a-channel}

請依照下列步驟，針對AEM Screens專案中的管道，將內容更新從作者傳送至發佈至裝置：

>[!NOTE]
>
>只有在管道發生變更時，才應遵循本節。 如果管道在上次更新離線內容後沒有任何變更，則個別管道的管理發布工作流程將無法運作。

1. 導覽至您的Screens專案並選取頻道。
1. 按一下 **管理發布** 以發佈管道至發佈例項。

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. 此 **管理發布** 精靈開啟。 您可以選取 **動作** 以及將發佈時間排程為現在或以後。 单击&#x200B;**下一步**。

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 按一下 **發佈** 從 **管理出版物精靈。**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >等候幾秒鐘/分鐘，讓內容到達發佈執行個體。

1. 觸發 **更新離線內容** 在管道儀表板中，只會將離線內容推送至作者例項，而不會推送至發佈例項。 步驟1-4用於將離線內容推送至發佈例項。

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >您必須先發佈，然後觸發更新離線內容，如先前步驟所述。

### 頻道和裝置重新指派： {#channel-and-device-re-assignment}

如果您已重新指派裝置，則一旦將裝置重新指派給新顯示，您必須發佈初始顯示和新顯示。

同樣地，如果您已重新指派管道，一旦管道重新指派給新顯示，您必須發佈初始顯示和新顯示。
