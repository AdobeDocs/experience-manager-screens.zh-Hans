---
title: AEM Screens调度程序配置
seo-title: AEM Screens调度程序配置
description: 本页重点介绍为AEM Screens项目配置调度程序的指南。
seo-description: 本页重点介绍为AEM Screens项目配置调度程序的指南。
translation-type: tm+mt
source-git-commit: 37025002d02603ab8a5c571086524be858389557
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 5%

---


# AEM Screens调度程序配置{#dispatcher-configurations-for-aem-screens}

Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。

下页提供了为AEM Screens项目配置调度程序的指南。

>[!NOTE]
>
>如果调度程序可用，可以通过在调度程序规则中过滤来防止与注册servlet的连接。
>
>如果没有调度程序，请禁用OSGi组件列表中的注册servlet。

## Pre-requisites {#pre-requisites}

在为AEM Screens项目配置调度程序之前，您必须事先了解Dispatcher。

有关更多详 [细信息，请参](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) 阅配置Dispatcher。

## 配置 Dispatcher {#configuring-dispatcher}

按照以下步骤为AEM Screens项目配置调度程序。

### 启用粘滞会话 {#enable-sticky-session}

如果任何人希望与调度程序一起使用多个发布实例，则必须更新调度程序中的dispatcher.any文件。

```xml
/stickyConnections {
  /paths
  {
    "/content/screens"
    "/home/users/screens"
    "/libs/granite/csrf/token.json"
  }
}
```

### 第1步：配置客户端头 {#step-configuring-client-headers}

将以下内容添加 `/clientheaders`到部分：

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 第2步：配置Screens过滤器 {#step-configuring-screens-filters}

要配置Screens过滤器，请向／筛选器中添 ***加以下内容***。

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/libs/granite/csrf/token.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0204 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0210 { /type "allow" /method '(GET|POST)' /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0211 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0212 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0213 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0220 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0222 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### 第3步：禁用调度程序缓存 {#step-disabling-dispatcher-cache}

禁用／内容／屏 ***幕路径的调度程序缓存***。

Screens播放器使用经过身份验证的会话，因此调度程序不缓存任何屏幕播放器请求 `channels/assets`。

要为资产启用缓存，以便从调度程序缓存提供资产，您必须：

* 添加 `/allowAuthorization 1` 到部 `/cache` 分
* 将以下规则添加 `/rules` 到 `/cache`

```xml
/0000
    {
        /glob "*"
        /type "allow"
    }   

/0001
    {
        # Disable Dispatcher Cache for Screens channels
        /glob "/content/screens/*.html"
        /type "deny" 
    }

/0002
    {
    # Disable Dispatcher Cache for Screens offline manifests
    /glob "/content/screens/*.json"
    /type "deny"
    }

/0003
    { # Disable Dispatcher Cache for Screens devices json 
    /glob "/home/users/screens/*.json"
    /type "deny"
    }
```
