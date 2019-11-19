---
title: AEM Screens的调度程序配置
seo-title: AEM Screens的调度程序配置
description: 本页重点介绍了为AEM Screens项目配置调度程序的指南。
seo-description: 本页重点介绍了为AEM Screens项目配置调度程序的指南。
uuid: ec5219b7-73f9-4026-99e5-e4a02201b128
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 1b1a36a4-4f95-41e3-b0a8-74249efb0119
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM Screens的调度程序配置{#dispatcher-configurations-for-aem-screens}

Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。

以下页面提供了为AEM Screens项目配置调度程序的准则。

## Pre-requisites {#pre-requisites}

在为AEM Screens项目配置调度程序之前，您必须事先了解Dispatcher。

有关更多详细信息， [请参阅**配置Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)**。

## 配置 Dispatcher {#configuring-dispatcher}

请按照以下步骤为AEM Screens项目配置调度程序。

### 第1步：配置客户端标题 {#step-configuring-client-headers}

将以下内容添加到 `/clientheaders`部分：

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 第2步：配置Screens过滤器 {#step-configuring-screens-filters}

要配置Screens过滤器，请将以下内容添加到 ***/过滤器***。

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0204 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0205 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0206 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0207 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0208 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0209 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0210 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### 第3步：禁用调度程序缓存 {#step-disabling-dispatcher-cache}

禁用调度程序缓 ***存／内容／屏幕路径***。
