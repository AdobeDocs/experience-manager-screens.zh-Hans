---
title: 製作和發佈架構概覽
seo-title: Author and Publish Architectural Overview
description: AEM Screens架構類似於傳統AEM Sites架構。 內容是在AEM編寫執行個體上編寫，然後轉送復寫到多個發佈執行個體。 請詳閱本頁內容，瞭解更多有關作者和發佈架構概觀的資訊。
seo-description: AEM Screens architecture resembles a traditional AEM Sites architecture. Content is authored on an AEM author instance and then forward-replicated to multiple publish instances. Follow this page to learn more on author and publish architectural overview.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---

# 製作和發佈架構概覽 {#author-and-publish-architectural-overview}

本頁面主要說明下列主題：

* **發佈伺服器簡介**
* **架构概述**
* **註冊程式**

## 前提条件 {#prerequisites}

在開始使用作者和發佈伺服器之前，您應該具備以下先前的知識：

* **AEM拓撲**
* **建立和管理AEM Screens專案**
* **裝置註冊程式**

>[!NOTE]
>
>此AEM Screens功能僅在您已安裝AEM 6.4 Screens Feature Pack 2時可用。 若要存取此Feature Pack，您必須聯絡Adobe支援並要求存取權。 一旦您擁有許可權，就可以從「封裝共用」下載它。

## 简介 {#introduction}

AEM Screens架構類似於傳統AEM Sites架構。 內容是在AEM編寫執行個體上編寫，然後轉送復寫到多個發佈執行個體。 AEM Screens裝置現在可以透過負載平衡器連線至AEM發佈陣列。 可以新增多個AEM發佈執行個體以繼續擴充發佈陣列。

*例如*，AEM Screens內容作者會在製作系統上針對設定為與發佈陣列互動的特定裝置發出命令，或是取得設定為與發佈陣列互動之裝置相關資訊的AEM Screens內容作者。

下圖說明製作和發佈環境。

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## 架構設計 {#architectural-design}

有五個架構元件，可加速此解決方案：

* ***復寫內容*** 從作者到發佈，以依裝置顯示

* ***反轉*** 將二進位內容從發佈（從裝置接收）複製到作者
* ***傳送中*** 透過特定REST API從作者發佈到發佈的命令
* ***傳訊*** 在發佈執行個體之間同步裝置資訊更新和命令
* ***輪詢*** 作者透過特定REST API取得裝置資訊

### 內容和設定的復寫（轉送）  {#replication-forward-of-content-and-configurations}

標準復寫代理程式可用來復寫畫面通道內容、位置設定和裝置設定。 這可讓作者更新管道的內容，並在發佈管道更新之前選擇性地進行某種核准工作流程。 需要為發佈伺服器陣列中的每個發佈執行個體建立復寫代理程式。

下圖說明復製程式：

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>需要為發佈伺服器陣列中的每個發佈執行個體建立復寫代理程式。

### Screens復寫代理和命令  {#screens-replication-agents-and-commands}

自訂Screens專用的復寫代理程式是用來從Author執行個體傳送命令至AEM Screens裝置。 AEM Publish執行個體可作為將這些命令轉送至裝置的中介者。

這可讓作者繼續管理裝置，例如傳送裝置更新，以及從作者環境擷取熒幕擷圖。 AEM Screens復寫代理程式具有自訂傳輸設定，例如標準復寫代理。

### 發佈執行個體之間的傳訊  {#messaging-between-publish-instances}

在許多情況下，命令只適用於單次傳送至裝置。 但在負載平衡的發佈架構中，未知裝置要連線的發佈執行個體。

因此，作者執行個體會將訊息傳送給所有發佈執行個體。 不過，之後只應將單一訊息轉送至裝置。 為確保傳訊正確無誤，發佈執行個體之間必須通訊。 這是使用取得的 *Apache ActiveMQ Artemis*. 每個發佈執行個體都會使用Oak型Sling探索服務放在鬆散耦合的拓撲中，且ActiveMQ已設定為讓每個發佈執行個體可以通訊並建立單一訊息佇列。 Screens裝置透過負載平衡器輪詢發佈陣列，並從佇列頂端挑選命令。

### 反向復寫 {#reverse-replication}

在許多情況下，在命令之後，會預期從Screens裝置將某種回應轉送到Author執行個體。 為了達成此AEM ***反向復寫*** 已使用。

* 為每個發佈執行個體建立反向復寫代理，類似於標準復寫代理和screens復寫代理。
* 工作流程啟動器設定會監聽在發佈執行個體上修改的節點，然後觸發工作流程將裝置的回應放入發佈執行個體的寄件匣中。
* 此內容中的反向復寫僅適用於裝置提供的二進位資料（例如記錄檔和熒幕擷圖）。 非二進位資料會透過輪詢擷取。
* 從AEM編寫執行個體輪詢的反向復寫會擷取回應，並將其儲存至編寫執行個體。

### 輪詢發佈執行個體  {#polling-of-publish-instances}

製作執行個體必須能夠輪詢裝置以取得心率，並瞭解連線裝置的健康狀態。

裝置ping負載平衡器並路由至發佈執行個體。 然後，發佈執行個體會透過提供的Publish API公開裝置的狀態@ **api/screens-dcc/devices/static** 適用於所有使用中裝置和 **api/screens-dcc/devices/&lt;device_id>/status.json** 適用於單一裝置。

製作執行個體會輪詢所有發佈執行個體，並將裝置狀態回應合併為單一狀態。 輪詢作者的排程工作為 `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` 並且可以根據cron運算式進行設定。

## 注册 {#registration}

註冊會持續源自AEM編寫執行個體。 AEM Screens裝置指向作者執行個體並完成註冊。

一旦裝置在製作環境中註冊後，裝置設定和管道/排程指派就會複製到AEM發佈執行個體。 AEM Screens裝置設定接著會更新，以指向AEM發佈伺服器陣列前面的負載平衡器。 此為一次性設定，一旦Screens裝置成功連線至發佈環境，就可以繼續接收來自製作環境的命令，而且應該不需要直接將Screens裝置連線至製作環境。

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### 后续步骤 {#the-next-steps}

瞭解AEM Screens中作者與發佈設定的架構設計後，請參閱 [設定AEM Screens的作者和發佈](author-and-publish.md) 以取得更多詳細資料。
