---
title: AEM 平台配置
seo-title: AEM Platform Configurations
description: 此頁面說明AEM平台組態
seo-description: The page describes AEM Platform Configurations
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 21%

---

# AEM 平台配置  {#platform-configurations}

>[!NOTE]
>
>此活動的典型利害關係人是AEM實作人員。

請依照下列各節所述，設定AEM平台設定，以開始使用AEM Screens。

## 伺服器設定 {#server-configurations}

若要設定伺服器組態，請參閱 [伺服器設定](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration).

## Author-Publish {#author-publish}

若要設定作者 — 發佈，請參閱 [在AEM Screens中設定作者和發佈](https://helpx.adobe.com/cn/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>如果只有一位作者和一个发布，您只需按照[在 AEM Screens 中配置作者和发布](https://helpx.adobe.com/cn/experience-manager/6-5/screens/using/author-and-publish.html)页面中&#x200B;**设置作者复制代理**&#x200B;下的步骤操作即可。

## Dispatcher 配置 {#dispatcher-configurations}

Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。使用 AEM 的 Dispatcher 还有助于保护 AEM 服务器免受攻击。因此，您可以通过将 Dispatcher 与企业级 Web 服务器结合使用来提高 AEM 实例的安全性。

請參閱 **[適用於AEM Screens的Dispatcher設定](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** 它會重點說明為AEM Screens專案設定Dispatcher的准則。

## 安裝FFMpeg和視訊轉譯 {#installing-ffmpeg}

請依照適當作業系統（通常是RHEL）的步驟安裝FFMpeg：

1. 如果透過啟用EPEL和RPMFusion進行安裝，您可以安裝所有gstreamer轉碼器，以擴大對FFmpeg轉換的支援
1. 如果AAC轉碼器標示為實驗性，ffmpeg轉換將會失敗。 為避免此問題，請在視訊設定檔中新增 — strict -2 (在AEM 6.3中為/etc/dam/video，在AEM 6.4中為/libs/settings/dam/video)
   >[!NOTE]
   >
   > 請注意，-strict -2必須是引數清單中的最後一個引數。 此外，在AEM 6.4中，您需要複製 */libs/settings/dam/video* 至 */conf/global/settings/dam/video* 如中所述 [視訊轉譯](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html).
1. 確認正在發生視訊轉換且正在建立轉譯。

## 密碼限制 {#password-restrictions}

需要在AMS執行個體上停用AEM的密碼原則。 您可以使用Screens裝置服務，在Web主控台中另外設定此設定 *com.adobe.cq.screens.device.impl.DeviceService*
請參閱 **密碼限制** 中的區段[在AEM Screens中設定作者和發佈](https://helpx.adobe.com/cn/experience-manager/6-5/screens/using/author-and-publish.html)

## 設定環境 {#setting-up-environments}

針對您的Adobe Experience Manager (AEM)版本安裝並執行下列套件的最新版本：

* AEM 服务包
* Screens Feature Pack
* AEM 累积修订包

除了上述內容，請識別所需的任何開發套件（例如WCM核心元件）或協力廠商工具套件（例如SAP Hybris）。
在本機開發環境中安裝相同的軟體套件。 指示您的使用者端在其所有QA、Stage和生產伺服器上採用相同的設定。 不相符的伺服器設定會在部署和測試時造成問題。

>[!NOTE]
>
>若要安裝AEM Screens的最新Feature Pack，請參閱 [發行說明](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js).

## 設定ACL {#setting-up-acls}

設定ACL說明如何區隔專案，以便每個個人或團隊處理自己的專案。

請參閱 [設定ACL](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) 以取得更多詳細資料。
