---
title: 使用動態內嵌序列
seo-title: Using Dynamic Embedded Sequence
description: 請依照本頁所述操作，瞭解如何在AEM Screens專案中實作動態內嵌序列。
seo-description: Follow this page to learn how to implement Dynamic Embedded Sequences in your AEM Screens project.
uuid: 1f442489-2eeb-4dd8-b892-911fcccb3377
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: a40eb5bb-fbf7-4c0d-a34a-db79b884de8f
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3208d058-0812-44e1-83e3-b727b384876a
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '2515'
ht-degree: 2%

---

# 使用動態內嵌序列 {#using-dynamic-embedded-sequence}

使用動態內嵌序列涵蓋下列主題：

* **概述**
* **在AEM Screens中使用動態內嵌式體驗**
* **檢視結果**
* **限制使用者和修改ACL**

## 概述 {#overview}

***動態內嵌序列*** 會為遵循父子階層的大型專案建立，其中子系會在位置資料夾內參照，而不是頻道資料夾。 它可讓使用者透過以下方式將序列內嵌在管道中 ***頻道角色***. 它可讓使用者使用主管道內的內嵌順序，為不同的辦公室定義位置特定的預留位置。

將管道指派給顯示時，您可以選擇指定顯示的路徑或管道的角色（會根據內容解析為實際管道）。

若要使用「動態內嵌序列」，您需透過以下方式指派管道 ***頻道角色***. 管道角色定義顯示的內容。 該角色由各種動作定位，並且獨立於履行該角色的實際頻道。 本節說明依角色定義管道的使用案例，以及如何將該內容用於全域管道。 您也可以將角色視為指派的識別碼，或前後關聯中管道的別名。

### 使用動態內嵌序列的好處 {#benefits-of-using-dynamic-embedded-sequences}

將順序頻道放在位置內而非頻道資料夾的主要優點，是允許本機或區域作者編輯與其相關的內容，同時受限制無法編輯階層中較高層的頻道。

參照 *依角色頻道*，可讓您建立本機版本的管道，以動態解析位置專用內容，也可讓您建立全域管道，將內容用於位置專用管道。

>[!NOTE]
>
>**內嵌序列與動態內嵌序列**
>
>「動態內嵌序列」類似於內嵌序列，但允許使用者遵循階層，對其中一個管道所做的變更/更新會傳播至相關的另一個管道。 它遵循父子层次结构，并且还包括图像或视频等资产。
>
>***動態內嵌序列*** 可讓您顯示特定位置的內容，而 ***內嵌順序*** 只顯示內容的一般投影片放映。 此外，在設定動態內嵌序列時，您需要使用頻道角色和名稱來設定頻道。 如需實際實施，請參閱以下步驟。
>
>若要進一步瞭解如何實作內嵌序列，請參閱 [內嵌順序](embedded-sequences.md) 在AEM Screens中。

下列範例著重下列主要辭彙，提供解決方案：

* a ***主序列頻道*** 全域序列
* ***動態內嵌序列*** 序列中每個本機可自訂部分的元件
* ***個別序列頻道*** 在個別位置，具有 *角色* 在符合以下條件的顯示中： **動態內嵌序列元件的 *角色*.**

>[!NOTE]
>
>若要進一步瞭解頻道指定任務，請參閱 **[頻道指定任務](channel-assignment.md)** 在AEM Screens檔案的「編寫」區段底下。

## 使用動態內嵌序列 {#using-dynamic-embedded-sequence-2}

下節將說明如何在AEM Screens管道中建立動態內嵌序列。

### 前提条件 {#prerequisites}

開始實作此功能之前，請確定您已具備下列先決條件，可以開始實作動態內嵌序列：

* 建立AEM Screens專案(在此範例中， **示範**)

* 建立管道為 **全域** 在 **頻道** 資料夾

