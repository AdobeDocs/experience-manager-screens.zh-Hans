---
title: Screens功能包20240215的发行说明
description: 请阅读本页，了解有关2024年2月15日发布的AEM Screens Feature Pack 20240215的信息。
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: d5b94814df33f00e23fcd22e85e50d6f02947d45
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 5%

---

# 功能包20240215发行说明 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>建议您升级到6.5 Adobe Experience Manager (AEM 6.5)的最新版本。 我们可以从获取最新版本信息 [此处](https://experienceleague.adobe.com/docs/experience-manager-65/content/release-notes/release-notes.html?lang=en)

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包11.3。

您可以从以下网站下载AEM Screens 6.5.11.3版本的最新功能包： [软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。 导航到 **Adobe Experience Manager** 选项卡和搜索 **Screens** 获取标题为 **AEM 6.5屏幕FP11.3**.

## 发布日期 {#release-date}

AEM Screens功能包20240215的发布日期为2024年2月15日。

### 新增功能 {#what-is-new}

此版本仅包含安全修复。

### 错误修复 {#bug-fixes}

* 从先前在FP11.1中为XSS提供的修复中移除了切换检查 `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* XSS问题位于 `libs/screens/dcc/components/clientlibs/columnviewnavigatorshim.js`. (SCRNS-3973)