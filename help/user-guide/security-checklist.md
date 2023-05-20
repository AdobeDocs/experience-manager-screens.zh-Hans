---
title: 安全性檢查清單
seo-title: Security Checklist
description: 此頁面說明主要安全性區域，並提供問題和考量事項的核對清單。
seo-description: The page describes Security Checklist
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# AEM Screens安全性檢查清單  {#security-checklist}

AEM Screens安全性檢查清單頁面說明主要安全性區域，並提供問題和考量事項檢查清單。

## 檢查清單表格 {#checklist-table}

| **安全區域** | **檢查清單** | **是/否/NA** |
|---|---|---|
| **AEM和Screens軟體更新** | ***答：*** *是否已套用最新的Adobe Experience Manager (AEM) Service Pack？* <br>***b.***  *是否已套用最新的AEM Screens Feature Pack？* <br>***c.*** *您是否使用最新可用的AEM Screens Player軟體，來源為 [AEM Screens播放器下載](https://download.macromedia.com/screens/)？* |
| **實體安全性** | ***答：*** *您是否已停用所有不必要的連線埠？* <br>***b.***  *您是否已確保纜線與硬體的安全？* <br>***c.*** *您使用任何容器嗎（如適用）？* |
| **網路安全性** | ***答：*** *您是否為招牌裝置使用隔離的子網路？* <br>***b.***  *隔離子網路是否允許存取必要的端點，包括AEM、Adobe Analytics或其他必要的服務？* <br>***c.*** *您是否使用企業最佳實務來保護您的Wi-Fi？* <br>***d.*** *如果使用同步播放，您只允許主裝置上的WebSocket使用TCP 24503嗎？* <br>***e.*** *您是否已解除封鎖播放器裝置的IP位址範圍，讓只有授權裝置才能存取作者上的註冊服務？* |
| **作業系統安全性** | ***答：*** *您是否已升級至作業系統的最新版本，並已套用所有必要的安全性修補程式？* <br>***b.*** *您是否已停用所有不必要的服務並移除不必要的應用程式？* <br>***c.*** *您是否已將裝置註冊到裝置管理以強制執行企業原則？* <br>***d.*** *您是否已將裝置鎖定至單一應用程式（播放器）資訊站？* <br>***e.*** *您是否有標準作業程式(SOP)可供日後安裝作業系統安全性更新？*<br>***f.*** *您是否遵循使用中作業系統的安全性最佳實務，例如防惡意程式碼軟體、非系統管理使用者？* |
| **應用程式安全性** | ***答：*** *您是否已針對生產環境停用管理員UI、管道切換器和活動UI？* <br>***b.*** *您是否將生產環境的記錄層級降到最低？* <br>***c.*** *您使用https連線到AEM嗎？* <br>***d.*** *您使用的是CA簽署的憑證還是企業PKI？ （不是自我簽署憑證）*<br>***e.*** *您使用TLS而非SSL v3嗎？*<br>***f.*** *註冊時，您是否正在裝置和AEM上驗證註冊權杖？*<br> ***g.*** *您是否已分類正在使用的資料，以及裝置上沒有PII或PHI？*<br> ***h.*** *您是否將正在使用的資料分類，而且裝置上沒有個人識別資訊(PII)或受保護的健康資訊(PHI)？*<br> ***i.*** *您是否已設定監視電子郵件，以及您是否有SOP來回應監視電子郵件和處理非釘選裝置？* |
| **访问控制** | ***答：*** *您是否有已識別且由內部管理的角色型存取控制(RBAC)？* <br>***b.*** *您使用Adobe的最佳實務來存取作者、管理員和玩家，是否遵循最低許可權原則？* |

### 下載安全性檢查清單 {#download-checklist}

若要下載AEM Screens安全性檢查清單，請按一下 [此處](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).
