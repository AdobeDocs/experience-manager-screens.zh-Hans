---
title: AEM Screens常見問題集
seo-title: AEM Screens FAQs
description: 請依照本頁面的說明操作，取得與AEM Screens專案相關的常見問題解答。
seo-description: Follow this page to get answers to FAQs related to an AEM Screens project.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: 089bf4eebe5234d77d6f02ae6fc3b8bb75ba6ea2
workflow-type: tm+mt
source-wordcount: '2185'
ht-degree: 0%

---

# AEM Screens常見問題集 {#aem-screens-faqs}

以下章節提供與AEM Screens專案相關之常見問答集的解答。

## 空白畫面問題 {#blank-screen}

>[!NOTE]
>列出的強制檢查，在引發問題之前應由主要支援或客戶端支援嘗試。

### 1.面對黑熒幕或未播放內容的客戶，其急救疑難排解步驟是什麼？ {#troubleshooting-blank-screen}

* 檢查頻道預覽是否正常運作。
* 檢查顯示預覽是否正常運作
* 請嘗試將播放器註冊為系統上的瀏覽器擴充功能，以顯示在相同的顯示器上，並檢查此功能是否運作。
* 在系統上執行播放器時，導覽至 `http://localhost:24502`. 檢查是否已正確下載所有內容。
* 檢查資產是否已建立適當的轉譯，且正在播放正確的轉譯。
* 檢查是否有任何排程內容，以及時間是否正確。 檢查播放器中設定的時間是否正確。
* Inspect播放器主控台會記錄並檢查是否有任何錯誤。 按一下滑鼠右鍵並檢查以檢視主控台記錄。 如果使用Windows Player，請按 `CTRL + ALT +I` 開啟dev console以檢視記錄。

### 2.如何建立預設頻道或排程，以解決AEM Screens中的灰幕問題？

為避免欄位中出現空白或灰色畫面，請建立預設的全域頻道或排程，指派給優先順序最低為1的每個顯示器。 萬一內容更新發生問題（由於網路、播放器、伺服器或復寫），因為播放器已在光碟上快取此內容，播放應該可以正常並避免灰屏。

所有其他內容（例如頻道或排程）的優先順序將大於1，因此其他內容具有優先順序，並且全域頻道或排程內容（具有優先順序1）將僅作為回退選項播放。

## 頻道管理 {#channel-management}

### 1.線上和離線管道之間有何差異？ {#what-is-the-difference-between-an-online-and-an-offline-channel}

一個 ***線上頻道***，會在即時環境中顯示更新的內容，而 ***離線頻道***，會顯示快取的內容。

### 2.如何線上建立管道？ {#how-do-i-make-a-channel-online}

選取頻道，然後從動作列導覽至頻道屬性。 Check **開發人員模式（強制頻道上線）** 在 **頻道** 索引標籤讓頻道上線。

### 3. 「管道角色」欄位有何用途？ {#what-is-the-use-of-the-channel-role-field}

管道角色是實際執行管道的抽象概念，可供作者直接專注於一般體驗。 您可以將它視為一種標籤，可唯一識別相關內容（顯示或排程）中的管道。

### 4.實際管道解析如何發生？ {#how-does-actual-channel-resolution-happen}

對象 *靜態參考*，解析度會依循指定的路徑。

對象 *動態參考*，將頻道指派給顯示區（而非排程）後，就會發生解析度。 顯示路徑會成為色版的前後關聯，解析度如下（最高至最低優先順序）：

1. 顯示區有一個子節點符合參照的管道名稱
1. 該顯示區有一個與參照的管道名稱相符的同層級節點
1. 顯示的父級位置有一個與參照的管道名稱相符的子節點
1. 顯示的父項位置有一個子節點符合參照的管道名稱

等等，直到您到達「位置」資料夾並在此停止（因此您無法參照會位於「色版」資料夾中的色版，例如僅參照位置子樹狀結構中的色版）。

### 5.如何在AEM Screens頻道中設定自訂clientlib離線設定？

使用內建自訂使用者端代碼時 `clientlib` 在AEM Screens管道中，若要確保 `clientlib` 檔案在管道中載入成功(`manifest.json`)並且將包含 `clientlib`.

從管道編輯器執行以下步驟：

1. 選取管道並按一下 **編輯** 以開啟管道編輯器。
1. 選取您要新增自訂的元件 `clientlib`.
1. 按一下設定按鈕（扳手圖示）。
1. 導覽至 **離線設定** 標籤並新增您的自訂clientlib的路徑 **使用者端資料庫**.

## 设备注册 {#device-registration}

### 1.如果發現端點（例如裝置上線和註冊請求），我可以編寫大量裝置的指令碼並註冊這些裝置。 除了將此鎖定到分支Wi-Fi之外，是否可以保護這些請求？ {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

目前僅可在作者執行個體上註冊。 雖然註冊服務未經驗證，但只會在AEM中建立擱置中的裝置，實際上並不會註冊裝置或指派任何顯示器。

