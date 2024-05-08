---
title: 适用于AEM Screens的Dispatcher配置
description: 本页重点介绍了为AEM Screens项目配置Dispatcher的准则。
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# 适用于AEM Screens的Dispatcher配置{#dispatcher-configurations-for-aem-screens}

Dispatcher是Adobe Experience Manager的缓存和/或负载平衡工具。

以下页面提供了为AEM Screens项目配置Dispatcher的准则。

>[!NOTE]
>
>如果Dispatcher可用，可以通过在Dispatcher规则中进行筛选来阻止与注册servlet的连接。
>
>如果没有Dispatcher，请在OSGi组件列表中禁用注册servlet。

在为AEM Screens项目配置Dispatcher之前，请先了解Dispatcher。
请参阅 [配置Dispatch](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration) 以了解更多详细信息。

## 为清单版本v2配置Dispatcher {#configuring-dispatcher}

>[!IMPORTANT]
>以下Dispatcher配置仅适用于清单版本v2。 请参阅 [清单版本v3的Dispatcher配置](#configuring-dispatcherv3) 清单版本v3。

AEM Screens播放器或设备使用经过身份验证的会话来访问发布实例中的资源。 因此，当您有多个发布实例时，请求应始终转到同一发布实例，以便经过身份验证的会话对来自AEM Screens播放器/设备的所有请求有效。

按照以下步骤为AEM Screens项目配置Dispatcher 。

### 启用粘性会话 {#enable-sticky-session}

如果要使用由单个Dispatcher提前的多个发布实例，请更新 `dispatcher.any` 文件以启用粘性。

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

如果您有一个发布实例由一个Dispatcher承载，则在Dispatcher上启用粘性没有帮助，因为负载平衡器可能会将每个请求发送到Dispatcher。 在这种情况下，请单击 **启用** 在 **粘性** 字段以将其在负载平衡器级别启用，如下图所示：

![图像](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

例如，如果您使用的是AWS ALB，请参阅 [应用程序负载平衡器的目标组](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) 用于在ALB级别启用粘性。 启用一天的粘性。

### 步骤1：配置客户端标头 {#step-configuring-client-headers}

将以下内容添加到 `/clientheaders`部分：

**X-Request-With**

**X-SET-HEARTBEAT**

**X请求命令**

### 步骤2：配置Screens过滤器 {#step-configure-screens-filters}

要配置Screens筛选器，请将以下内容添加到 ***/filter***.

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

### 步骤3：禁用Dispatcher缓存 {#step-disabling-dispatcher-cache}

禁用的Dispatcher缓存 ***/content/screens路径***.

Screens播放器使用经过身份验证的会话，因此Dispatcher不会缓存播放器请求的 `channels/assets`.

要为资产启用缓存，以便从Dispatcher缓存中提供资产，请执行以下操作：

* 添加 `/allowAuthorization 1` 在 `/cache` 部分
* 将以下规则添加到 `/rules` 部分 `/cache`

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

确保在发布实例前面的调度程序中允许这些过滤器和缓存规则以便Screens正常工作。

### 清单版本v3的先决条件{#prerequisites3}

在为AEM Screens配置Dispatcher（清单版本v3）之前，请遵循以下两个先决条件：

* 确保您使用 `v3 manifests`. 导航到 `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` 并确保 `Enable ContentSync Cache` 未选中。

* 确保Dispatcher刷新代理配置在 `/etc/replication/agents.publish/dispatcher1useast1Agent` 在发布实例中。

  ![图像](/help/user-guide/assets/dispatcher/dispatcher-1.png)

  ![图像](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### 过滤器  {#filter-v3}

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

* 添加 `/allowAuthorized "1"` 到 `/cache` 中的部分 `publish_farm.any`.

* 所有AEM Screens播放器都使用经过身份验证的会话连接到AEM（创作/发布）。 现成的Dispatcher不会缓存这些URL，因此您应该启用这些URL。

* 添加 `statfileslevel "10"` 到 `/cache` 中的部分 `publish_farm.any`
这支持从缓存docroot中缓存最多十个级别，并在发布内容时相应地使其失效，而不是使所有内容失效。 您可以根据内容结构的深度来更改此级别

* 将以下内容添加到 `/invalidate section in publish_farm.any`

  ```
  /0003 {
      /glob "*.json"
      /type "allow"
  }
  ```

* 将以下规则添加到 `/rules` 中的部分 `/cache` 在 `publish_farm.any` 或包含在 `publish_farm.any`：

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

### 为segments.js添加失效规则 {#invalidsegmentjs}

如果您要在AEM Screens中使用定向促销活动，则 `segments.js file` 当您在AEM上添加和发布新区段时，由Dispatcher提供的服务必须失效。 如果没有此失效规则，新的定向营销活动将无法在AEM Screens Player上正常运行（它会显示默认内容）。

* 添加失效规则到 `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. 以下是要添加的规则：

```
    /invalidate {
                        .
                        .
                        /0004 {
                               /glob "conf/<project-name>/settings/wcm/.js"
                               /type "allow"
                        }
                }
```

* 此规则确保 `segments.js` 文件失效，修改时获取最新文件。
