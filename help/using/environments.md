---
title: 環境 [!UICONTROL AEM Screens]
seo-title: Environments for [!UICONTROL AEM Screens]
description: 本頁面說明AEM Screens專案的環境。
seo-description: This page highlights the environments for an AEM Screens project.
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 5%

---


# 环境 {#environments}

預先判斷使用者端擁有以及將期望您使用的AEM環境，兩者皆適用於 *開發* 和 *部署*.

>[!NOTE]
>
>AEM Screens需要多個套件才能讓專案運作。 所有環境都應執行相同版本的Adobe Experience Manager。

請遵循下列准則，為您的AEM Screens專案設定環境：

1. 針對您的Adobe Experience Manager版本執行以下套件的最新版本：

   * **AEM 服务包**
   * **Screens Feature Pack**
   * **AEM 累积修订包**

1. 識別所需的任何開發套件（例如WCM核心元件）或第三方工具套件（例如SAP Hybris）。

1. 在本機開發環境中安裝相同的軟體套件。

1. 指示您的使用者端在其所有QA、Stage和生產伺服器上採用相同的設定。 不相符的伺服器設定會在部署和測試時造成問題。
