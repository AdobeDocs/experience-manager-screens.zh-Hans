---
title: AEM Screens通知服務
seo-title: AEM Screens Notifications Service
description: 請詳閱本頁，瞭解更多關於如何監視裝置活動的資訊。
seo-description: Follow this page to learn more about how you can monitor device activity.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# AEM Screens通知服務{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens通知服務***，說明可監控裝置活動的功能。

本節涵蓋下列主題：

* **概述**
* **正在設定電子郵件設定**
* **電子郵件通知**
* **範例使用案例**

>[!CAUTION]
>
>此AEM Screens功能僅在您已安裝AEM 6.3.2 Feature Pack 3或AEM 6.4.1 Screens Feature Pack 1時可用。
>
>若要存取此Feature Pack，您必須聯絡Adobe支援並要求存取權。 一旦您擁有許可權，就可以從「封裝共用」下載它。

## 概述 {#overview}

***AEM Screens通知服務***，可讓管理員在AEM screens播放器未ping通可設定時段時收到電子郵件。

此服務可在OSGi Web主控台中設定。

## 正在設定電子郵件設定 {#configuring-email-settings}

請依照下列步驟設定電子郵件通知設定：

1. 開啟 **Adobe Experience Manager Web主控台設定**.
1. 開啟 **Screens裝置電子郵件監控服務**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 定義下列欄位以設定電子郵件的設定：

   **裝置路徑** 輸入您要監視的畫面專案的路徑。 路徑通常為 `/home/users/screens/<Name of your project>`.

   例如，如果您的專案為 **We.Retail**，您會將專案路徑用作 ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >指定裝置使用者所在的專案路徑。

   **排程頻率** 指定此監視器應傳送電子郵件的時間（例如，下午5:00或17:00）或頻率（例如，1）。

   **Ping逾時** 這會指定間隔，以分鐘為單位，之後裝置應視為無法連線。

   **SMTP伺服器** 指定用於傳送電子郵件的SMTP伺服器。

   **SMTP連線埠** 輸入SMTP連線埠。

   **使用TLS** 傳輸層安全性(TLS)可讓您使用與SMTP伺服器的安全通訊。

   建議使用TLS來安全地連線到公司郵件伺服器。 請洽詢您的郵件管理員以取得適當的值。

   **使用者名稱** 指定傳送電子郵件的使用者名稱。

   **密碼** 指定傳送電子郵件的密碼。

   **收件者** 指定收件者的電子郵件地址。

   >[!NOTE]
   >
   >您只能輸入一個電子郵件地址。 若要傳送大量電子郵件，請建立群組或通訊群組清單以及相關使用者。

1. 按一下 **儲存** 若要透過電子郵件為您的AEM Screens裝置設定監視器活動。

## 電子郵件通知 {#email-notification}

設定電子郵件通知的設定後，您將會收到電子郵件通知，其中包含報告為非使用狀態的實際裝置的連結。

存取該連結會直接將您導覽至裝置控制面板。

只有當至少一個裝置在指定的ping逾時期間尚未偵測，且在產生電子郵件時仍未偵測，才會傳送電子郵件。

### 範例使用案例 {#example-use-cases}

以下範例說明一些案例，以供在Screens裝置電子郵件監視服務中設定屬性時參考。

**案例1**：

如果您將排程頻率設定為凌晨1:00，並將ping逾時設定為60，那麼如果您的Screens裝置在正午12:00到正午1:00之間未執行ping，則您會收到電子郵件通知，確認裝置處於非使用狀態。

**案例2**：

如果您將排程頻率設為1，將ping逾時設為60，則如果您的Screens裝置在一天的任何特定時間都未執行一次ping動作，您會收到電子郵件通知，確認裝置未使用中。
