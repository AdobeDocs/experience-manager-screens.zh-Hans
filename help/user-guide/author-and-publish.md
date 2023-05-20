---
title: 在AEM Screens中設定作者和發佈
description: AEM Screens架構類似於傳統AEM Sites架構。 內容是在AEM編寫執行個體上編寫，然後轉送復寫到多個發佈執行個體。 請依照本頁面的說明操作，瞭解如何設定AEM Screens的作者和發佈功能。
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: ab959584c01c10f76c231ab89b574886ad7346c5
workflow-type: tm+mt
source-wordcount: '1988'
ht-degree: 0%

---


# 在AEM Screens中設定作者和發佈 {#configuring-author-and-publish-in-aem-screens}

本頁面主要說明下列主題：

* **設定作者和發佈執行個體**
* **設定發佈拓撲**
* **管理發布：將內容更新從作者傳送至發佈至裝置**

## 前提条件 {#prerequisites}

在開始使用作者和發佈伺服器之前，您應該具備以下先前的知識：

* **AEM拓撲**
* **建立和管理AEM Screens專案**
* **裝置註冊程式**

>[!NOTE]
>
>此AEM Screens功能僅在您已安裝AEM 6.4 Screens Feature Pack 2時可用。 若要存取此Feature Pack，您必須聯絡Adobe支援並要求存取權。 一旦您擁有許可權，就可以從「封裝共用」下載它。

