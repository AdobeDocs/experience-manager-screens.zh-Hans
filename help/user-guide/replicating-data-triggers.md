---
title: 將資料觸發器復寫至發佈伺服器
seo-title: Replicate data-triggers to publish server
description: 請依照本頁所述操作，瞭解如何將資料觸發器復寫至發佈伺服器。
seo-description: Replicate data-triggers to publish server.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 2%

---

# 將資料觸發程式複製到發佈伺服器 {#replicating-data-triggers}

使用ContextHub和AEM Targeting Engine根據作者/發佈設定中的資料觸發器自訂內容時，所有ContextHub和Personalization相關設定在發佈時不會自動與管道復寫。

請依照本頁面瞭解分別發佈這些設定所需的手冊步驟。

這基本上歸結為手動發佈：

1. ContextHub存放區和UI模組設定
1. 個人化對象
1. 個人化活動

## 將資料觸發程式復寫至發佈伺服器的步驟 {#replicating-data-triggers-publish}

請依照下列步驟，將資料觸發程式復寫至發佈伺服器。

### 步驟1：複製ContextHub設定 {#replicating-contexthub-configurations}

1. 導覽至 **工具** > **部署** > **分佈** > **發佈代理程式** 並按一下發佈代理程式以設定您的設定。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >或者，您可以使用 `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` 導覽至畫面以設定及測試連線。

1. 按一下 **測試連線** 從動作列驗證作者與發佈執行個體的通訊，如下圖所示。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >如果測試失敗，您需要修正製作和發佈執行個體之間的復寫代理程式設定。 請參閱 [疑難排解測試連線](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) 以取得更多詳細資料。

1. 選取 **新增** 從 **發佈代理程式** 熒幕樹狀結構並選取專案的設定路徑，例如， `/conf/screens/settings/cloudsettings/configuration`.

1. 按一下 **提交**.

### 復寫對象 {#replicating-audiences}

1. 導覽至您的AEM執行個體> **個人化** > **受眾** 或使用 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` 以直接導覽。

1. 向下切入您的專案資料夾，例如， `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 從使用者介面中選取所有對象和區段。

1. 按一下 **管理發布** 動作列中的。

1. 按一下 **下一個** 和 **發佈**.

### 復寫活動  {#replicating-activities}

1. 導覽至您的AEM執行個體> **個人化** > **活動** 或使用 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` 以直接導覽。

1. 向下切入您的專案資料夾，即， `/content/campaigns/screens/…`.

1. 從使用者介面中選取所有活動。

1. 按一下 **管理發布** 動作列中的。

1. 按一下 **下一個** 和 **發佈**.

>[!IMPORTANT]
>
>複製ContextHub設定和對象是在專案設定期間完成，而複製活動且在每次頻道內的目標定位變更時都是必要的。

#### 结果 {#result}

如果複製成功，您應在發佈執行個體（或專案的類似專案）上檢視以下結構：

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 疑難排解測試連線 {#troubleshoot-test}

如果測試連線在復寫ContextHub設定時失敗，請遵循以下章節以疑難排解問題：

1. 導覽至工具> **部署** > **分佈** > **發佈代理程式**.

1. 按一下 **編輯** 並確保端點URL **匯入工具端點** 欄位也指向散發代理程式中的發佈伺服器URL。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 如果您未使用預設的管理員認證，則需要使用不同的使用者名稱和密碼來設定發佈代理程式。

   应遵循以下步骤：

   1. 導覽至工具> **作業** > **網頁主控台** `http://localhost:4502/system/console/configMgr`以開啟 **Adobe Experience Manager Web Console畫面**.
   1. 搜尋 **Apache Sling散發傳輸認證 — 以使用者認證為基礎的DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 建立設定，透過填入 **名稱**， **使用者名稱** 和 **密碼**&#x200B;例如， *Slingtransportsecretprovider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. 按一下 **儲存**
   1. 使用 `Cmd +F` 以搜尋 **Apache Sling散發代理程式 — 轉寄代理程式工廠** 以開啟設定並搜尋 **傳輸機密提供者**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. 更新 `(name=default)` 替換為 `(name=slingTransportSecretProvider)`.
   1. 按一下 **儲存** 並從重新執行測試連線 **發佈代理程式** 再次從AEM執行個體中熒幕顯示。
