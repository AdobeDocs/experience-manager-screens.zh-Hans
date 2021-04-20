---
title: AEM Screens的调度程序配置
seo-title: AEM Screens的调度程序配置
description: 本页重点介绍为AEM Screens项目配置调度程序的指南。
seo-description: 本页重点介绍为AEM Screens项目配置调度程序的指南。
feature: Administering Screens
role: Developer, Business Practitioner
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 3%

---


# AEM Screens{#dispatcher-configurations-for-aem-screens}的调度程序配置

Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。

以下页提供了为AEM Screens项目配置调度程序的指南。

>[!NOTE]
>
>如果调度程序可用，可以通过在调度程序规则中过滤来防止与注册servlet的连接。
>
>如果没有调度程序，请禁用OSGi组件列表中的注册servlet。

## 先决条件{#pre-requisites}

在为AEM Screens项目配置调度程序之前，您必须事先了解Dispatcher。

有关详细信息，请参阅[配置Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)。

## 配置 Dispatcher {#configuring-dispatcher}

AEM Screens播放器/设备也使用经过身份验证的会话来访问发布实例中的资源。 因此，当您有多个发布实例时，请求应始终转到同一发布实例，以便经过身份验证的会话对来自AEM Screens播放器/设备的所有请求有效。

请按照以下步骤为AEM Screens项目配置调度程序。

### 启用粘滞会话{#enable-sticky-session}

如果要使用由单个调度程序前置的多个发布实例，则必须更新`dispatcher.any`文件以启用粘性

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

如果您有一个由一个调度程序前置的发布实例，则在调度程序上启用粘性将无济于事，因为负载平衡器可能会向调度程序发送每个请求。 在这种情况下，单击&#x200B;**粘性**&#x200B;字段中的&#x200B;**启用**，以在负载平衡器级别启用它，如下图所示：

![图像](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

例如，如果您使用的是AWS ALB，请参考[目标组，以便在ALB级别启用粘性。 ](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)启用1天的粘性。

### 第1步：配置客户端标头{#step-configuring-client-headers}

在`/clientheaders`部分添加以下内容：

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 第2步：配置Screens过滤器{#step-configuring-screens-filters}

要配置Screens过滤器，请将以下内容添加到&#x200B;***/filter***。

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

### 第3步：禁用调度程序缓存{#step-disabling-dispatcher-cache}

禁用&#x200B;***/content/screens路径***&#x200B;的调度程序缓存。

Screens播放器使用经过身份验证的会话，因此调度程序不缓存任何屏幕播放器请求。`channels/assets`

要为资产启用缓存，以便从调度程序缓存中提供资产，您必须：

* 在`/cache`节中添加`/allowAuthorization 1`
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
