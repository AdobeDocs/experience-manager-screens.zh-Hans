---
title: 配置和部署AEM Screens
seo-title: 配置和部署 Screens
description: AEM Screens播放器适用于Android、Chrome OS、iOS和Windows。 本页介绍了AEM Screens的配置和部署，并概述了播放器设备的高/低选择准则。
seo-description: AEM Screens播放器适用于Android、Chrome OS、iOS和Windows。 本页介绍了AEM Screens的配置和部署，并概述了播放器设备的高/低选择准则。
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 1%

---


# 配置和部署AEM Screens {#configuring-and-deploying-aem-screens}

本页介绍如何在您的设备上安装和配置Screens播放器。

## 服务器配置{#server-configuration}

>[!NOTE]
>
>**重要信息**：
>
>AEM Screens播放器不使用跨站点请求伪造(CSRF)令牌。 因此，要配置和AEM服务器以便准备好用于AEM Screens，请通过允许空反向链接来跳过反向链接过滤器。

## 运行状况检查框架{#health-check-framework}

运行状况检查框架允许用户在运行AEM Screens项目之前检查是否设置了两个必需的配置。

它允许用户验证以下两个配置检查以运行AEM Screens项目，即检查以下两个过滤器的状态：

1. **允许空反向链接**
2. **https**

请按照以下步骤检查是否已为AEM Screens启用这两个重要配置：

1. 导航至[Adobe Experience Manager Web Console Sling运行状况检查](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=)。

   ![资产](assets/health-check1.png)


2. 单击&#x200B;**执行选定的运行状况检查**&#x200B;以对上面列出的两个属性运行验证。

   如果同时启用了这两个过滤器，则&#x200B;**Screens Configuration Health Service**&#x200B;将&#x200B;**Result**&#x200B;显示为&#x200B;**OK**，并同时启用这两个配置。

   ![资产](assets/health-check2.png)

   如果禁用一个或两个过滤器，则会为用户显示警报，如下图所示。

   以下警报会显示是否同时禁用了这两个过滤器：
   ![资产](assets/health-check3.png)

>[!NOTE]
>
>* 要启用&#x200B;**Apache Sling反向链接过滤器**，请参阅[允许空反向链接请求](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)。
>* 要启用&#x200B;**HTTP**&#x200B;服务，请参阅[Apache Felix Jetty Based HTTP服务](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service)。


### 前提条件 {#prerequisites}

以下要点可帮助配置和AEM服务器以准备好用于AEM Screens。

#### 允许空反向链接请求{#allow-empty-referrer-requests}

1. 通过AEM实例导航到&#x200B;**Adobe Experience Manager Web控制台配置** —>锤子图标 — > **操作** —> **Web控制台**。

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web控制台** 配置打开。搜索sling反向链接。

   要搜索Sling反向链接属性，请按&#x200B;**Command+F**（对于&#x200B;**Mac**）和&#x200B;**Control+F**（对于&#x200B;**Windows**）。

1. 选中&#x200B;**允许空**&#x200B;选项，如下图所示。

   ![图像](assets/config/empty-ref2.png)

1. 单击&#x200B;**Save**&#x200B;以启用Apache Sling反向链接过滤器允许为空。


#### 基于Apache Felix Jetty的HTTP服务{#allow-apache-felix-service}

1. 通过AEM实例导航到&#x200B;**Adobe Experience Manager Web控制台配置** —>锤子图标 — > **操作** —> **Web控制台**。

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web控制台** 配置打开。搜索基于Apache Felix Jetty的HTTP服务。

   要搜索此属性，请按&#x200B;**Command+F**（对于&#x200B;**Mac**）和&#x200B;**Control+F**（对于&#x200B;**Windows**）。

1. 选中&#x200B;**启用HTTP**&#x200B;选项，如下图所示。

   ![图像](assets/config/config-1.png)

1. 单击&#x200B;**Save**&#x200B;以启用&#x200B;*http*&#x200B;服务。

#### 为AEM Screens启用触屏UI {#enable-touch-ui-for-aem-screens}

AEM Screens需要触屏UI，并且无法用于Adobe Experience Manager(AEM)的经典UI。

1. 导航到&#x200B;*&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. 确保将&#x200B;**默认创作UI模式**&#x200B;设置为&#x200B;**TOUCH**，如下图所示

或者，您也可以使用AuthorInstance *->*&#x200B;工具（锤子图标） — > **操作** -> **Web控制台**&#x200B;执行相同的设置，并搜索&#x200B;**WCM创作UI模式服务**。

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>您始终可以使用用户首选项为特定用户启用经典UI。

#### AEM在NOSAMPLECONTENT运行模式{#aem-in-nosamplecontent-runmode}中

在生产中运行AEM使用&#x200B;**NOSAMPLECONTENT**&#x200B;运行模式。 从&#x200B;**

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`。

AEM Screens播放器需要此参数才能播放在线渠道。

#### 密码限制{#password-restrictions}

对&#x200B;***DeviceServiceImpl***&#x200B;进行最新更改后，您不必删除密码限制。

您可以从以下链接配置&#x200B;***DeviceServiceImpl*** ，以在为屏幕设备用户创建密码时启用密码限制：

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

请按照以下步骤配置&#x200B;***DeviceServiceImpl***:

1. 通过AEM实例导航到&#x200B;**Adobe Experience Manager Web控制台配置** —>锤子图标 — > **操作** —> **Web控制台**。

1. **Adobe Experience Manager Web控制台** 配置打开。搜索&#x200B;*deviceservice*。 要搜索属性，请按&#x200B;**Command+F**（对于macOS）和&#x200B;**Control+F**（对于Microsoft Windows）。

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### 调度程序配置{#dispatcher-configuration}

要了解如何为AEM Screens项目配置Dispatcher，请参阅[为AEM Screens项目配置Dispatcher](dispatcher-configurations-aem-screens.md)。

#### Java编码{#java-encoding}

将&#x200B;***Java编码***&#x200B;设置为Unicode。 例如， *Dfile.encoding=Cp1252*&#x200B;将不起作用。

>[!NOTE]
>**推荐:**
>建议在生产使用中对AEM Screens Server使用HTTPS。