若要註冊裝置(這表示在AEM中為該裝置建立使用者)，您仍然需要向AEM進行驗證，並且目前手動遵循註冊精靈以完成註冊。 理論上，惡意使用者可能會建立多個擱置中的裝置，但無法在沒有AEM登入的情況下註冊任何裝置。

### 2.是否有方法可透過某種形式的驗證將HTTPGET要求轉換為HTTPPOST？ {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

註冊要求是POST要求。

建議從工作階段取得裝置ID，而非以引數傳遞。 這會清除伺服器記錄、瀏覽器快取等。 目前不是安全性問題。 請注意，當伺服器上沒有狀態變更時，會使用語義GET，而當狀態變更時，則會使用POST。

### 3.是否可以拒絕裝置註冊要求？ {#is-there-a-way-to-decline-a-device-registration-request}

您無法拒絕註冊要求。 實際上，註冊請求應在中設定的逾時後過期 `Adobe Experience Manager Web Console`. 根據預設，此值會設定為一天，並儲存在記憶體快取中。

## 裝置監視和健康情況報告 {#device-monitoring-and-health-reports}

### 1.如果我的AEM Screens播放器顯示空白熒幕，該如何進行疑難排解？ {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

請檢查下列是否可能疑難排解空白熒幕問題：

* AEM無法推送離線內容
* 頻道沒有任何內容
* 沒有任何資產排程為目前時間顯示

### 2.如果AEM Screens播放器無法註冊且其狀態顯示為「失敗」，我該怎麼做？ {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

您需要啟用Apache Sling反向連結篩選允許空白。 這是在AEM Screens Player和AEM Screens伺服器之間最佳化控制通訊協定運作的必要專案。

1. 導覽至 **Adobe Experience Manager Web主控台設定**
1. 檢查 **allow.empty** 選項。
1. 单击“**保存**”。

### 3.如果在註冊AEM Screens播放器時，裝置顯示失敗且主控台記錄顯示ENAME_NOT_FOUND錯誤，該如何進行疑難排解？ {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

如果播放器找不到AEM Screens伺服器DNS，就可能會發生此問題。 您可以嘗試使用IP位址進行連線。 若要取得伺服器的IP，請使用： *arp &lt;server_dns_name>*.

### 4. AMS是否建議在所有裝置上實作Android Watchdog？ APK是否包含Watchdog (Cordova)外掛程式？ {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

使用純Android API的跨平台Android看門狗已經是計畫的一部分。 不需要其他軟體，但視您使用的裝置而定，您可能需要放棄此要求，才能取得完整電源週期(Powermanager api)的系統許可權。 若未使用製造商金鑰放棄，則會結束並重新啟動應用程式，但不會重新啟動電源。

如需如何實作Android Player的詳細資訊，請參閱 [**實作Android Player**](implementing-android-player.md).

### 5.Adobe/AMS建議使用哪些協力廠商遠端監視和警示工具（軟體）來監視每個裝置？  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

根據您希望在監視和警報中顯示的內容，如果裝置一段時間未偵測，AEM Screens Notifications服務會通知您。 協力廠商工具取決於您的作業系統(OS)、其功能及客戶的特定需求。

有關您可在何處監控裝置活動的詳細資訊，請參閱 [**AEM Screens通知服務**](screens-notifications-service.md).

## AEM Screens 播放器 {#aem-screens-player}

### 1.如何將ChromeOS播放器安裝為Chrome瀏覽器外掛程式？ {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS播放器可在開發人員模式下安裝為Chrome瀏覽器外掛程式，而不需要實際的Chrome播放器裝置。 若要進行安裝，請遵循下列步驟：