* 將內容新增至 **全域** 頻道(*請檢查&#x200B;**Resources.zip**相關資產的*)

下圖顯示 **示範** 專案與 **全域** 中的頻道 **頻道** 資料夾。
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### 资源 {#resources}

您可以下載下列資源（影像並將其新增至資產），然後進一步將這些資源作為通道內容用於示範用途。

[获取文件](assets/resources.zip)

>[!NOTE]
>
>如需如何建立專案以及如何建立順序頻道的詳細資訊，請參閱以下資源：
>
>* **[建立和管理專案](creating-a-screens-project.md)**
>* **[管理管道](managing-channels.md)**
>


在AEM Screens專案中實作動態內嵌序列涉及三個主要工作：

1. **設定專案分類法，包括頻道、位置和顯示**
1. **建立排程**
1. **指派排程給每個顯示器**

請依照下列步驟實作該功能：

>[!CAUTION]
>
>實作動態內嵌序列時，請留意 **名稱** 和 **標題** 欄位。 請仔細依照命名法的說明操作。

1. **建立兩個位置資料夾。**

   導覽至 **位置** AEM Screens資料夾，並建立兩個位置資料夾做為 **地區A** 和 **區域B**.

   >[!NOTE]
   >
   >建立 **地區A** 位置資料夾，請務必輸入 **標題** 作為 **地區A** 而且您可以將 **名稱** 欄位空白，因此自動 **region-a** 名稱已擷取。
   >
   >建立位置資料夾的情況類似 **區域B**，如下所示：

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >若要瞭解如何建立位置，請參閱 **[建立和管理位置](managing-locations.md)**.

1. **在每個位置資料夾下建立兩個位置和一個頻道。**

   1. 導覽至 **示範** —> **位置** —> **地區A**.
   1. 選取 **地區A** 並按一下 **+建立** 動作列中的。
   1. 選取 **位置** 從精靈，使用 **標題** 作為 **商店1**. 同樣地，從精靈中建立另一個位置，標題為 **商店2** 替換為 **標題** 作為 **商店2**. 您可以將 **名稱** 建立時欄位空白 **商店1** 和 **商店2**.
   1. 重複步驟(b)，現在選取 **序列頻道** 從精靈中。 輸入 **標題** 作為 **地區A** 和 **名稱** 作為 **區域** 此管道的。

   >[!CAUTION]
   >
   >在建立管道時請務必確認 **地區A**，輸入 **標題** 作為 **地區A** 和 **名稱** 作為 **區域**.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   同樣地，在下方建立兩個位置 **區域B** 標題為 **商店3** 和 **商店4**. 此外，建立 **序列頻道** 替換為 **標題** 作為 **區域B** 和 **名稱** 作為 **區域**.

   >[!CAUTION]
   >
   >請確定您在中建立的管道可以使用相同的名稱 **地區A** 和 **區域B** 作為 **區域**.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **在每個位置下建立顯示和頻道。**

   1. 導覽至 **示範** —> **位置** —> **地區A** —> **商店1**.
   1. 選取 **商店1** 並按一下 **+建立** 動作列中的。
   1. 選取 **顯示** 從精靈並建立 **Store1Display。**
   1. 重複步驟(b)，這次請選取 **序列頻道** 從精靈中。 輸入 **標題** 作為 **Store1Channel** 和 **名稱** 作為 **儲存**.

   >[!CAUTION]
   >
   >建立序列管道時，請務必遵循 **標題** 可以視您的需求而定，但 **名稱** 應該在所有本機通道中都是相同的。
   >在此範例中，位於下方的管道 **地區A** 和 **區域B** 共用相同的 **名稱** 作為 **區域** 和管道位於 **商店1**， **商店2**， **商店3**、和 **商店4** 共用相同的 **名稱** 作為 **儲存**.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   同樣地，建立顯示為 **Store2Display** 和頻道 **Store2Channel** 在 **商店2** (名稱為 **儲存**)。

   >[!NOTE]
   >請確定您在中建立的管道可以使用相同的名稱 **商店1** 和 **商店2** 作為 **儲存**.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   依照上述步驟建立管道並顯示在中 **商店3** 和 **商店4** 在 **區域B**. 再次強調，請務必使用相同的 **名稱** 作為 **儲存** 建立管道時 **Store3Channel** 和 **Store4Channel** （分別）。

   下圖顯示中的顯示區和色版 **商店3**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   下圖顯示中的顯示區和色版 **商店4**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **將內容新增至頻道中各自位置中的專案。**

   導覽至 **示範** -> **位置** -> **地區A** -> **地區A** 並按一下 **編輯** 動作列中的。 拖放您要新增至頻道的資產。

   >[!NOTE]
   >您可以使用 ***Resources.zip*** 檔案來自 **資源** 區段，將影像用作管道內容的資產。

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   同樣地，導覽至 **示範** -> **位置** -> **區域B** -> **區域B** 並按一下 **編輯** 將資產拖放至您的管道中，如下所示：

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   依照上述步驟和資源操作，將內容新增至下列管道：

   * **Store1Channel**
   * **Store2Channel**
   * **Store3Channel**
   * **Store4Channel**

1. **建立排程**

   導覽並選取 **時程表** AEM Screens資料夾，然後按一下「 」 **建立** 以建立新排程。

   下圖顯示 **AdSchedule** 建立於 **示範** 專案。

   ![screen_shot_2018-09-13at33307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **將頻道指派給排程**

   1. 導覽至 **示範** —> **時程表** —> **AdSchedule** 並按一下 **儀表板** 動作列中的。
   1. 按一下 **+指派管道** 從 **已指派的頻道** 面板以開啟 **頻道指定任務** 對話方塊。
   1. 選取 **引用頻道**.. 按照路径.
   1. 選取 **頻道路徑** 作為 **示範** —> ***頻道*** —> ***全域***.
   1. 輸入 **頻道角色** 作為 **GlobalAdSegment**.
   1. 選取 **支援的事件** 作為 **初始載入**， **閒置畫面**、和 **使用者互動**.
   1. 单击“**保存**”。

   **依地區角色指派管道：**

   1. 按一下 **+指派管道** 從 **已指派的頻道** 面板以開啟 **頻道指定任務** 對話方塊。
   1. 選取 **引用頻道**.. 按照名称.
   1. 輸入 **頻道名稱** 作為 **區域***.
   1. 輸入 **頻道角色** 作為 **RegionAdSegment**.
   1. 单击“**保存**”。

   **依儲存區的角色指派頻道：**

   1. 按一下 **+指派管道** 從 **已指派的頻道** 面板以開啟 **頻道指定任務** 對話方塊。
   1. 選取 **引用頻道**.. 按照名称.
   1. 輸入 **頻道名稱** 作為 **儲存**.
   1. 輸入 **頻道角色** 作為 **StoreAdSegment**.
   1. 单击“**保存**”。

   下圖顯示依路徑和角色指派的色版。

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **設定動態內嵌序列至全域頻道。**

   導覽至 **全域** 管道，您最初建立於 **示範** 專案。

   按一下 **編輯** 以開啟編輯器。

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   拖放兩個 **動態內嵌順序** 元件在管道編輯器中。

   開啟其中一個元件的屬性，並輸入 **頻道指派角色** 作為 **RegionAdSegment**.

   同樣地，選取其他元件並開啟屬性以輸入 **頻道指派角色** 作為 **StoreAdSegment**.

   ![channeldisplay4](assets/channeldisplay4.gif)

1. **指派排程給每個顯示器**

   1. 導覽至每個顯示區，例如 **示範** —> **位置** —> **地區A** —>**商店1** —>**Store1Display**.
   1. 按一下 **儀表板** 以開啟顯示控制面板。
   1. 按一下 **...** 從 **已指派的管道和排程** 面板，然後按一下 **+指派排程**.
   1. 選取排程的路徑(例如，此處， **示範** —> **時程表** —>**AdSchedule**)。
   1. 单击“**保存**”。

## 檢視結果 {#viewing-the-results}

設定好管道並顯示完成之後，請啟動AEM Screens播放器以檢視內容。

>[!NOTE]
>
>若要瞭解AEM Screen Player，請參閱下列資源：
>
>* [AEM Screens播放器下載](https://download.macromedia.com/screens/)
>* [使用AEM Screens Player](working-with-screens-player.md)



以下輸出會根據顯示路徑，確認您在AEM Screens播放器中的管道內容。

**案例1**：

如果您將顯示路徑指派為 **示範** —> **位置** —> **地區A** —> **商店1** —> **Store1Display**，下列內容將會顯示在您的AEM Screens播放器中。

![channeldisplay1](assets/channeldisplay1.gif)

**案例1**：

如果您將顯示路徑指派為 **示範** —> **位置** —> **區域B** —> **商店3** —> **Store3Display**，下列內容將會顯示在您的AEM Screens播放器中。

![channeldisplay2](assets/channeldisplay2.gif)

## 限制使用者和修改ACL {#restricting-users-and-modifying-the-acls}

您可以建立全域、區域或本機作者來編輯與他們相關的內容，同時受限制無法編輯階層中較高層的管道。

您需要修改ACL，以根據使用者的位置限制使用者對內容的存取權。

### 範例使用案例 {#example-use-case}

下列範例可讓您為上述示範專案建立三個使用者。

指派給每個群組的許可權如下：

**组**:

* **Global-Author**：由可存取中所有位置和管道的使用者組成。 **示範** 專案並擁有所有讀取、寫入和編輯許可權。

* **Region-Author**：包含對下列專案具有讀取、寫入及編輯許可權的使用者： **地區A** 和 **區域B**.

* **Store-Author**：由只對下列專案具有讀取、寫入和編輯許可權的使用者組成 **商店1**， **商店2**， **商店3**、和 **商店4**.

#### 建立使用者群組、使用者和設定ACL的步驟 {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>若要詳細瞭解如何使用ACL來區隔專案，以便每個個人或團隊處理自己的專案，請參閱 **設定ACL**.

請依照下列步驟建立群組、使用者並根據許可權修改ACL：

1. **建立群組**

   1. 導覽至 **Adobe Experience Manager**.
   1. 按一下 **工具** —> **安全性** —> **群組**.
   1. 按一下 **建立群組** 並輸入 **Global-Author** 在 **ID**.
   1. 单击“**保存并关闭**”。

   同樣地，建立兩個其他群組，例如 **Region-Author** 和 **Store-Author**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **建立使用者並將使用者新增至群組**

   1. 導覽至 **Adobe Experience Manager**.
   1. 按一下 **工具** —> **安全性** —> **使用者**.
   1. 按一下 **建立使用者** 並輸入 **全域 — 使用者** 在 **ID**.
   1. 輸入 **密碼** 並確認此使用者的密碼。
   1. 按一下 **群組** 標籤並輸入群組名稱 **選取群組**，例如，輸入 **Global-Author** 新增 **全域 — 使用者** 至該特定群組。
   1. 单击“**保存并关闭**”。

   同樣地，建立兩個其他使用者，例如 **Region-User** 和 **Store-User** 並將這些專案新增至 **Region-Author** 和 **Store-Author** （分別）。

   >[!NOTE]
   >最佳實務是在群組中新增使用者，然後將許可權指派給每個特定的使用者群組。

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **將所有群組新增至貢獻者**

   1. 導覽至 **Adobe Experience Manager**.
   1. 按一下 **工具** —> **安全性** —> **群組**.
   1. 選取 **貢獻者** 從清單中選取 **成員** 標籤。
   1. 選取 **群組** 例如 **Global-Author**， **Region-Author，** 和 **Store-Author** 貢獻者。
   1. 单击“**保存并关闭**”。

1. **存取每個群組的許可權**

   1. 導覽至 *Useradmin* 和此UI來修改不同群組的許可權。
   1. 搜尋 **Global-Author** 並按一下 **許可權** 標籤，如下圖所示。
   1. 同樣地，您可以存取以下專案的許可權： **Region-Author** 和 **Store-Author**.

   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **修改每個群組的許可權**

   **若為Global-Author：**

   1. 導覽至 **許可權** 標籤
   1. 導覽至 ***/content/screens/demo*** 並檢查所有許可權
   1. 導覽至 ***/content/screens/demo/locations*** 並檢查所有許可權
   1. 導覽至 ***/content/screens/demo/locations/region-a*** 並檢查所有許可權。 同樣地，檢查下列專案的許可權： **region-b**.

   如需瞭解步驟，請參閱下圖：
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   下圖顯示現在的 **全域 — 使用者** 有權存取 **全域頻道** 和兩者 **地區A** 和 **區域B** 所有四個店舖： **商店1**， **商店2**， **商店3**、和 **商店4**.

   ![全局](assets/global.gif)

   **若為Region-Author：**

   1. 導覽至 **許可權** 標籤。
   1. 導覽至 ***/content/screens/demo*** 並且只檢查 **讀取** 許可權。
   1. 導覽至 ***/content/screens/demo/locations*** 並且只檢查 **讀取** 許可權。
   1. 導覽至 ***/content/screens/demo/channels*** 和取消勾選下列專案的許可權： **全域** 頻道。
   1. 導覽至 ***/content/screens/demo/locations***/***region-a*** 並檢查所有許可權。 同樣地，檢查下列專案的許可權： **region-b**.

   如需瞭解步驟，請參閱下圖：

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   下圖顯示，現在Region-User可以存取這兩個 **地區A** 和 **區域B** 所有四個店舖： **商店1**， **商店2**， **商店3**、和 **商店4** 但無法存取 **全域** 頻道。

   ![區域](assets/region.gif)

   **若為Store-Author：**

   1. 導覽至 **許可權** 標籤。
   1. 導覽至 ***/content/screens/demo*** 並且只檢查 **讀取** 許可權。
   1. 導覽至 ***/content/screens/demo/locations*** 並且只檢查 **讀取** 許可權。
   1. 導覽至 ***/content/screens/demo/channels*** 和取消勾選下列專案的許可權： **全域** 頻道。
   1. 導覽至 ***/content/screens/demo/locations/region-a*** 並且只檢查 **讀取** 許可權。 同樣地，僅核取 **讀取** 許可權： **region-b**.
   1. 導覽至 ***/content/screens/demo/locations***/***region-a /store-1*** 並檢查所有許可權。 同樣地，檢查下列專案的許可權： **商店2、商店3** 和 **store-4**.

   如需瞭解步驟，請參閱下圖：

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   下圖顯示現在的 **Store-User** 只能存取四個存放區，即 **商店1**， **商店2**， **商店3**、和 **商店4** 但沒有許可權存取 **全域** 或地區(**地區A** 和 **區域B**)管道。

   ![儲存](assets/store.gif)

>[!NOTE]
>
>若要深入瞭解設定許可權，請參閱 [設定ACL](setting-up-acls.md).
