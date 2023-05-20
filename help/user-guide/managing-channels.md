---
title: 建立和管理管道
seo-title: Managing Channels
description: 請依照本頁所述操作，瞭解如何建立和管理管道。 此外也說明管道控制面板和編輯管道的內容。
seo-description: Follow this page to learn about creating and managing channels. It also explains channel dashboard and editing content for a channel.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 7bbd211a-f54f-42b9-a1b3-516efe6fb579
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1303'
ht-degree: 3%

---

# 建立和管理管道 {#creating-and-managing-channels}

管道可顯示內容順序（影像和影片），也可顯示網站或單頁應用程式。

此頁面顯示如何建立和管理AEM Screens的管道。

**先決條件**：

* [設定和部署畫面](configuring-screens-introduction.md)
* [建立和管理畫面專案](creating-a-screens-project.md)

## 建立新管道 {#creating-a-new-channel}

為AEM Screens建立專案後，請依照下列步驟為您的專案建立新的管道：

1. 選取Adobe Experience Manager連結（左上方），然後選取Screens。 或者，您也可以直接導覽至 `https://localhost:4502/screens.html/content/screens`.

1. 導覽至您的Screens專案並選取 **頻道** 資料夾。

1. 按一下 **建立** 動作列中的。

   ![demochannel](assets/create-channel1.png)

1. 選取 **序列頻道** 範本來自 **建立** 精靈並按一下 **下一個**.

   ![demochannel](assets/create-channel2.png)

1. 輸入標題為 **ScreensChannel** 並按一下 **建立**.

   ![demochannel](assets/create-project4.png)

1. 順序頻道現在已新增到您的 **頻道** 資料夾。

### 管道型別 {#channel-types}

使用精靈時，可使用下列範本選項，例如：

| **範本選項** | **描述** |
|---|---|
| 渠道文件夹 | 允許建立資料夾以儲存管道集合。 |
| 序列渠道 | 允許建立依序播放元件的色版（在投影片放映中逐一播放）。 |
| 应用程序渠道 | 允許在Screens播放器中顯示您的自訂網頁應用程式。 |
| 1x1 分屏渠道 | 允許在單一區域中檢視元件。 |
| 1x2 分屏渠道 | 允許檢視兩個區域中的資產（水準分割）。 |
| 2X1拆分畫面頻道 | 允許檢視兩個區域中的資產（垂直分割）。 |
| 2x2 分屏渠道 | 允許檢視四個區域中的資產（在矩陣中水平與垂直分割）。 |
| 2x3 分屏渠道 | 允許檢視兩個區域（水準分割）中的資產，其中一個區域大於另一個區域。 |
| 左或右L列拆分畫面頻道 | 可讓內容作者在適當大小的區域中檢視不同型別的資產。 |

>[!NOTE]
>
>拆分畫面頻道會將顯示分割成多個區域，以便您同時並排播放多個體驗。 體驗可以是靜態資產/文字或內嵌序列。

>[!IMPORTANT]
>
> 建立內容並新增至管道後，下一步就是建立位置，然後建立顯示區。 此外，您需要將該頻道指派給顯示器。 如需瞭解詳細資訊，請參閱以下章節結尾的資源。

## 使用管道 {#working-with-channels}

您可以編輯、檢視屬性和控制面板，複製、預覽和刪除管道。


![screen_shot_2019-07-24at103723am](assets/screen_shot_2019-07-24at103723am.png)

### 新增/編輯內容至頻道 {#adding-editing-content-to-a-channel}

若要新增或編輯管道中的內容，請遵循下列步驟：

1. 選取您要編輯的頻道（如上圖所示）。
1. 按一下 **編輯** 從動作列的左上角，編輯頻道屬性。 編輯器隨即開啟，可讓您將資產/元件新增至您要發佈的管道。

>[!NOTE]
>您可以將元件新增至頻道。 請參閱 **[新增元件至管道](adding-components-to-a-channel.md)** 以取得更多詳細資料。

![demochannel1](assets/demochannel1.gif)

**將視訊上傳至頻道**

請依照下列步驟，將視訊上傳至您的頻道：

1. 選取您要上傳視訊的頻道。
1. 按一下 **編輯** 以開啟編輯器。
1. 選取 **影片** 在「資產」下，拖放所需的影片。

>[!NOTE]
>如果您在管道上傳影片時遇到問題，請參閱 [疑難排解影片](troubleshoot-videos.md).

### 檢視屬性 {#viewing-properties}

若要檢視或編輯管道的屬性，請遵循下列步驟：

1. 按一下您要編輯的頻道。
1. 按一下 **屬性** 以檢視/編輯頻道屬性。 下列標籤可讓您變更選項。

![属性](assets/properties.gif)

### 檢視控制面板 {#viewing-dashboard}

若要檢視管道的控制面板，請遵循下列步驟：

1. 選取您要編輯的頻道。
1. 按一下 **儀表板** 以檢視控制面板。 此 **頻道資訊**，**已指派的顯示區**、和 **啟動擱置中** 面板會開啟，如下圖所示：

![儀表板](assets/dashboard.gif)

### 渠道信息 {#channel-information}

「色版資訊」面板說明色版屬性，以及色版的預覽。 此外，它也會提供您頻道為離線或線上的資訊。

按一下(**...**)從 **頻道資訊** 動作列，可檢視屬性、編輯內容或更新頻道的快取（離線內容）。

