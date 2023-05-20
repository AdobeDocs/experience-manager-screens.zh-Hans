---
title: 實作Chrome OS Player
seo-title: Implementing Chrome OS Player
description: 請詳閱本頁面，瞭解如何使用Chrome管理主控台實作Chrome作業系統播放器。
seo-description: Follow  this page to learn about the implementation of the Chrome OS Player using the Chrome Management Console.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 0%

---

# 實作Chrome OS Player  {#implementing-chrome-os-player}

本節說明如何使用Chrome管理主控台實作Chrome作業系統播放器。

## 使用Chrome管理主控台 {#using-chrome-management-console}

請依照下列步驟設定Chrome管理主控台：

1. 註冊Chrome管理主控台。 您必須取得Chrome管理主控台的授權。 連絡人 [Google支援](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995) 管理Chrome裝置設定以取得詳細資訊。
1. 將您的Chrome作業系統裝置註冊至網域，等待15分鐘，讓裝置與Chrome管理主控台同步。 若要進一步瞭解如何註冊Chrome裝置，請按一下 [此處](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. Chrome播放器可在Chrome線上應用程式商店中取得。

>[!NOTE]
>
>建議使用裝置管理解決方案（例如Chrome管理主控台）來部署及管理Chrome作業系統裝置。 雖然如此，本檔案提供Chrome管理主控台的實作，但其他廠商也聲稱提供類似的功能。 請連絡裝置管理軟體的廠商。

## 命名Chrome作業系統播放器 {#name-chrome}

您可以為Chrome播放器指派好記的裝置名稱，藉此將指派的裝置名稱傳送至Adobe Experience Manager (AEM)。 此功能不僅可讓您為Chrome播放器命名，也可讓您輕鬆指派適當內容。

>[!NOTE]
>您只能在註冊之前選擇播放器名稱。 播放器註冊後，就無法再變更播放器名稱。

請依照下列步驟，在Chrome播放器中設定名稱：

1. 您可以選擇允許AV整合經銷商或IT管理員設定資產ID和位置，作為企業註冊的一部分。

   ![图像](/help/user-guide/assets/chrome-device/chrome1.png)

1. 當您註冊裝置時，畫面會顯示選項。

   ![图像](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. 您可以將資產ID設定為企業註冊的一部分以及在Chrome管理主控台中。

   ![图像](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Chrome播放器必須在企業註冊中註冊，且Chrome播放器必須透過Chrome管理主控台部署，否則資產ID會傳回空白（例如chrome作為擴充功能）。 裝置名稱僅在註冊時記錄。 Adobe Experience Manager (AEM)不會擷取未來的變更。

### 啟用資訊站模式 {#enabling-kiosk-mode}

請依照下列步驟啟用Kiosk模式：

1. 登入Chrome開發人員主控台。

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. 瀏覽至 **裝置管理** > **Chrome管理** > **裝置設定**.
1. 向下捲動至 **資訊站設定** 並按一下 **管理資訊站應用程式**.

   ![資訊站](assets/kiosk.png)

1. 從Chrome線上應用程式商店選取AEM Screens Player。

   >[!NOTE]
   >
   >最近發佈的應用程式可能需要約15分鐘才會出現在此清單中。

1. 選取 **AEM Screens Player** 從 **自動啟動資訊站應用程式** 下拉式清單。

   視網路而定，變更可能需要幾分鐘才會生效。 建議重新啟動。

#### 正在檢查遠端裝置狀態 {#checking-remote-device-status}

1. 登入Chrome開發人員主控台。
1. 瀏覽至 **裝置管理** > **Chrome裝置** 並選取您要控制的裝置。
1. 按一下 **系統活動和疑難排解**.
1. 檢查 **重新開機裝置** 和 **熒幕擷取** 裝置的屬性。 您也可以檢查裝置狀態和健康情況資訊。

>[!NOTE]
>
>請注意，這些設定可能會在裝置註冊後幾分鐘啟用。 每個選項都可能隨著時間啟用。

### 設定Chrome作業系統播放器的遠端設定 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player是啟用Kiosk的應用程式，也可啟用Chrome作業系統播放器的遠端原則設定。

請依照下列步驟設定播放器的各種選項：

1. 登入Chrome管理主控台。
1. 按一下 **裝置管理** > **Chrome管理** > **應用程式管理**. AEM Screens Player會顯示在清單中。
1. 按一下應用程式 **AEM Screens Player**.
1. 按一下 **資訊站設定** 並選取您的組織(*若使用測試環境*)。
1. 按一下 **上傳設定檔** 並上傳設定原則(*Json檔案*)。
1. 单击“**保存**”。您必須重新啟動裝置才能同步原則。

>[!NOTE]
>
>重新啟動裝置以同步處理原則變更。

#### 原則JSON檔案範例 {#example-policy-json-file}

```java
{
  "server": {
    "Value": "https://aemscreensdemo.adobeitc.com"
  },
  "resolution": {
    "Value": "auto"
  },
  "rebootSchedule": {
    "Value": "at 4:00am"
  },
  "enableAdminUI": {
    "Value": true
  },
  "enableOSD": {
    "Value": true
  },
  "enableActivityUI": {
    "Value": true
  }
}
```

### 原則屬性和用途 {#policy-attributes-and-purpose}

下表總結了這些原則及其功能。

| **原則名稱** | **用途** |
|---|---|
| *服务器* | Adobe Experience Manager伺服器的URL |
| *分辨率* | Chrome作業系統裝置的解析度 |
| *rebootSchedule* | 重新開機Chrome播放器的排程 |
| *enableAdminUI* | 啟用管理員UI，讓技術人員在現場設定裝置。 完成設定並投入生產後，請設為false。 |
| *enableOSD* | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 在完全設定完畢並投入生產後，請考慮將設定為false 。 |
| *enableActivityUI* | 啟用以顯示活動的進度，例如下載和同步。 啟用以進行疑難排解，並在完全設定後和生產環境中停用。 |

>[!NOTE]
>
>原則設定會嚴格執行，不會手動在播放器的管理UI覆寫。 若要允許特定原則的手動播放器設定，請勿在 ***原則設定，*** 例如，如果要允許手動設定重新開機排程，請勿指定機碼 ***rebootSchedule*** 在原則設定中。

### 使用Screens遙控器 {#using-remote-control}

AEM Screens提供遠端控制功能。 若要進一步瞭解此功能，請前往這裡： [熒幕遙控器](implementing-remote-control.md)
