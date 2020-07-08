---
title: DispatcherAEM Screens配置
seo-title: DispatcherAEM Screens配置
description: 本页重点介绍为AEM Screens项目配置调度程序的指南。
seo-description: 本页重点介绍为AEM Screens项目配置调度程序的指南。
uuid: ec5219b7-73f9-4026-99e5-e4a02201b128
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 1b1a36a4-4f95-41e3-b0a8-74249efb0119
docset: aem65
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 7%

---


# DispatcherAEM Screens配置{#dispatcher-configurations-for-aem-screens}

Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。

以下页提供了为AEM Screens项目配置调度程序的指南。

>[!NOTE]
>
>如果调度程序可用，可以通过在调度程序规则中过滤来防止与注册servlet的连接。
>
>如果没有调度程序，请禁用OSGi组件列表中的注册servlet。

## Pre-requisites {#pre-requisites}

在为AEM Screens项目配置Dispatcher程序之前，您必须事先掌握调度程序知识。

有关更多 [详细信息](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) ，请参阅配置Dispatcher。

## 配置 Dispatcher {#configuring-dispatcher}

按照以下步骤为AEM Screens项目配置调度程序。

### 第1步： 配置客户端头 {#step-configuring-client-headers}

将以下内容添加 `/clientheaders`到部分：

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 第2步： 配置Screens过滤器 {#step-configuring-screens-filters}

要配置Screens过滤器，请向／筛选器中添 ***加以下内容***。

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

### 第3步： 禁用Dispatcher缓存 {#step-disabling-dispatcher-cache}

禁用／内容／屏 ***幕路径的调度程序缓存***。
