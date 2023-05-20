---
title: 設定和部署AEM Screens
seo-title: Configuring and Deploying Screens
description: AEM Screens播放器適用於Android、Chrome作業系統、iOS和Windows。 此頁面說明AEM Screens的設定和部署，並概述播放器裝置的h/w選擇准則。
seo-description: The AEM Screens player is available for Android, Chrome OS, iOS, and Windows. This page describes the configuration and deployment of AEM Screens and also summarizes the h/w selection guidelines for player device.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 0%

---

# 設定和部署AEM Screens {#configuring-and-deploying-aem-screens}

本頁面說明如何在您的裝置上安裝和設定Screens播放器。

## 伺服器設定 {#server-configuration}

>[!NOTE]
>
>**重要**:
>
>AEM Screens播放器未使用跨網站請求偽造(CSRF)權杖。 因此，為了設定和AEM伺服器以準備好用於AEM Screens，請允許空白反向連結以略過反向連結篩選。

## 健康情況檢查架構 {#health-check-framework}

健康情況檢查架構可讓使用者在執行AEM Screens專案之前，檢查是否已設定兩個必要的設定。

它可讓使用者驗證以下兩個設定檢查以執行AEM Screens專案，即檢查以下兩個篩選器的狀態：

1. **允許空的反向連結**
2. **https**

請依照下列步驟，檢查這兩個重要設定是否已為AEM Screens啟用：

1. 導覽至 [Adobe Experience Manager Web主控台Sling健康狀態檢查](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![資產](assets/health-check1.png)


2. 按一下 **執行選取的運行狀況檢查** 以對上述兩個屬性執行驗證。

   如果兩個篩選器都啟用，則 **Screens設定健康情況服務** 顯示 **結果** 作為 **確定** 將兩個設定都設為啟用。

   ![資產](assets/health-check2.png)

   如果停用其中一個或兩個篩選器，則會顯示給使用者的警報，如下圖所示。

   下列警報會顯示兩個篩選器皆已停用的情況：
   ![資產](assets/health-check3.png)

>[!NOTE]
>
>* 若要啟用 **Apache Sling查閱者篩選器**，請參閱 [允許空的反向連結請求](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* 若要啟用 **HTTP** 服務，請參閱 [Apache Felix Jetty型HTTP服務](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).


### 前提条件 {#prerequisites}

以下要點可協助您設定和AEM伺服器，以準備好用於AEM Screens。

#### 允許空的反向連結請求 {#allow-empty-referrer-requests}

1. 導覽至 **Adobe Experience Manager Web主控台設定** 透過AEM執行個體 — >槌子圖示 — > **作業** —> **網頁主控台**.

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web主控台設定** 隨即開啟。 搜尋Sling反向連結。

   若要搜尋Sling查閱者屬性，請按 **Command+F** 的 **Mac** 和 **Control+F** 的 **Windows**.

1. 檢查 **允許空白** 選項，如下圖所示。

   ![图像](assets/config/empty-ref2.png)

1. 按一下 **儲存** 以啟用Apache Sling反向連結篩選允許空白。


#### Apache Felix Jetty型HTTP服務 {#allow-apache-felix-service}

1. 導覽至 **Adobe Experience Manager Web主控台設定** 透過AEM執行個體 — >槌子圖示 — > **作業** —> **網頁主控台**.

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web主控台設定** 隨即開啟。 搜尋Apache Felix Jetty型HTTP服務。

   若要搜尋此屬性，請按 **Command+F** 的 **Mac** 和 **Control+F** 的 **Windows**.

1. 檢查 **啟用HTTP** 選項，如下圖所示。

   ![图像](assets/config/config-1.png)

1. 按一下 **儲存** 以啟用 *http* 服務。

#### 啟用AEM Screens的觸控式UI {#enable-touch-ui-for-aem-screens}

AEM Screens需要TOUCH UI，無法搭配Adobe Experience Manager (AEM)的CLASSIC UI使用。

1. 導覽至 *&lt;yourauthorinstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. 確保 **預設編寫UI模式** 設為 **觸控**，如下圖所示

或者，您也可以使用yourAuthorInstance執行相同的設定 *->* 工具（槌子圖示） -> **作業** -> **網頁主控台** 並搜尋 **WCM編寫UI模式服務**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>您一律可以使用使用者偏好設定為特定使用者啟用傳統UI。

#### NOSAMPLECONTENT執行模式中的AEM {#aem-in-nosamplecontent-runmode}

在生產環境中執行AEM會使用 **NOSAMPLECONTENT** 執行模式。 移除 *X-Frame-Options=SAMEORIGIN* 標題（在其他回應標題區段中）來自

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`。

這是AEM Screens Player播放線上頻道所必需的。

#### 密碼限制 {#password-restrictions}

包含對下列專案的最新變更： ***DeviceServiceImpl***，您不必移除密碼限制。

您可以設定 ***DeviceServiceImpl*** 從下列連結為screens裝置使用者建立密碼時啟用密碼限制：

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

請依照下列步驟進行設定 ***DeviceServiceImpl***：

1. 導覽至 **Adobe Experience Manager Web主控台設定** 透過AEM執行個體 — >槌子圖示 — > **作業** —> **網頁主控台**.

1. **Adobe Experience Manager Web主控台設定** 隨即開啟。 搜尋 *裝置服務*. 若要搜尋屬性，請按 **Command+F** 適用於macOS和 **Control+F** 適用於Microsoft Windows。

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher設定 {#dispatcher-configuration}

若要瞭解如何為AEM Screens專案設定Dispatcher，請參閱 [為AEM Screens專案設定Dispatcher](dispatcher-configurations-aem-screens.md).

#### Java編碼 {#java-encoding}

設定 ***Java編碼*** 轉換為Unicode。 例如， *Dfile.encoding=Cp1252* 將無法運作。

>[!NOTE]
>**建議：**
>建議將HTTPS用於AEM Screens伺服器以供生產使用。
