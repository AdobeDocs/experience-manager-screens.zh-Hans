---
title: Adobe Analytics與AEM Screens整合
seo-title: Adobe Analytics Integration with AEM Screens
description: 請詳閱本頁，瞭解AEM Screens與Adobe Analytics的立即可用整合，並提供您的使用證明。
seo-description: Follow this page to learn about out of the box integration of AEM Screens with Adobe Analytics and provides you with a proof of play.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 92c8c42b-7c1e-4d4a-8662-18c99666e9c6
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 1%

---

# Adobe Analytics與AEM Screens整合 {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>此AEM Screens功能僅在您已安裝AEM 6.4.2 Feature Pack 2或AEM 6.3.3 Feature Pack 4的最低版本時可用。

>[!NOTE]
>
>若要存取這兩個Feature Pack，您必須聯絡Adobe支援並請求存取權。 您可以從以下網址下載AEM Screens的最新Feature Pack： [軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。

本節涵蓋下列主題：

* **概述**
* **架構詳細資料**
* **設定屬性**

## 概述 {#overview}

***AEM Screens*** 運用Adobe Analytics，可達成市場上獨一無二的功能：跨管道分析，協助將位置中顯示的內容與其他資料來源建立關聯。

AEM Screens提供與Adobe Analytics的現成整合，並為您提供播放證明。

本節說明以下連線AEM Screens專案與Adobe Analytics的功能：

* 允許依裝置提供播放報告證明
* 允許依資產提供播放報表的證明
* 確保擷取所有播放器事件並加上時間戳記
* 如果播放未連線到網路，請確定所有播放器事件都儲存在本機
* 允許建立回饋迴路，以追蹤播放事件隨時間的變化
* 允許系統根據內容作者定義的成功標準修改內容和版面

因此，Adobe Analytics與AEM Screens的整合會強制執行下列動作 *目標*：

* 實現數位招牌實作的ROI
* 整合Analytics，作為日後收集和分析使用資訊的基礎

## 架構詳細資料 {#architectural-details}

AEM Screens客戶想要瞭解哪些內容在何時顯示，以及顯示的時間長短（彙總）。 這是招牌解決方案的常見功能。 AEM Screens不會建置我們自己的分析，而是會運用Adobe Analytics，而我們可以藉此達成市場上獨一無二的目標：跨管道分析，有助於將位置中顯示的內容與其他資料來源建立關聯。

下列架構圖表說明Adobe Analytics與AEM Screens的整合：

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## 在AEM Screens中啟用Adobe Analytics {#enabling-adobe-analytics-in-aem-screens}

可以從OSGi主控台設定Adobe Analytics設定。

導覽至 **Adobe Experience Manager Web主控台設定** 設定適用於AEM Screens的Adobe Analytics，如下圖所示：

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Screens Analytics：啟用流程 {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>在您設定屬性之前，請聯絡您的Adobe關係管理員以建立票證並取得 **Analytics API金鑰** 和 **Analytics專案** 與AEM Screens搭配使用。

![]()

### 設定屬性 {#configuring-the-properties}

>[!CAUTION]
>
>在您設定屬性之前，請聯絡您的Adobe關係管理員以建立票證並取得 **Analytics API金鑰** 和 **Analytics專案** 與AEM Screens搭配使用。

下表重點說明為AEM Screens設定Adobe Analytics的屬性：

<table>
 <tbody>
  <tr>
   <td><strong>属性</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td><strong>Analytics URL</strong></td>
   <td>用於從播放器發佈分析資料的URL。 <br>
   適用於開發/階段</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>用於生產</em> - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Analytics API金鑰</strong></td>
   <td>用於向Adobe Analytics伺服器驗證的API金鑰（由帳戶管理員提供）。</td>
  </tr>
  <tr>
   <td><strong>Analytics專案</strong></td>
   <td>AEM Screens專案已設定在您的analytics上，用於接收資料（由帳戶管理員提供）。</td>
  </tr>
  <tr>
   <td><strong>环境</strong></td>
   <td><p>中繼或生產環境（選擇中繼或生產）。</p></td>
  </tr>
  <tr>
   <td><strong>Analytics傳送頻率</strong></td>
   <td>從播放器傳送分析資料的頻率（分鐘）。 預設為15分鐘。</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>根據預設， **Analytics傳送頻率** 為15分鐘。

#### 在AEM Screens中使用Adobe Analytics服務 {#using-adobe-analytics-service-in-aem-screens}

此情境會透過韌體和Instrument Screens核心元件中分析服務的REST呼叫叫用Analytics API，以明確建立並傳送特定使用案例的特定事件，同時允許擴充，讓任何自訂訊息都可從自訂開發的頻道傳送到Analytics。

Analytics事件會離線儲存在indexedDB中，並在稍後進行區塊化並傳送至雲端。

>[!NOTE]
>
>若要進一步瞭解 ***排序*** 和 ***事件的標準資料模型***，請參閱 **[為AEM Screens設定Adobe Analytics](configuring-adobe-analytics-aem-screens.md)**.
