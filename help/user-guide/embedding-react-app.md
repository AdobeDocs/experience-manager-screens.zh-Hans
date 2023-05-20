---
title: 使用AEM SPA編輯器內嵌REACT應用程式並與AEM Screens Analytics整合
seo-title: Embedding a REACT application using the AEM SPA Editor and Integrating with AEM Screens Analytics
description: 請依照本頁面的說明操作，瞭解如何使用AEM SPA編輯器(可由AEM中的商務專業人員設定)，以REACT (或Angular)內嵌互動式單頁應用程式，以及如何將互動式應用程式與離線Adobe Analytics整合。
seo-description: Follow this page to learn how to embed an interactive single page application using REACT (or Angular) using the AEM SPA editor that can be configured by business professionals in AEM and also how to integrate your interactive application with offline Adobe Analytics.
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 7dc7d07e-cd94-4ce1-a106-98669be62046
source-git-commit: ffc44dbf1822ff4d0e875ef693d48dece248d555
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# 使用AEM SPA編輯器內嵌REACT應用程式並與AEM Screens Analytics整合 {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

本節說明如何使用AEM SPA編輯器(可由AEM中的商務專業人員設定)使用REACT (或Angular)內嵌互動式單頁應用程式，以及如何將互動式應用程式與離線Adobe Analytics整合。

## 使用AEM SPA編輯器 {#using-the-aem-spa-editor}

請依照下列步驟使用AEM SPA編輯器：

1. 複製AEM SPA Editor存放庫，位於 [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >此原型會建立最低限度的Adobe Experience Manager專案，作為您自己的SPA專案起點。 使用此原型時必須提供的屬性允許根據需要命名此專案的所有部分。

1. 依照Readme指示建立AEM SPA編輯器原型專案：

   ```
   mvn clean install archetype:update-local-catalog
   mvn archetype:crawl
   
   mvn archetype:generate \
   -DarchetypeCatalog=internal \
   -DarchetypeGroupId=com.adobe.cq.spa.archetypes \
   -DarchetypeArtifactId=aem-spa-project-archetype \
   -DarchetypeVersion=1.0.3-SNAPSHOT \
   ```

   >[!NOTE]
   >
   >我們使用 **群組ID** 作為 ***com.adobe.aem.screens*** 和 **ArtifactId** 作為 ***我的範例SPA*** （這是預設值）。 您可以視需要選擇自己的專案。

1. 建立專案後，請使用您選擇的IDE或編輯器並匯入產生的Maven專案。
1. 使用命令部署到您的本機AEM執行個體 ***mvn全新安裝 — PautoInstallPackage***.

### 在REACT應用程式中編輯內容 {#editing-content-in-the-react-app}

若要編輯REACT應用程式中的內容：

1. 導覽至 `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` （如適用，請取代主機名稱、連線埠和專案名稱）。
1. 您應該能夠編輯Hello world應用程式中顯示的文字。

### 將互動式REACT應用程式新增至AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

請依照下列步驟，將互動式REACT應用程式新增至AEM Screens：

1. 建立新的AEM Screens專案。 請參閱 [建立和管理專案](creating-a-screens-project.md) 以取得更多詳細資料。

1. 建立新的 **應用程式頻道** （最好是） （或1x1範本或多區域頻道） **頻道** 畫面專案的資料夾。

   >[!NOTE]
   >**序列頻道** 不建議在此使用案例中使用，因為它們本身附帶的幻燈片邏輯將與體驗的互動性質衝突
   >請參閱 [建立和管理管道](managing-channels.md) 以取得更多詳細資料。


1. 編輯任何序列頻道，並拖放內嵌的頁面元件。

   請參閱 [新增元件至管道](adding-components-to-a-channel.md) 以取得更多詳細資料。

   >[!NOTE]
   >
   >請務必在指派頻道給顯示區時新增使用者互動事件。

1. 按一下 **編輯** 以編輯頻道屬性。

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. 拖放 **內嵌頁面** 元件，或重複使用應用程式通道中的現有元件，然後選取mysamplespa應用程式下的首頁，例如， ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. 將頻道指派給顯示區。

   >[!NOTE]
   >請務必在指派頻道給顯示區時新增使用者互動事件。

1. 針對此專案註冊播放器，並將其指派給顯示區。 您現在應該能夠看到您的互動式應用程式在AEM Screens上執行。

   請參閱 [裝置註冊](device-registration.md) 以詳細瞭解如何註冊裝置。

## 透過AEM Screens將SPA與Adobe Analytics與離線功能整合 {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

請依照下列步驟，透過AEM Screens將SPA與Adobe Analytics與離線功能整合：

1. 在AEM Screens中設定Adobe Analytics。

   請參閱 [使用AEM Screens設定Adobe Analytics](configuring-adobe-analytics-aem-screens.md) 瞭解如何使用AEM Screens在Adobe Analytics中執行排序，以及使用離線Adobe Analytics傳送自訂事件。

1. 在您選擇的IDE/編輯器中編輯您的react應用程式（尤其是文字元件或您要開始發出事件的其他元件）。
1. 在您要為元件擷取的點選事件或其他事件上，使用標準資料模型新增分析資訊。

   請參閱 [使用AEM Screens設定Adobe Analytics](configuring-adobe-analytics-aem-screens.md)s以取得更多詳細資料。

1. 呼叫AEM Screens Analytics API以離線儲存事件，並以突發方式傳送至Adobe Analytics。

   例如，

   ```
   handleClick() {
       if ((window.parent) && (window.parent.CQ) && (window.parent.CQ.screens) && (window.parent.CQ.screens.analytics))
       {
           var analyticsEvent = {};
           analyticsEvent['event.type'] = 'play'; // Type of event
    analyticsEvent['event.coll_dts'] = new Date().toISOString(); // Start of collecting the event
    analyticsEvent['event.dts_start'] = new Date().toISOString(); // Event start
    analyticsEvent['content.type'] = 'Washing machine'; // Mime Type or product category
    analyticsEvent['content.action'] = 'Path to the washing machine asset in AEM'; // Path in AEM to relevant asset
    analyticsEvent['trn.product'] = 'Washing machine Model number'; // Product being explored
    analyticsEvent['trn.amount'] = 1000; // Product pricing or other numeric value or weight
    analyticsEvent['event.dts_end'] = new Date().toISOString(); // Event end
    analyticsEvent['event.count'] = 100; // Numeric value that may count a number of clicks or keystrokes or wait time in seconds for example
    analyticsEvent['event.value'] = 'My favorite analytics event';
           analyticsEvent['trn.quantity'] = 10; // Quantity of product selection
    analyticsEvent['event.subtype'] = 'end'; // Event subtype if applicable
    window.parent.CQ.screens.analytics.sendTrackingEvent(analyticsEvent);
       }
   }
   ```

   >[!NOTE]
   >
   >播放器韌體會自動將有關播放器及其執行階段環境的更多詳細資訊，新增至您傳送的自訂分析資料。 因此，除非絕對必要，否則您可能不需要擷取低階作業系統/裝置詳細資料。 您只需要專注於業務分析資料。