>[!IMPORTANT]
>
>如果您想要搭配Dispatcher使用多個發佈執行個體，您必須更新Dispatcher中的dispatcher.any檔案。 另請參閱 [啟用粘性工作階段](dispatcher-configurations-aem-screens.md#enable-sticky-session) 以取得更多詳細資料。

## 設定作者和發佈執行個體 {#configuring-author-and-publish-instances}

>[!NOTE]
>
>若要進一步瞭解製作和發佈架構概觀，以及如何在AEM製作執行個體上製作內容，然後轉送復寫至多個發佈執行個體，請參閱 [製作和發佈架構概覽](author-publish-architecture-overview.md).

下節說明如何在製作和發佈拓撲上設定復寫代理。

您可以設定一個簡單範例，在此範例中託管一個作者和兩個發佈例項：

* 作者 — > localhost：4502
* 發佈1 (pub1) —> localhost：4503
* 發佈2 (pub2) —> localhost：4504

## 在作者上設定復寫代理 {#setting-replication-agents}

若要建立復寫代理，您必須瞭解如何建立標準復寫代理。

Screens需要3個復寫代理：

1. **預設復寫代理 ***(指定為*** 標準復寫代理**)
1. **Screens復寫代理**
1. **反向复制代理**

### 步驟1：建立預設復寫代理程式 {#step-creating-a-default-replication-agent}

請依照下列步驟建立預設復寫代理程式：

1. 導覽至您的AEM執行個體 — >槌子圖示 — > **作業** —> **設定**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 選取 **復寫** 左側導覽樹狀結構中的。

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. 選取 **作者上的代理** 從 **復寫** 資料夾並按一下 **新增** 建立新的標準復寫代理程式。

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. 輸入 **標題** 和 **名稱** 建立復寫代理程式，然後按一下 **建立**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. 以滑鼠右鍵按一下復寫代理程式，然後按一下 **開啟** 以編輯設定。

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. 按一下 **編輯** 以開啟 **代理程式設定** 對話方塊輸入詳細資訊。

   >[!NOTE]
   >
   >使用者需要檢查 **已啟用** 以啟用復寫代理。 您必須在「預設」、「熒幕」和「反向復寫代理」上勾選此選項。

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. 導覽至 **傳輸** 標籤並輸入 **URI**， **使用者** 和 **密碼**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >您也可以複製和重新命名現有的預設復寫代理。


#### 建立標準復寫代理  {#creating-standard-replication-agents}

1. 為pub1建立標準復寫代理程式（應已設定立即可用的預設代理程式） (例如， *https://&lt;hostname>：4503/bin/receive？sling：authRequestLogin=1*)
1. 為pub2建立標準復寫代理程式。 您可以複製pub1的復寫代理程式，並透過變更傳輸設定中的連線埠來更新要用於pub2的傳輸。 (例如， *https://&lt;hostname>：4504/bin/receive？sling：authRequestLogin=1*)

#### 建立Screens復寫代理 {#creating-screens-replication-agents}

1. 建立pub1的screens復寫代理程式。 現成可用的名稱為Screens復寫代理程式，指向連線埠4503。 需要啟用此功能。
1. 建立pub2的screens復寫代理程式。 複製pub1的Screens復寫代理程式，並將連線埠變更為pub2的4504。

   >[!NOTE]
   >若要瞭解如何設定Screens復寫代理，請參閱 [設定Screens復寫代理程式](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/configure-screens-replication.html?lang=en).

#### 建立Screens反向復寫代理 {#creating-screens-reverse-replication-agents}

1. 為pub1建立反向復寫代理程式。
1. 為pub2建立反向復寫代理程式。 您可以複製pub1的反向復寫代理程式，並透過變更傳輸設定中的連線埠來更新要用於pub2的傳輸。

## 設定發佈拓撲 {#setting-up-publish-topology}

### 步驟1：設定Apache Sling Oak型探索 {#step-configure-apache-sling-oak-based-discovery}

為拓撲中的所有發佈執行個體設定Apache Sling Oak型探索

對於每個發佈執行個體：

1. 导航至 `https://<host>:<port>/system/console/configMgr`
1. 選取 **Apache Sling Oak型Discovery Service** 設定。
1. 更新拓朴聯結器URL：新增以下所有參與發佈執行個體的URL：
   * `https://publish:4503/libs/sling/topology/connector`
   * `https://publish:4504/libs/sling/topology/connector`
1. **拓朴聯結器白名單清單**：調整為涵蓋所有發佈執行個體的IP或子網路。 請確定您將所有沒有連線埠號碼的發佈執行個體的IP/主機名稱列入白名單。

1. 啟用 **自動停止本機回圈**

每個發佈執行個體的設定應該相同，自動停止本機回圈可防止無限回圈。

#### 步驟2：驗證發佈拓撲 {#step-verify-publish-topology}

對於任何發佈執行個體，請導覽至 `https://:/system/console/topology`. 您應該會看到拓撲中代表的每個發佈執行個體，在 **傳出拓撲聯結器**.

#### 步驟3：設定ActiveMQ Artemis叢集 {#step-setup-activemq-artemis-cluster}

此步驟可讓您為ActiveMQ Artemis叢集建立加密密碼。
拓撲中所有發佈執行個體的叢集使用者和密碼必須相同。 需要加密ActiveMQ Artemis設定的密碼。 由於每個執行個體都有自己的加密金鑰，因此有必要使用加密支援來建立加密的密碼字串。 然後，加密的密碼將用於ActiveMQ的OSGi設定。

在每個發佈執行個體上：

1. 在OSGi主控台中導覽至 **主要** —> **加密支援** (`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`)。
1. 在中鍵入所需的純文字密碼（所有執行個體都相同） **純文字**
1. 按一下 **Protect**.
1. 複製值 **受保護的文字** 至記事本或文字編輯器。 此值將用於ActiveMQ的OSGi設定。

由於每個發佈執行個體預設都有唯一的加密金鑰，因此您必須在每個發佈執行個體上執行此步驟，並儲存唯一的金鑰以供下一個設定使用。

>[!NOTE]
>
>密碼的開頭和結尾應該要有大括弧。 例如：
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### 步驟4：啟動ActiveMQ Artemis叢集 {#step-activate-activemq-artemis-cluster}

在每個發佈執行個體上：

1. 導覽至OSGi設定管理員 `https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. 選取 **Apache ActiveMQ Artemis JMS提供者** 設定
1. 更新下列專案：

   * ***叢集密碼***：針對個別執行個體使用先前步驟的加密值
   * ***主題***： `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### 驗證ActiveMQ Artemis叢集 {#verify-activemq-artemis-cluster}

在每個發佈執行個體上依照下列步驟操作：

1. 導覽至「OSGi主控台 — >主要> ActiveMQ Artemis」 `https://localhost:4505/system/console/mq`.
1. 在「叢集資訊>拓撲>節點=2，成員=2」下驗證並檢查以檢視其他執行處理的連線埠。
1. 傳送測試訊息（畫面頂端，在「代理人資訊」下方）
1. 在欄位中輸入下列變更：

   1. **目的地**： /com.adobe.cq.screens/devTestTopic
   1. **文字**： Hello World
   1. 檢視每個執行個體的error.log，以檢視訊息是否已在叢集中傳送和接收

>[!NOTE]
>
>在上一步中儲存設定後，導覽至OSGi控制檯可能需要幾秒鐘的時間。 您也可以檢查error.log以取得更多詳細資料。

例如，下列影像會顯示在ActiveMQ Artemis伺服器的成功設定上。

如果您沒有從看到以下設定 */system/console/mq*，然後導覽至 */system/console/mq* 並按一下 **重新啟動** 以重新啟動Broker。

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### 移除反向連結標題需求 {#remove-referrer-header-requirement}

請依照每個Publish例項上的步驟操作：

1. 導覽至 **OSGi控制檯** > **設定管理員**
1. 選取 **Apache Sling查閱者篩選器**
1. 更新設定和 **勾選允許空白**

### 設定作者和發佈執行個體 {#configuring-author-and-publish-instance}

設定發佈拓撲後，您需要設定作者和發佈執行個體，以檢視實作的實際結果：

>[!NOTE]
>
>**前提条件**
>
>若要開始使用此範例，請先建立新的AEM Screens專案，接著在您的專案中建立位置、顯示和頻道。 新增內容至您的頻道，並將頻道指派給顯示區。

#### 步驟1：啟動AEM Screens Player （裝置） {#step-starting-an-aem-screens-player-device}

1. 啟動個別的瀏覽器視窗。
1. 前往Screens播放器，使用 *網頁瀏覽器*，也就是說，`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` 或啟動AEM Screens應用程式。 開啟裝置時，您會注意到裝置的狀態為未註冊。

>[!NOTE]
>
>您可以使用下載的AEM Screens應用程式或網頁瀏覽器來開啟AEM Screens播放器。

#### 步驟2：在作者上註冊裝置 {#step-registering-a-device-on-author}

1. 前往 `https://localhost:4502/screens.html/content/screens/we-retail` 或選取您的專案，並導覽至「裝置>裝置管理員」。
1. 選取 **註冊裝置**.
1. 按一下 **裝置註冊** 以檢視裝置。
1. 選取您要註冊的裝置，然後按一下 **註冊裝置**.
1. 驗證註冊代碼，然後按一下 **驗證**.
1. 輸入裝置的標題，然後按一下 **註冊**.

#### 步驟3：指派要顯示的裝置 {#step-assigning-the-device-to-display}

1. 按一下 **指派顯示區** （從上一步驟的對話方塊）。
1. 從中選擇頻道的顯示路徑 **位置** 資料夾。
1. 按一下 **指派**.
1. 按一下 **完成** 以完成此程式，現在裝置已指派。

檢查您的播放器，您將會看到在頻道中新增的內容。

#### 步驟4：將裝置設定發佈至發佈例項 {#step-publishing-device-configuration-to-publish-instances}

**驗證裝置**

請依照下列步驟複製裝置使用者：

1. 導覽至使用者管理頁面(例如： `https://localhost:4502/useradmin`
1. 搜尋 **screens-devices-master** 群組
1. 以滑鼠右鍵按一下群組，然後按一下 **啟動**

>[!CAUTION]
>
>請勿啟用author-publish-screens-service，因為它是系統使用者，由作者工作使用。

您也可以從「裝置管理主控台」啟動裝置。 应遵循以下步骤：

1. 導覽至您的畫面專案 — > **裝置**.
1. 按一下 **裝置管理員** 動作列中的。
1. 選取裝置並按一下 **啟動** 從動作列，如下圖所示。

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>或者，啟動裝置後，您也可以按一下「 」，編輯或更新伺服器URL **編輯伺服器URL** （如下圖所示），而您的變更將會傳播至AEM Screens播放器。

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### 發佈檢查清單 {#publishing-check-list}

下列幾點總結列出Publishing Check清單：

* *畫面裝置使用者*  — 這會儲存為AEM使用者，並且可從以下位置啟動： **工具** > **安全性** > **使用者**. 使用者會有一個長序列化字串當作前置詞「screens」。

* *專案* - AEM Screens專案。
* *位置*  — 裝置所連線的位置。
* *頻道*  — 此位置顯示的一或多個管道
* *排程*  — 如果使用排程，請確定已發佈此排程
* *位置、時程表和頻道資料夾*  — 如果對應的資源在資料夾內。

請依照下列步驟驗證作者/發佈行為：

1. 更新作者執行個體上的某些管道內容
1. 執行 **管理發布** 若要將新變更發佈至所有發佈執行個體
1. 按下 **啟動** 以從啟動裝置 **裝置管理員**
1. **編輯URL** 從作者執行個體URL到其中一個發佈執行個體URL
1. 驗證AEM Screens播放器上顯示的更新頻道內容
1. 使用不同的發佈執行個體重複這些步驟


#### 步驟5：在管理面板中將裝置指向發佈執行個體 {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. 從Screens播放器檢視管理員UI，長按左上角以開啟「管理員」功能表、在已啟用觸控功能的AEM Screens播放器上或使用滑鼠。
1. 按一下 **設定** 選項。
1. 將作者執行個體變更為發佈執行個體，於 **伺服器**.

在AEM Screens播放器中檢視變更。

或者，您也可以使用下列步驟，從裝置管理主控台更新/編輯伺服器URL：

1. 導覽至您的AEM Screens專案，然後選取 **裝置** 資料夾。
1. 按一下 **裝置管理員** 動作列中的。
1. 選取裝置並按一下 **編輯伺服器URL** （如下圖所示），而您的變更將會傳播至AEM Screens播放器。

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

此 **管理發布** 功能可讓您將author的內容更新傳送至publish to device。 您可以為整個AEM Screens專案或僅限其中一個頻道、位置、裝置、應用程式或排程發佈/取消發佈內容。 若要進一步瞭解此功能，請參閱 [隨選內容更新](on-demand-content.md).

## 疑難排解提示 {#troubleshoot-tips}

請依照以下章節取得與作者/發佈設定相關的常見問題解答。

### 如何在初始註冊和指派後新增從https到http的重新導向？ {#add-redirect}

**解決方案**
設定啟用 `Proxy/Load Balancer Connection in the Jetty configuration` 至 `true`.

### 如何更新離線內容和播放器下載問題，以及外部資產的問題 `/content/dam/projects/<project>`？ {#update-offline-content}

**解決方案**
為大量offline-update-screens-service使用者和screens-devices-master group授予讀取許可權 `/content/dam` 或您想要使用的特定資產（如果您想要更嚴格的限制）。

### 如何解決Screens復寫代理程式錯誤？ {#replication-agent}

**解決方案**
請確定您尚未在代理程式設定中核取使用反向復寫選項。 Screens復寫代理程式無法當作反向復寫代理程式使用，而且此功能的範圍是將裝置命令從作者轉送至發佈。