---
title: 實作Android Player
seo-title: Implementation of Android Player
description: 請詳閱本頁，瞭解Android Watchdog的實作，這是將播放器從當機復原的解決方案。
seo-description: Follow this page to learn implementation of Android Watchdog, a solution to recover the player from crashes.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---

# 實作Android Player {#implementing-android-player}

本節說明如何設定Android播放器。 它提供設定檔和可用選項的資訊，以及開發和測試使用哪些設定的建議。

此外， **監視程式** 是讓播放器從當機復原的解決方案。 應用程式需要向看門狗服務註冊自己，然後定期傳送訊息給其處於使用中狀態的服務。 如果watchdog服務在規定的時間內沒有收到保持連線訊息，服務會嘗試重新開機裝置以進行完全復原（如果它有足夠的許可權）或重新啟動應用程式。

## 安裝Android Player {#installing-android-player}

若要實作適用於AEM Screens的Android Player，請安裝適用於AEM Screens的Android Player。

造訪 [**AEM 6.5播放器下載**](https://download.macromedia.com/screens/) 頁面。

### 設定AEM Screens 6.5.5 Service Pack的環境 {#fp-environment-setup}

>[!NOTE]
>如果您使用AEM Screens 6.5.5 Service Pack，必須設定Android播放器的環境。

設定 **登入權杖Cookie的SameSite屬性** 從 **鬆散** 至 **無** 從 **Adobe Experience Manager Web主控台設定** 在所有AEM作者和發佈執行個體上。

应遵循以下步骤：

1. 導覽至 **Adobe Experience Manager Web主控台設定** 使用 `http://localhost:4502/system/console/configMgr`.

1. 搜尋 *AdobeGranite權杖驗證處理常式*.

1. 設定 **登入權杖Cookie的SameSite屬性** 從 **鬆散** 至 **無**.
   ![图像](/help/user-guide/assets/granite-updates.png)

1. 单击“**保存**”。


### 臨機方法 {#ad-hoc-method}

臨機操作方法可讓您安裝最新的Android Player (*.exe*)。 造訪 [**AEM 6.5播放器下載**](https://download.macromedia.com/screens/) 頁面。

下載應用程式後，請依照播放器上的步驟完成隨選安裝：

1. 長按左上角以開啟「管理」面板。
1. 導覽至 **設定** 從左側動作選單中輸入您要連線的AEM執行個體的位置（位址），然後按一下 **儲存**.

1. 導覽至 **裝置** **註冊** 從左側動作選單連結以檢查裝置註冊程式的狀態。

>[!NOTE]
>
>如果 **州** 是 **已註冊**，您會注意到 **裝置ID** 欄位將會填入。
>
>如果 **州** 是 **未註冊**，您可以使用 **Token** 以註冊裝置。

## 實作Android Watchdog {#implementing-android-watchdog}

由於Android的架構，重新啟動裝置需要應用程式具有系統許可權。 要執行此操作，您必須使用製造商的簽署金鑰來簽署應用程式，否則監視器會重新啟動播放器應用程式，而不會重新啟動裝置。

### 使用製造商金鑰的Android應用程式標牌 {#signage-of-android-apks-using-manufacturer-keys}

若要存取Android的某些特殊許可權API，例如 *PowerManager* 或 *HDMIControlService*，您必須使用製造商的金鑰簽署android apk。

>[!CAUTION]
>
>先決條件：
>
>您應先安裝Android SDK，然後再執行下列步驟。

請依照下列步驟，使用製造商的金鑰簽署android應用程式：

1. 從Google Play或下載應用程式 [AEM Screens播放器下載](https://download.macromedia.com/screens/) 頁面
1. 向製造商取得平台金鑰以取得 *pk8* 和 *pem* 檔案

1. 使用「尋找~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;，在android sdk中找到apksigner工具
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. 尋找android sdk中zip對齊工具的路徑
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. 安裝 ***aemscreensaligned.apk*** 使用adb install到裝置

## 瞭解Android監視程式服務 {#android-watchdog-services}

跨Android Watchdog服務是使用實作為Cordova外掛程式 *AlarmManager*.

下圖顯示監視程式服務的實作：

![chlimage_1-31](assets/chlimage_1-31.png)

**1. 初始化** 初始化cordova外掛程式時，會檢查許可權以檢視我們是否有系統許可權，進而檢查是否有「重新開機」許可權。 如果滿足這兩個條件，則會建立擱置的重新開機意圖，否則會建立擱置的重新開機意圖（根據應用程式的啟動活動）。

**2. 保持作用中計時器** 保持連線計時器可用來每15秒觸發一次事件。 在此情況下，您需要取消現有的擱置意圖（重新開機或重新啟動應用程式），並在未來的60秒內註冊新的擱置意圖（基本上會延遲重新開機）。

>[!NOTE]
>
>在Android中， *AlarmManager* 用於註冊 *pendingIntents* 即使應用程式當機且其警報傳送與API 19 (Kitkat)不準確，仍可執行。 在計時器的間隔和 *AlarmManager的* *pendingIntent的* 警報。

**3. 應用程式當機** 在當機時，在AlarmManager中註冊的pendingIntent for Reboot不再重設，因此會執行應用程式重新開機或重新啟動（取決於初始化cordova外掛程式時可用的許可權）。

## 大量布建Android Player {#bulk-provision-android-player}

大量推出Android播放器時，需要布建播放器以指向AEM執行個體，以及設定其他屬性，而不需在管理員UI中手動輸入。

>[!NOTE]
>Android播放器42.0.372提供此功能。

請依照下列步驟，在Android播放器中允許大量布建：

1. 以名稱建立設定JSON檔案 `player-config.default.json`.
請參閱 [範例JSON原則](#example-json) 以及說明各種 [原則屬性](#policy-attributes).

1. 使用MDM、ADB或Android Studio檔案總管將此原則JSON檔案拖放至 *sdcard* Android裝置上的資料夾。

1. 部署檔案後，請使用MDM安裝播放器應用程式。

1. 播放器應用程式啟動時，會讀取此設定檔，並指向適用的AEM伺服器，以便登入並接著加以控制。

   >[!NOTE]
   >此檔案為 *唯讀* 首次啟動應用程式，且無法用於後續設定。 如果在卸除設定檔案之前啟動播放器，只需在裝置上解除安裝並重新安裝應用程式即可。

### 原則屬性 {#policy-attributes}

下表摘要列出原則屬性，並提供原則JSON範例以供參考：

| **原則名稱** | **用途** |
|---|---|
| *服务器* | Adobe Experience Manager伺服器的URL。 |
| *分辨率* | 裝置的解析度。 |
| *rebootSchedule* | 重新開機的排程適用於所有平台。 |
| *enableAdminUI* | 啟用管理員UI以在網站上設定裝置。 設定為 *false* 完成設定並投入生產後。 |
| *enableOSD* | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 考慮將設定為 *false* 完成設定並投入生產後。 |
| *enableActivityUI* | 啟用以顯示活動的進度，例如下載和同步。 啟用以進行疑難排解，並在完全設定後和生產環境中停用。 |
| *enableNativeVideo* | 啟用以在視訊播放中使用原生硬體加速（僅限Android）。 |

### 範例JSON原則 {#example-json}

```java
{
  "server": "https://author-screensdemo.adobecqms.net",
"device": "",
"user": "",
"password": "",
"resolution": "auto",
"rebootSchedule": "at 4:00 am",
"maxNumberOfLogFilesToKeep": 10,
"logLevel": 3,
"enableAdminUI": true,
"enableOSD": true,
"enableActivityUI": false,
"enableNativeVideo": false,
"enableAutoScreenshot": false,
"cloudMode": false,
"cloudUrl": "https://screens.adobeioruntime.net",
"cloudToken": "",
"enableDeveloperMode": true
}
```

>[!NOTE]
>所有Android裝置都有 *sdcard* 資料夾(無論是 *sdcard* 是否插入。 部署時，此檔案會與「下載」資料夾位於相同層級。 有些MDM如Samsung Knox可能會參考此內容 *sdcard* 資料夾位置為 *內部儲存*.

## 使用企業行動管理大量布建Android Player {#bulk-provisioning}

大量部署Android播放器時，手動向AEM註冊每個單一播放器會變得繁瑣。 強烈建議使用EMM （企業行動管理）解決方案，例如VMWare Airwatch、MobileIron或Samsung Knox，從遠端布建和管理您的部署。 AEM Screens Android播放器支援業界標準的EMM AppConfig，以允許遠端布建。

## 命名Android Player {#name-android}

您可以為Android播放器指派好記的裝置名稱，藉此將指派的裝置名稱傳送至Adobe Experience Manager (AEM)。 此功能不僅可讓您為Android播放器命名，也可讓您輕鬆指派適當內容。

>[!NOTE]
>您只能在註冊之前選擇播放器名稱。 播放器註冊後，就無法再變更播放器名稱。

請依照下列步驟，在Android Player中設定名稱：

1. 導覽至 **設定** —> **關於裝置**
1. 編輯並設定您的裝置名稱，以命名您的Android播放器

### 使用Enterprise Mobility Management實作Android Player的大量布建 {#implementation}

請依照下列步驟，在Android Player中允許大量布建：

1. 確認您的Android裝置支援Google Play服務。
1. 使用您最愛的支援AppConfig的EMM解決方案註冊您的Android播放器裝置。
1. 登入EMM主控台，並從Google Play提取AEM Screens Player應用程式。
1. 選取受管理的組態或相關選項。
1. 您現在應該會看到可設定的播放器選項清單，例如伺服器和大量註冊代碼。
1. 設定這些引數、儲存原則，並將其部署至裝置。

   >[!NOTE]
   >裝置應該會收到應用程式和設定，並指向具有所選設定的正確AEM伺服器。 如果您選擇設定大量註冊代碼，並保留與AEM中設定的相同，則播放器應該能夠自動註冊自身。 如果您已設定預設顯示，它也可以下載並顯示某些預設內容（稍後可視您的方便性進行變更）。

此外，您也應該向EMM供應商洽詢AppConfig支援。 最受歡迎的內容，例如 [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)， [Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)， [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)， [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)， [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) 和 [Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) 其他支援此產業標準。

### 使用Screens遙控器 {#using-remote-control}

AEM Screens提供遠端控制功能。 若要進一步瞭解此功能，請前往這裡： [熒幕遙控器](implementing-remote-control.md)
