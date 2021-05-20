---
title: 适用于AEM Screens的调度程序配置
seo-title: 适用于AEM Screens的调度程序配置
description: 本页重点介绍为AEM Screens项目配置调度程序的准则。
seo-description: 本页重点介绍为AEM Screens项目配置调度程序的准则。
feature: 管理屏幕
role: Developer, Business Practitioner
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 3%

---

# AEM Screens的调度程序配置{#dispatcher-configurations-for-aem-screens}

Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。

以下页面提供了为AEM Screens项目配置调度程序的准则。

>[!NOTE]
>
>如果调度程序可用，则可以通过在调度程序规则中进行过滤来阻止与注册Servlet的连接。
>
>如果没有调度程序，请在OSGi组件列表中禁用注册Servlet。

## 先决条件{#pre-requisites}

在为AEM Screens项目配置Dispatcher之前，您必须先了解Dispatcher。

有关更多详细信息，请参阅[配置Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)。

## 配置 Dispatcher {#configuring-dispatcher}

AEM Screens播放器/设备还使用经过身份验证的会话来访问发布实例中的资源。 因此，当您有多个发布实例时，请求应始终转到同一发布实例，以便经过身份验证的会话对来自AEM Screens播放器/设备的所有请求都有效。

请按照以下步骤为AEM Screens项目配置Dispatcher。

### 启用置顶会话{#enable-sticky-session}

如果要使用由单个调度程序前端的多个发布实例，则必须更新`dispatcher.any`文件以启用吸引力

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

如果一个发布实例由一个调度程序前端，则在调度程序上启用吸引力将不起作用，因为负载平衡器可能会向调度程序发送每个请求。 在此例中，单击&#x200B;**粘性**&#x200B;字段中的&#x200B;**启用**&#x200B;以在负载平衡器级别启用它，如下图所示：

![图像](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

例如，如果您使用的是AWS ALB，请参阅[应用程序负载平衡器的目标组](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)以在ALB级别启用粘性。 启用1天的吸引力。

### 步骤1:配置客户端标头{#step-configuring-client-headers}

在`/clientheaders`部分中添加以下内容：

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 步骤2:配置Screens过滤器{#step-configuring-screens-filters}

要配置Screens过滤器，请将以下内容添加到&#x200B;***/filter***&#x200B;中。

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

### 步骤3:禁用调度程序缓存{#step-disabling-dispatcher-cache}

禁用&#x200B;***/content/screens路径***&#x200B;的调度程序缓存。

Screens播放器使用经过验证的会话，因此调度程序不会缓存任何适用于`channels/assets`的Screens播放器请求。

要为资产启用缓存，以便从调度程序缓存提供资产，您必须：

* 在`/cache`部分中添加`/allowAuthorization 1`
* 将以下规则添加到`/cache`的`/rules`部分

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
