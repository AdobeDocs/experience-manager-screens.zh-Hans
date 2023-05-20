---
title: 测试和质量保证
seo-title: Testing and Quality Assurance for AEM Screens
description: 頁面說明AEM Screens最佳實務指南的測試和品質保證
seo-description: The page describes Testing and Quality Assurance for AEM Screens Best Practices Guide
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 2%

---

# 测试和质量保证 {#testing-quality}

>[!NOTE]
>此活動的一般利害關係人是A/V整合商。

當我們更接近數位看板網路的實際部署時，應該建立測試與QA計畫，解決網路的每個元素，包括所有硬體元件、所有軟體元件和所有網路元件。
在這個階段中，應該建置並完整測試整個測試系統。

應建立檢查清單，識別所有先前定義的KPI，並根據它們測量交付成果。

>[!NOTE]
>
>此階段也應作為建立安裝和使用手冊的工具，之後可隨裝置一併寄出，並保留在現場以供日後參考。

應考慮以下元素：

## 1.機械考量 {#mechanical-considerations}

建議採取下列機械考量：

* 顯示器掛載
* 播放器掛載
* 通風
* 周邊裝置附件
* 纜線管理
* 裝置網路

## 2.軟體考量事項 {#software-considerations}

建議採取下列軟體考量事項：

* 裝置註冊
* 媒體發佈
* 播放
* 資料庫相依性（先前定義）


## 3.裝置管理考量事項 {#device-management-considerations}

AEM Screens包含Device Control Center模組，可管理Screens播放器應用程式端點。

這指任何 *播放器* 已安裝Screens播放器應用程式且已註冊至AEM執行個體的硬體裝置。
此模組可讓您：

1. 監視播放器應用程式錯誤記錄
1. 管理遠端熒幕擷取畫面
1. 管理內容下載
1. 管理應用程式重新啟動問題

若要深入瞭解 ***裝置控制中心***，請參閱 [疑難排解裝置控制中心](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) 在 **AEM Screens使用手冊**.

>[!CAUTION]
>
> 您不應使用「裝置控制中心」來：
> 1. 安裝播放器應用程式的新版本
> 1. 監視系統層級資源
> 1. 疑難排解系統層級錯誤
> 1. 允許遠端案頭介入



>[!NOTE]
>
> Adobe建議所有部署都應使用專用的第三方裝置管理平台。

選擇的特定平台取決於許多因素，包括 ***目標作業系統***， ***專案需求*** 和 ***端點數目***.

以下是幾個範例：

* Google Chrome裝置管理
* 團隊檢視器
* AirWatch
* 42Gears
* 專屬AV Integrator中介軟體
