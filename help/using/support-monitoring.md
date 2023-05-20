---
title: 支援監控
seo-title: Support Monitoring for AEM Screens
description: 頁面說明「AEM Screens支援監控最佳實務指南」
seo-description: The page describes Support Monitoring for AEM Screens Best Practices Guide
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 支援監控 {#support-monitoring}

本節提供與管理數位看板專案中裝置和內容異常相關的最佳實務。

支援監控包括：

* **裝置監視**
* **內容監視**

## 內容監視 {#content-monitoring}

內容監視可讓您疑難排解與畫面上未正確顯示內容相關的問題：

1. 如果遇到空白熒幕問題：

   * Check *預覽* 以檢視頻道是否顯示黑色熒幕
   * 註冊 *本機chrome播放器* （作為擴充功能）顯示至該顯示器，並檢視是否顯示黑色熒幕。
   * 按一下滑鼠右鍵，檢查並檢查 *適用的記錄*.

   此外，如果這並非本機播放器上的動作，而是隻發生在裝置上的動作：

   * Check *媒體型別* （正在使用）中，該裝置上可能有問題，並且還要確認內容是否已成功在本機下載（管理員UI清除頻道快取）。
   * 包含任何 *裝置記錄* 快速疑難排解的票證中。
   * *收集記錄* 從AEM裝置。


## 裝置監視 {#device-monitoring}

與監視實體裝置相關的裝置監視（如果您遇到空白熒幕問題）：

1. 如果遇到空白熒幕問題：

   * 檢查 *顯示* 已開啟。
   * 檢查 *電腦* 已開啟電源，且正在傳送訊號。
   * 按一下滑鼠右鍵，檢查並檢查 *適用的記錄*.
