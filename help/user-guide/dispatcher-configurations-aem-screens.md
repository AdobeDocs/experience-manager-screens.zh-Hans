---
title: 适用于AEM Screens的调度程序配置
seo-title: 适用于AEM Screens的调度程序配置
description: 本页重点介绍为AEM Screens项目配置调度程序的准则。
seo-description: 本页重点介绍为AEM Screens项目配置调度程序的准则。
feature: 管理屏幕
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 449f59f25f1164f1e638921192c538ac46d781d3
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 2%

---

# 适用于AEM Screens的调度程序配置{#dispatcher-configurations-for-aem-screens}

Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。

以下页面提供了为AEM Screens项目配置调度程序的准则。

>[!NOTE]
>
>如果调度程序可用，则可以通过在调度程序规则中进行过滤来阻止与注册Servlet的连接。
>
>如果没有调度程序，请在OSGi组件列表中禁用注册Servlet。

在为AEM Screens项目配置Dispatcher之前，您必须先了解Dispatcher。
有关更多详细信息，请参阅[配置Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)。

## 为清单版本v2配置Dispatcher {#configuring-dispatcher}

>[!IMPORTANT]
>以下Dispatcher配置仅适用于清单版本v2。 有关清单版本v3的信息，请参阅[清单版本v3](#configuring-dispatcherv3)的调度程序配置。

AEM Screens播放器或设备还使用经过身份验证的会话来访问发布实例中的资源。 因此，当您有多个发布实例时，请求应始终转到同一发布实例，以便经过身份验证的会话对来自AEM Screens播放器/设备的所有请求都有效。

请按照以下步骤为AEM Screens项目配置Dispatcher。

### 启用置顶会话 {#enable-sticky-session}

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

### 步骤1:配置客户端标头 {#step-configuring-client-headers}

在`/clientheaders`部分中添加以下内容：

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 步骤2:配置Screens过滤器 {#step-configuring-screens-filters}

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

### 步骤3:禁用Dispatcher缓存 {#step-disabling-dispatcher-cache}

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

## 为清单版本v3配置Dispatcher{#configuring-dispatcherv3}

请确保在位于发布实例前方的调度程序中允许这些过滤器和缓存规则，以便Screens正常运行。

### 清单版本v3的先决条件{#prerequisites3}

在为AEM Screens配置Dispatcher（清单版本v3）之前，请确保遵循以下两个先决条件：

* 确保使用`v3 manifests`。 导航到`https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`并确保未选中`Enable ContentSync Cache`。

* 确保在发布实例的`/etc/replication/agents.publish/dispatcher1useast1Agent`处配置调度程序刷新代理。

   ![图像](/help/user-guide/assets/dispatcher/dispatcher-1.png)

### 筛选器  {#filter-v3}

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
#/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
/0222 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" } ## add any other formats required for your project here
 
## # Enable clientlibs proxy servlet
/0230 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### 缓存规则 {#cache-rules-v3}

* 将`/allowAuthorized "1"`添加到`publish_farm.any`中的`/cache`部分。

* 所有Screens播放器都将使用经过身份验证的会话连接到AEM（创作/发布）。 现成的Dispatcher不会缓存这些url，因此我们应该启用这些url。

* 将`statfileslevel "10"`添加到`publish_farm.any`中的`/cache`部分
这将支持从缓存缓存中缓存多达10个级别，并在发布内容时相应地使其失效，而不是使所有内容失效。 根据内容结构的深度随时更改此级别

* 将以下内容添加到`/invalidate section in publish_farm.any`

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* 将以下规则添加到`publish_farm.any`中`/cache`的`/rules`部分或`publish_farm.any`中包含的文件中：

   ```
   ## Don't cache CSRF login tokens
   /0001
       {
       /glob "/libs/granite/csrf/token.json"
       /type "deny"
       }
   ## Allow Dispatcher Cache for Screens channels
   /0002
       {
           /glob "/content/screens/*.html"
           /type "allow"
       }
   ## Allow Dispatcher Cache for Screens offline manifests
   /0003
       {
       /glob "/content/screens/*.manifest.json"
       /type "allow"
       }
   ## Allow Dispatcher Cache for Assets
   /0004
       {
   
       /glob "/content/dam/*"
       /type "allow"
       }
   ## Disable Dispatcher Cache for Screens devices json
   /0005
       {
       /glob "/home/users/screens/*.json"
       /type "deny"
       }
   ## Disable Dispatcher Cache for Screens svc json
   /0006
       {
       /glob "/content/screens/svc.json"
       /type "deny"
       }
   ```
