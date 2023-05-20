---
title: 疑難排解裝置控制中心
seo-title: Monitoring Screens
description: 請依照此頁面，使用Device儀表板來監視和疑難排解Screens播放器活動和裝置的效能。
seo-description: Follow this page to monitor and troubleshoot performance for your Screens player activity and device usingtheDevice dashboard.
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 2%

---

# 疑難排解裝置控制中心 {#troubleshooting-device-control-center}

您可以使用「裝置」儀表板來監視和疑難排解Screens播放器活動和裝置的效能。 此頁面提供如何監視和疑難排解Screens播放器和指派裝置的感知效能問題的相關資訊。

## 從Device Control Center進行監控和疑難排解 {#monitor-and-troubleshoot-from-device-control-center}

您可以使用Device Dashboard監控活動，進而疑難排解Screens播放器的問題。

### 裝置控制面板 {#device-dashboard}

請依照下列步驟導覽至裝置控制面板：

1. 從您的專案導覽至裝置控制面板，例如， ***測試專案*** —> ***裝置***.

   選取 **裝置** 和 **裝置管理員** 動作列中的。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 清單會顯示指派和未指派的裝置，如下圖所示。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. 選取裝置(**NewTestDevice**)並按一下 **儀表板** 動作列中的。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. 此頁面會顯示裝置資訊、活動，以及可讓您監視裝置活動和功能的裝置詳細資訊。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### 監視裝置活動 {#monitor-device-activity}

此 **活動** 面板會以時間戳記顯示screens播放器的最後一次ping。 上次ping對應於裝置上次連線伺服器的時間。

![chlimage_1](assets/chlimage_1.png)

此外，按一下 **收集記錄** 從的右上角 **活動** 面板以檢視播放器的記錄檔。

### 更新裝置詳細資料 {#update-device-details}

檢查 **裝置詳細資料** 面板可檢視裝置IP、儲存空間使用量、韌體版本和播放器運作時間。

![chlimage_1-1](assets/chlimage_1-1.png)

此外，按一下 **清除快取** 和 **更新** 以清除裝置的快取並更新 [韌體](screens-glossary.md) 版本（分別來自此面板）。

此外，按一下 **...** 從右上角 **裝置詳細資料** 面板以重新啟動或重新整理播放器的狀態。

![chlimage_1-2](assets/chlimage_1-2.png)

### 更新裝置資訊 {#update-device-information}

檢查 **裝置資訊** 面板以檢視設定更新、裝置型號、裝置作業系統和殼層資訊。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

此外，按一下(**...**)，以檢視屬性或更新裝置。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

按一下 **屬性** 若要檢視 **裝置屬性** 對話方塊。 您可以編輯裝置標題或選擇設定更新的選項，如下所示 **手動** 或 **自動**.

>[!NOTE]
>
>若要進一步瞭解與裝置的自動或手動更新相關聯的事件，請參閱區段 ***從裝置儀表板自動與手動更新*** 在 [管理管道](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### 檢視播放器熒幕擷圖 {#view-player-screenshot}

您可以從裝置檢視播放器熒幕擷圖 **播放器熒幕擷圖** 面板。

按一下(**...**)，然後選取「 」 **重新整理熒幕擷圖** 以檢視執行中播放器的快照。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 管理偏好設定 {#manage-preferences}

此 **偏好設定** 面板可讓使用者變更的偏好設定 **管理員UI**， **頻道切換器**、和 **遠端偵錯** 裝置的。

>[!NOTE]
>若要進一步瞭解這些選項，請參閱 [AEM Screens Player](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

此外，按一下 **設定** 從右上角更新裝置偏好設定。 您可以更新下列偏好設定：

* **服务器 URL**
* **解决方法**
* **重新启动计划**
* **最大數量 要保留的記錄檔**
* **日志级别**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>您可以選取下列任一「記錄」層級：
>* **禁用**
>* **调试**
>* **信息**
>* **警告**
>* **错误**


![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## 疑難排解OSGi設定 {#troubleshoot-osgi-settings}

您必須啟用空白反向連結，才能讓裝置將資料張貼至伺服器。 例如，如果停用空白反向連結屬性，裝置就無法張貼熒幕擷圖。

目前，其中部分功能僅適用於 *Apache Sling反向連結篩選器允許空白* 在OSGi設定中啟用。 儀表板可能會顯示警告，指出安全性設定可能會阻止這些功能的部分功能運作。

請依照下列步驟，啟用Apache Sling查閱者篩選條件允許空白

1. 導覽至 **Adobe Experience Manager Web主控台設定**，也就是說， `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. 檢查 **allow.empty** 選項。
1. 单击“**保存**”。

![chlimage_1-3](assets/chlimage_1-3.png)

### 推荐 {#recommendations}

下節建議監控網路連結、伺服器和播放器，以瞭解運作狀況並對問題做出反應。

AEM提供下列專案的內建監控：

* *心率* 每5秒顯示一次，指出AEM Screens Player運作中。
* *熒幕擷圖* 從「播放器」中，顯示目前顯示在「播放器」上的內容。
* 此 *AEM Screens播放器韌體* 版本已安裝在播放器上。
* *可用儲存空間* 在播放器上。

使用第三方軟體進行遠端監控的Recommendations：

* 播放器上的CPU使用量。
* 檢查AEM Screens Player程式是否正在執行。
* 遠端重新啟動/重新開機播放器。
* 即時通知。

建議以可讓遠端登入診斷問題和重新啟動播放器的方式部署播放器硬體及作業系統。

#### 其他资源 {#additional-resources}

另請參閱 [視訊播放設定和疑難排解](troubleshoot-videos.md) 若要對頻道中播放的視訊進行除錯和疑難排解，請執行下列動作。
