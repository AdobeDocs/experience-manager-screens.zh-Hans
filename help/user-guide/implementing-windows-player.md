---
title: 實作Windows 10 Player
seo-title: Implementing Windows 10 Player
description: 請依照此頁面瞭解如何設定AEM Screens Windows 10播放器。
seo-description: Follow this page to learn about configuring AEM Screens Windows 10 player.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: 97bc64ce3c01ac2de301b17bf9f8610662d45f88
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 1%

---

# 實作Windows 10 Player {#implementing-windows-player}

本節說明如何設定AEM Screens Windows 10播放器。 它提供設定檔和可用選項的資訊，以及開發和測試使用哪些設定的建議。

## 安裝Windows Player {#installing-windows-player}

若要實作適用於AEM Screens的Windows Player，請安裝適用於AEM Screens的Windows Player。

造訪 [**AEM 6.5播放器下載**](https://download.macromedia.com/screens/) 頁面。

>[!NOTE]
>Windows Player中沒有視窗模式。 永遠是全熒幕模式。

### 設定AEM Screens 6.5.5 Service Pack的環境 {#fp-environment-setup}

>[!NOTE]
>如果您使用AEM Screens 6.5.5 Service Pack，則必須設定Windows Player環境。

設定 **登入權杖Cookie的SameSite屬性** 從 **鬆散** 至 **無** 從 **Adobe Experience Manager Web主控台設定** 在所有AEM作者和發佈執行個體上。

应遵循以下步骤：

1. 導覽至 **Adobe Experience Manager Web主控台設定** 使用 `http://localhost:4502/system/console/configMgr`.

1. 搜尋 *AdobeGranite權杖驗證處理常式*.

1. 設定 **登入權杖Cookie的SameSite屬性** 從 **鬆散** 至 **無**.
   ![图像](/help/user-guide/assets/granite-updates.png)

1. 单击“**保存**”。

### 臨機方法 {#ad-hoc-method}

Ad-Hoc方法可讓您安裝最新的Windows Player (*.exe*)。 造訪 [**AEM 6.5播放器下載**](https://download.macromedia.com/screens/) 頁面。

下載應用程式後，請依照播放器上的步驟完成隨選安裝：

1. 長按左上角以開啟「管理」面板。
1. 導覽至 **設定** 從左側動作選單中輸入您要連線的AEM執行個體的位置（位址），然後按一下 **儲存**.
1. 導覽至 **裝置** **註冊** 從左側動作選單連結以檢查裝置註冊程式的狀態。

>[!NOTE]
>
>如果 **州** 是 **已註冊**，您會注意到 **裝置ID** 欄位將會填入。
>
>如果 **州** 是 **未註冊**，您可以使用 **Token** 以註冊裝置。

## 命名Windows Player {#name-windows}

您可以為Windows播放器指派好記的裝置名稱，藉此將指派的裝置名稱傳送至Adobe Experience Manager (AEM)。 此功能不僅可讓您為Windows播放器命名，也可讓您輕鬆指派適當的內容。

>[!NOTE]
>您只能在註冊之前選擇播放器名稱。 播放器註冊後，就無法再變更播放器名稱。

請依照下列步驟，在Windows Player中設定名稱：

1. 按一下 **開始** —> **執行**
1. 輸入 `system.cpl`
1. 使用電腦名稱標籤來設定電腦的主機名稱

## 變更Windows Installer中的預設選項 {#changing-default-options}

請詳閱本節，瞭解如何變更Windows Installer中的預設選項及可用的自訂清單。

## 使用CLI安裝(PowerShell) {#install-powershell}

1. 建立自訂位置 **專用** 例如，對於Screens播放器：
   `C:\Users\User\screens-player`)
1. 安装
   `aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\screens-player`
1. 打开
   `Start-Process C:\Users\User\screens-player\AEMScreensPlayer.exe`

**示例**

```shell
C:\Users\User\Downloads> mkdir screens-player

C:\Users\User\Downloads> .\aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\Downloads\screens-player

C:\Users\User\Downloads> Start-Process C:\Users\User\Downloads\screens-player\AEMScreensPlayer.exe
```

## 大量註冊Windows Player {#bulk-registration}

實作Windows Player時，您不需要手動設定每個單一播放器。 您可以在配置JSON檔案經過測試並準備好部署後進行更新。

此設定會確保所有播放器都會偵測到設定檔案中提供的相同伺服器。 您仍然必須手動註冊每個播放器。

請依照下列步驟設定Windows 10 Player：

1. 安裝Windows Player。
1. 在下方尋找設定檔 ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. 使用以下資訊更新設定JSON，然後將相同的資料夾複製到播放器所在的所有系統。

### 原則屬性 {#policy-attributes}

下表摘要列出原則屬性，並提供原則JSON範例以供參考：

| **原則名稱** | **用途** |
|---|---|
| 服务器 | Adobe Experience Manager (AEM)伺服器的URL。 |
| 分辨率 | 裝置的解析度。 |
| rebootSchedule | 重新啟動播放器的排程。 |
| enableAdminUI | 啟用管理員UI以在網站上設定裝置。 完成設定並投入生產後，請設為false。 |
| enableOSD | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 在完全設定完畢並投入生產後，請考慮將設定為false 。 |
| enableActivityUI | 啟用以顯示活動的進度，例如下載和同步。 啟用以進行疑難排解，並在完全設定後和生產環境中停用。 |

#### 原則JSON檔案範例 {#example-policy-json-file}

```
{
    "server": "https://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

## 啟用資訊站模式 {#enabling-kiosk-mode}

部署Windows Player時，請務必啟用Kiosk模式，以免其他應用程式或工作列出現在Windows案頭上。

>[!CAUTION]
>
>Adobe建議使用裝置管理解決方案來啟用Windows專用的Kiosk。 如果您沒有裝置管理解決方案可啟用Kiosk模式，請遵循下列步驟。 此方法使用Windows 10企業版和Edu中可用的殼層啟動器功能。 Microsoft針對非UWP應用程式所建議的任何其他方法，也可以套用以啟用Kiosk，尤其是在其他Windows版本上。

請依照下列步驟啟用Kiosk模式：

>[!NOTE]
>
>在依照下列步驟執行之前，請確定您使用的是Windows 10企業版或教育版。

1. 啟用殼層啟動器。

   請參閱區段 ***設定殼層啟動器*** 在 **[殼層啟動器](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** 按Microsoft Windows支援分頁，以取得其他資訊。

1. 建立一個非管理使用者（如果您還沒有的話），以用於Kiosk。 這可以是本機或網域使用者。
1. 從安裝該Kiosk使用者的Windows Player [AEM Screens播放器下載](https://download.macromedia.com/screens/) 頁面。
1. 請參閱 [使用Shell啟動器建立Windows 10資訊站](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) 修改PowerShell指令碼以取得詳細資訊。

   修改PowerShell指令碼，以您所建立的使用者名稱取代使用者名稱。 請確定應用程式可執行檔的路徑正確。 這會將自訂殼層設定為Kiosk使用者的Windows Player應用程式，並將其他使用者的預設設定為explorer.exe。

1. 以管理員身分執行PowerShell指令碼。
1. 重新開機並以Kiosk使用者身分登入，播放器應用程式應立即啟動。

### 疑难解答 {#troubleshooting}

如果您以Kiosk使用者身分登入時出現黑色熒幕，表示您可能未正確指定Windows Player可執行檔的路徑。 以管理員身分重新登入，然後驗證並重新執行指令碼。

Windows Player的預設安裝路徑為：

***C:\Users\&amp;lt；您的使用者>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

連結中的範例指令碼將會啟用和停用自訂殼層。 因此，您可能需要將指令碼一分為二，並啟用/停用以下適用的行：

>[!NOTE]
>
>在某些Windows環境中，PowerShell指令碼可能受到原則（特別是未簽署的指令碼）的限制。 若要執行指令碼，您可能需要暫時停用並重新啟用此限制以執行指令碼。 開啟PowerShell視窗並使用這些指令。
>
>*set-executionpolicy不受限制*  — 暫時移除限制
>
>*set-executionpolicy已限制*  — 在執行指令碼後重新啟用限制

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### 使用Screens遙控器 {#using-remote-control}

AEM Screens提供遠端控制功能。 若要進一步瞭解此功能，請前往這裡： [熒幕遙控器](implementing-remote-control.md)