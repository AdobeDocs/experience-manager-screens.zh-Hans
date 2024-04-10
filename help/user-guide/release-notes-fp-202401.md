---
title: Screens功能包202401的发行说明
description: 了解2024年1月2日发布的AEM Screens功能包202401。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 4%

---

# 功能包202401发行说明 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>建议您升级到6.5 Adobe Experience Manager (AEM 6.5)的最新版本。 您可以从中获取最新版本信息 [此处](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/release-notes)

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包11.1 。

您可以从以下网站下载AEM Screens 6.5.11.1版本的最新功能包： [软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。 导航到 **Adobe Experience Manager** 选项卡和搜索 **Screens** 获取标题为 **AEM 6.5屏幕FP11.1**.

## 发布日期 {#release-date}

AEM Screens功能包202204的发布日期是2024年1月2日。

### 新增功能 {#what-is-new}

此版本仅包含安全修复。

### 错误修复 {#bug-fixes}

* AEM Screens设备“空闲文本”字段出现XSS问题。 (SCRNS-2614)

* XSS问题位于 `screens/dashboard/device.html` 通过 `Clear cache` 操作对话框。 (SCRNS-2632)

* 位于的Screens播放器配置中存在XSS问题 `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* 删除设备时，设备标题中存储的XSS将触发。 (SCRNS-2653)

* XSS问题位于 `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* 反射了参数的XSS `item` 在 `/screens/register-device-wizard.html`. (SCRNS-2670)

* 在中反映的XSS `screens/dashboard/device.html` 通过 `returnPage` 参数。 (SCRNS-3056)

* 打开assign-device-wizard.html上的“重定向”。 (SCRNS-3444)

* 在设备仪表板上打开重定向。 (SCRNS-3443)

* XSS问题位于 `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* 修复了“周期性计划”和“添加计划”按钮缺失：渠道计划中发现的问题。 (SCRNS-2739)
