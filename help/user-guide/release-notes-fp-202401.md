---
title: Screens Feature Pack 202401发行说明
description: 了解2024年1月2日发布的AEM Screens功能包202401。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
TQID: https://experienceleague.adobe.com/b6ZM04Vl6ozehx8E-y9iV1KAo-FI7DZSpDcHvhudkMI
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 248
ht-degree: 10%

---

# 功能包202401发行说明 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe建议您升级到Adobe Experience Manager 6.5 (AEM 6.5)的最新版本。 从[此处](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/release-notes/release-notes)获取最新版本信息。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包11.1。

您可以使用您的Adobe ID从[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载AEM Screens 6.5.11.1版本的最新功能包。 导航到&#x200B;**Adobe Experience Manager**&#x200B;选项卡并搜索&#x200B;**Screens**，以获取标题为&#x200B;**AEM 6.5 Screens FP11.1**&#x200B;的最新功能包。

## 发布日期 {#release-date}

AEM Screens功能包202204的发布日期是2024年1月2日。

### 新增功能 {#what-is-new}

此版本仅包含安全修复。

### 错误修复 {#bug-fixes}

* AEM Screens设备“空闲文本”字段出现XSS问题。 (SCRNS-2614)

* 通过`Clear cache`操作对话框在`screens/dashboard/device.html`上出现XSS问题。 (SCRNS-2632)

* `libs/screens/player/browser/firmware.html`处Screens播放器配置中的XSS问题。 (SCRNS-2652)

* 删除设备时，设备标题中存储的XSS将触发。 (SCRNS-2653)

* `/libs/screens/core/components/device/info.json.html`处的XSS问题。 (SCRNS-2659)

* 在`/screens/register-device-wizard.html`处使用参数`item`反映了XSS。 (SCRNS-2670)

* 通过`returnPage`参数在`screens/dashboard/device.html`中反映了XSS。 (SCRNS-3056)

* 打开assign-device-wizard.html上的“重定向”。 (SCRNS-3444)

* 在设备仪表板上打开重定向。 (SCRNS-3443)

* `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`处的XSS问题。 (SCRNS-3459)

* 修复了“周期性计划”和“添加计划”按钮缺失：渠道计划中发现的问题。 (SCRNS-2739)
