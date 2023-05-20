---
title: 執行遠端控制
seo-title: Impementing the Remote Control
description: 請依照本頁瞭解Screens遠端控制功能。
seo-description: Follow  this page to learn about using the Screens Remote Control Feature.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 6cb2705e-83e6-46f3-bd71-6688d7edc11f
source-git-commit: 6cd68194bf3128464ec368f3e7fd69d20925c3d6
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# 使用Screens遙控器  {#implementing-remote-control}

遠端控制功能可讓您更輕鬆地存取管理員UI、管道切換器或清除快取和重新載入等功能。 此外，它提供您檢視本機韌體版本與播放器系統資訊的方法。 這特別有用，因為滑鼠連線以及在無法存取的生產裝置上操作會很困難，如果播放器失去與AEM的連線，更是如此。 這也適用於使用Samsung RMS的情況，因為解析度的差異可能會讓使用者很難找到並使用滑鼠開啟Admin UI。

## 通用遠端修飾鍵組合 {#using-common-remote-control}

在所有播放器上，您可以在「熒幕遙控器」中使用下列按鍵組合：

1. 切換管理員UI - CTRL + 1
1. 切換頻道切換器 — CTRL + 2
1. 清除快取 — CTRL + ALT + 3
1. 重新載入播放器 — CTRL + 4

## 啟動特定的遠端修飾鍵組合 {#using-tizen-remote-control}

特定於Tizen播放器，您可以使用Samsung RMS提供的硬體遠端或軟體遠端來存取這些功能：

1. A — 切換管理員UI
1. B — 切換頻道切換器
1. C — 清除快取
1. D — 重新載入播放器

## 其他使用說明 {#using-additional-remote-control}

1. 在Admin UI開啟的狀態下，您可以使用向上和向下箭頭來瀏覽標籤，以檢視各標籤上的資訊。
1. 頻道切換器開啟時，您可以使用向上鍵和向下鍵來瀏覽頻道，也可以按下Enter鍵（或位於遠端箭頭中央的按鈕）來切換頻道。

下圖說明Samsung遠端的主要使用方式：
![影像](assets/tizen/remote.png)

>[!NOTE]
>如果您將enableAdminUI和/或enableOSD的裝置設定值設為false，遠端將不會切換管理UI和頻道切換器。 您也無法使用方向鍵來導覽一個或多個管理UI。 不過，您仍可清除快取並重新載入播放器。 如果有任何鍵盤組合與您的互動式內容衝突，您可以使用此程式碼停用遠端控制功能：

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
