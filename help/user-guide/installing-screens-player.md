---
title: 安装 Screens 播放器
seo-title: Installing Screens Player
description: 請依照本頁所述操作，瞭解如何安裝可用的AEM Screens Player。
seo-description: Installing Screens Player
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: c6506ca62e806ec11d3380d6ac7670bcfcf13adb
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 1%

---

# 安裝AEM Screens Player {#installing-player}

本頁面說明如何安裝AEM Screens播放器。

## 可用的Screens播放器 {#available-players}

AEM Screens播放器適用於Android、Chrome作業系統和Windows。

若要下載 **AEM Screens Player**，請造訪 [AEM 6.5播放器下載](https://download.macromedia.com/screens/) 頁面。

>[!NOTE]
>
>下載最新的播放器後(*.exe*)，然後依照播放器上的步驟完成隨選安裝：
>
>1. 長按左上角以開啟「管理」面板。
>1. 導覽至 **設定** 從左側動作功能表，並輸入AEM執行個體的位置地址 **伺服器** 並按一下 **儲存**.
>1. 按一下 **註冊** 左側動作選單的連結，以及完成裝置註冊程式的下列步驟。


## 基本播放監視 {#playback-monitoring}

播放器會報告各種播放量度，每種 `ping` 預設為30秒。 根據這些量度，我們可以偵測各種邊緣情況，例如停滯體驗、空白畫面和排程問題。 這可讓我們瞭解裝置上的問題並加以疑難排解，進而加快與您進行調查和採取修正措施。

AEM Screens播放器中的基本播放監視可讓我們：

* 遠端監視（如果播放器正確播放內容）。

* 改善對空白畫面或欄位中中斷體驗的反應性。

* 降低向一般使用者顯示中斷體驗的風險。

### 瞭解屬性 {#understand-properties}

下列屬性包含在每個 `ping`：

| 属性 | 描述 |
|---|---|
| ID {string} | 播放器識別碼 |
| activeChannel {string} | 目前播放頻道路徑，或若未排程則為空值 |
| activeElements {string} | 以逗號分隔的字串，目前所有播放順序頻道中可見的元素（如果是多區域配置，則為多個） |
| isDefaultContent {boolean} | 如果播放頻道被視為預設或備援頻道（即優先順序為1且無排程），則為true |
| hasContentChanged {boolean} | 如果內容在過去5分鐘內變更，則為真，否則為假 |
| lastContentChange {string} | 上次內容變更的時間戳記 |

>[!NOTE]
>或者，您也可以從播放器偏好設定（啟用播放監視）啟用更進階的屬性，即：
>|屬性|說明|
>|—|—|
>|isContentRendering {boolean}|true (如果GPU能確認它正在播放實際內容（根據畫素分析）|

### 限制 {#limitations}

基本播放監視的少數限制列於下方：

* 播放器會向伺服器報告自己的播放狀態，因此需要使用中的連線。

* 此 `isContentRendering` 檢查GPU的屬性目前資源過於密集，預設無法啟用，且需要從播放器偏好設定中明確選擇加入。 建議不要在生產環境中與影片結合使用。

* 此功能僅支援序列頻道，尚未涵蓋互動式頻道(SPA)使用案例。

* 這些量度尚未完全開放給我們的客戶，我們正在努力在不久的將來啟用類似控制面板的報告和警報機制。

### 其他资源 {#additional-resources}

如需深入資訊，請參閱下列主題：

* 若要下載Android Player，請造訪 **Google Play**. 若要瞭解如何實作Android Watchdog，請參閱 [實作Android播放器](implementing-android-player.md).

* 若要實作Chrome OS Player，請參閱 [Chrome管理主控台](implementing-chrome-os-player.md) 以取得詳細資訊。

* 若要設定AEM Screens Windows Player，請參閱 [實作Windows Player](implementing-windows-player.md).