![screen_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

#### 檢視資訊清單 {#view-manifest}

您可以從頻道儀表板檢視資訊清單。

>[!IMPORTANT]
>此選項僅適用於AEM 6.4 Feature Pack 8或AEM 6.5 Feature Pack 4。

請依照下列步驟，從頻道控制面板啟用此選項：

1. **將頻道設定為離線**
   1. 選取管道並選取 **屬性** 從動作列
   1. 導覽至 **頻道** 按Tab鍵，並請務必取消勾選 **開發人員模式（強制頻道上線）** option
   1. 按一下 **儲存並關閉**
1. **更新脱机内容**
   1. 選取管道並選取 **儀表板** 從動作列
   1. 導覽至 **頻道資訊** 面板並按一下 *...*
   1. 按一下 **更新離線內容**

您應該會看到 **檢視資訊清單** 選項來自 **頻道資訊** 面板中。

![image1](assets/channel-one.png)


### 線上和離線頻道 {#online-and-offline-channels}

>[!NOTE]
>建立管道時，預設為「離線」。

建立管道時，管道可定義為線上或離線管道。

一個 ***線上頻道***，會在即時環境中顯示更新的內容，而 ***離線頻道***，會顯示快取的內容。

請依照下列步驟，讓頻道上線：

1. 瀏覽至管道的方式 **TestProject** —> **頻道** —> **TestChannel**.

   選取頻道。

   ![screen_shot_2019-08-01at31406pm](assets/screen_shot_2019-08-01at31406pm.png)

   按一下 **儀表板** 以檢視播放器的狀態。 此 **頻道資訊** 面板提供有關頻道為線上或離線狀態的資訊。

   ![screen_shot_2019-08-01at31458pm](assets/screen_shot_2019-08-01at31458pm.png)

1. 按一下 **屬性** 並從動作列導覽至 **頻道** 標籤，如下所示：

   ![screen_shot_2019-08-01at31542pm](assets/screen_shot_2019-08-01at31542pm.png)

1. 檢查 **開發人員** **模式（強制頻道上線）** 讓頻道線上上。

   按一下 **儲存並關閉** 以儲存您的選項。

   ![screen_shot_2019-08-01at31658pm](assets/screen_shot_2019-08-01at31658pm.png)

   導覽回頻道控制面板，現在導覽至 **頻道資訊** 面板會顯示播放器的線上狀態。

   ![screen_shot_2019-08-01at31821pm](assets/screen_shot_2019-08-01at31821pm.png)

>[!NOTE]
>如果您要將頻道再次設定為離線，請從以下位置取消勾選「開發人員模式」選項： **屬性** 標籤(如步驟(3)所示)，然後從 **頻道資訊** 面板點按 **更新離線內容**，如下圖所示。

![dashboard2](assets/dashboard2.gif)

#### 從裝置儀表板自動與手動更新 {#automatic-versus-manual-updates-from-the-device-dashboard}

下表總結列出與裝置控制面板中的自動和手動更新相關聯的事件。

<table>
 <tbody>
  <tr>
   <td><strong>Event</strong></td>
   <td><strong>裝置自動更新</strong></td>
   <td><strong>裝置手動更新</strong></td>
  </tr>
  <tr>
   <td>線上頻道中的變更</td>
   <td>內容已自動更新</td>
   <td><p>「裝置：推送設定」上已更新內容</p> <p>或者,</p> <p>內容更新日期 <strong><i>裝置：重新啟動</i></strong></p> </td>
  </tr>
  <tr>
   <td>離線管道變更，但未觸發管道「推送內容」（未重新建立離線套件）</td>
   <td>無內容更新</td>
   <td>無內容更新</td>
  </tr>
  <tr>
   <td>離線頻道和頻道「推送內容」中的變更已觸發（新的離線套件）</td>
   <td>內容已自動更新</td>
   <td><p>內容更新日期 <strong><i>裝置：推送設定</i></strong></p> <p>或者,</p> <p>內容更新日期 <strong><i>裝置：重新啟動</i></strong></p> </td>
  </tr>
  <tr>
   <td><p>設定中的變更</p>
    <ul>
     <li>顯示（強制頻道）</li>
     <li>设备</li>
     <li>管道指派（新管道、已移除管道）</li>
     <li>頻道指派（角色、事件、排程）</li>
    </ul> </td>
   <td>設定已自動更新</td>
   <td><p>設定更新日期 <strong><i>裝置：推送設定</i></strong></p> <p>或者,</p> <p>設定更新日期 <strong><i>裝置：重新啟動</i></strong></p> </td>
  </tr>
 </tbody>
</table>

### 已指定显示 {#assigned-displays}

指派的顯示面板會顯示與色版相關聯的顯示。 它提供指定顯示的快照以及解析度。

關聯的顯示專案會列在 **已指派的顯示** 面板，如下所示：

![chlimage_1-27](assets/chlimage_1-27.png)

>[!NOTE]
>若要瞭解如何在位置中建立顯示，請參閱：
>
>* [建立和管理位置](managing-locations.md)
>* [建立和管理顯示區](managing-displays.md)
>


此外，按一下 **已指派的顯示區** 面板，檢視顯示資訊，如下所示：

![chlimage_1-28](assets/chlimage_1-28.png)

### 后续步骤 {#the-next-steps}

建立管道並在管道中新增/編輯內容後的下一個步驟，是瞭解如何建立位置及顯示。 再者，為該顯示區指派管道。

如需後續步驟，請參閱下列資源：

* [建立和管理頻道](managing-channels.md)
* [建立和管理位置](managing-locations.md)
* [建立和管理顯示區](managing-displays.md)