1. 按一下 [此處](https://download.macromedia.com/screens/) 以下載最新的Chrome Player。
1. 解壓縮並儲存在磁碟上。
1. 開啟Chrome瀏覽器並選取 **擴充功能** 或直接導覽至「 」 ***chrome://extensions***.
1. 切換至 **開發人員模式** 從右上角。
1. 按一下 **載入已解壓縮** 從左上角，並載入解壓縮的Chrome Player。
1. Check **AEM Screens Chrome Player** 外掛程式（如果可在擴充功能清單中取得）。
1. 開啟新標籤，然後按一下 **應用程式** 圖示瀏覽，或直接導覽至 ***chrome://apps***.
1. 按一下 **AEM Screens** 啟動Chrome Player的外掛程式。 依預設，播放器會以全熒幕模式啟動。 按下 **esc** 以結束全熒幕模式。

### 2.如果Screens播放器無法透過具有自訂錯誤處理常式的發佈執行個體進行驗證，該如何進行疑難排解？ {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

AEM Screens播放器啟動時，會要求 ***/content/screens/svc.ping.json***，播放器收到404錯誤時。 播放器會起始驗證請求，以針對發佈執行個體進行驗證。 如果發佈執行個體中有自訂錯誤處理常式，請確定您在上為匿名使用者傳回404狀態碼 ***/content/screens/svc.ping.json***.

### 3.如何在Android Player中設定裝置熒幕持續開啟？ {#how-to-set-the-device-screen-stay-on-in-an-android-player}

請依照下列步驟，在任何Android播放器上開啟「保持清醒」：

1. 導覽至Android播放器設定 — > **關於**
1. 在組建編號上點選7次以啟用 **開發人員選項** 在 **設定**
1. 導覽至 **開發人員選項**
1. 啟用 **保持清醒**

### 4.如何啟用Windows播放器的視窗模式？{#enable-player}

Windows Player中沒有視窗模式。 永遠是全熒幕模式。

### 5.如果AEM Screens播放器持續傳送登入要求，該如何進行疑難排解？{#requests-login}

請依照下列步驟，疑難排解持續傳送請求的AEM Screens播放器 `/content/screens/svc.json` 和 `/libs/granite/core/content/login.validate/j_security_check`：

1. AEM Screens播放器啟動時，會要求 `/content/screens/svc.json`. 當播放器收到回應中的404狀態碼時，它會使用起始驗證請求 `/libs/granite/core/content/login.validate/j_security_check` 針對 *發佈* 執行個體。 如果中有自訂錯誤處理常式 *發佈* 執行個體，請確定傳回匿名使用者的404狀態碼 `/content/screens/svc.json` 或 `/content/screens/svc.ping.json`.

1. 檢查您的Dispatcher設定是否允許在 `/filters`.

   另請參閱 [設定畫面篩選器](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) 以取得更多詳細資料。

1. 檢查您的Dispatcher重寫規則是否正在將任何Screens路徑重寫為其他路徑。

1. 檢查您是否擁有 `/etc/map` 上的規則 *作者* 或 *發佈* 執行個體和畫面路徑符合 `sling:match` 並在內部重新導向至不同的路徑。 解析中的確切url `/system/console/jcrresolver` 有助於識別 *發佈* 執行個體正在將這些URL重寫為任何其他路徑。

1. 檢查Apache Sling Resource Resolver Factory設定是否造成內部重寫。

### 6.如何從播放器API取得顯示器和裝置的詳細資料？

您可以透過以下方式取得顯示器和裝置的詳細資訊：

* **內部JS API**
* **ContextHub存放區**：三個ContextHub存放區定義於 `/libs/screens/clientlibs/contexthub` 以公開頻道、裝置和顯示資訊。

   請依照下列步驟，使用這些ContentHub存放區值：

   * 編輯管道屬性，並將「個人化」標籤中的ContextHub路徑設定為值（如上所述）
   * 在管道JS中，您可以使用：

      ```shell
         ContextHub.getStore('screens-device');
         ContextHub.getStore('screens-display');
         ContextHub.getStore('screens-channels');
      ```

## 一般疑難排解提示 {#general-troubleshooting-tips}

### 1.如何停用Livefyre以避免A/P Screens錯誤？ {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

若要停用Livefyre以避免記錄錯誤：

1. ***停用Livefyre套裝：***

   * 导航至 `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * 搜尋AEM Livefyre套件組合： `com.adobe.cq.social.cq-social-livefyre`
   * 按一下 **停止**

1. ***停用Livefyre輪詢程式：***

   * 在CRXDE Lite中，導覽至 `/etc/importers/polling/livefyre-poller/jcr:content`
   * 新增屬性 *已啟用* type *布林值*
   * 設定 **啟用屬性** 至 **false**

### 2.如何新增Oak索引資訊？ {#add-oak-index-info}

AEM Screens會為產品使用的查詢建立索引定義。
如果有的話 *查詢周遊警告* 在 `error.log`，為您的查詢建立自訂索引。 請參閱 [設定索引](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes) 以取得更多詳細資料。

您也可以參閱上的其他資源 [Oak檔案](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### 3.設定v3資訊清單需要什麼？ {#configure-v3}

若要啟用v3資訊清單，您必須：

* 更新Dispatcher。
另請參閱 [為資訊清單版本v3設定Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) 以取得更多詳細資料。

* 更新自訂元件。
另請參閱 [自訂處理常式的範本](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers) 以取得更多詳細資料。

* 在中停用ContentSync `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* 在中啟用SmartSync `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* 编辑 `channel/experience fragment/page components`.

* 導覽至 **離線設定** 標籤。

* 輸入 `clientlibs `以及需要新增至資訊清單的靜態檔案資料夾。

### 4.如果在套件screens-cloud-ams-pkg-0.0.20、screens-cloud-ams-pkg-0.0.16和screens核心套件已安裝但未啟用，您應該怎麼做？

您必須安裝AEM 6.5 Feature Pack 8的最低版本，AMS聯結器才能運作。 請參閱 [可用性](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105.html?lang=en#availability) 以取得Screens Feature Pack的最低版本。

### 5.如何在Screens中設定CQ Link Externalizer服務？

此服務可用來定義製作和發佈執行個體的公用主機名稱，然後使用值來更新裝置伺服器URL及用於ContextHub目標定位。

Screens中的CQ Link Externalizer服務可透過以下方式設定：

1. 导航至 `http://localhost:4502/system/console/configMgr`
1. Day CQ連結外部化器
1. 變更的主機名稱 `author/publish` 視需要輸入