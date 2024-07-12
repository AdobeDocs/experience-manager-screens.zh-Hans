---
title: 配置和部署AEM Screens
description: AEM Screens Player适用于Android&amp；trade；、Chrome操作系统、iOS和Windows。 了解AEM Screens的配置和部署。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 1%

---

# 配置和部署AEM Screens {#configuring-and-deploying-aem-screens}

本页说明如何在设备上安装和配置Screens播放器。

## 服务器配置 {#server-configuration}

>[!IMPORTANT]
>
>AEM Screens播放器不使用跨站点请求伪造(CSRF)令牌。 因此，要将AEM服务器配置为可用于AEM Screens，请通过允许空反向链接跳过反向链接过滤器。

## 运行状况检查框架 {#health-check-framework}

运行状况检查框架让用户在运行AEM Screens项目之前检查是否设置了两个必要的配置。

它允许用户验证以下两项配置检查以运行AEM Screens项目，即检查以下两个筛选器的状态：

1. **允许空反向链接**
2. **https**

请按照以下步骤检查是否已为AEM Screens启用这两个重要配置：

1. 导航到[Adobe Experience Manager Web控制台Sling运行状况检查](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=)。

   ![资源](assets/health-check1.png)


2. 单击&#x200B;**执行选定的运行状况检查**，以便您可以为上面列出的两个属性运行验证。

   如果两个筛选器都已启用，则&#x200B;**Screens配置运行状况服务**&#x200B;会将&#x200B;**Result**&#x200B;显示为&#x200B;**OK**，并将两个配置都显示为已启用。

   ![资源](assets/health-check2.png)

   如果禁用了一个或两个过滤器，则会为用户显示警报，如下图所示。

   如果两个过滤器都处于禁用状态，则会显示以下警报：
   ![资源](assets/health-check3.png)

>[!NOTE]
>
>* 要启用&#x200B;**Apache Sling引用过滤器**，请参阅[允许空引用请求](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)。
>* 要启用&#x200B;**HTTP**&#x200B;服务，请参阅[基于Apache Felix Jetty的HTTP服务](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service)。

### 先决条件 {#prerequisites}

以下要点有助于配置和AEM服务器，以便随时用于AEM Screens。

#### 允许空反向链接请求 {#allow-empty-referrer-requests}

1. 通过AEM实例>锤子图标> **操作** > **Web控制台**&#x200B;导航到&#x200B;**Adobe Experience Manager Web控制台配置**。

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web控制台配置**&#x200B;打开。 搜索Sling反向链接。

   要搜索sling反向链接属性，请在&#x200B;**Mac**&#x200B;中按&#x200B;**Command+F**，在&#x200B;**Windows**&#x200B;中按&#x200B;**Control+F**。

1. 选中&#x200B;**允许为空**&#x200B;选项，如下图所示。

   ![图像](assets/config/empty-ref2.png)

1. 单击&#x200B;**保存**&#x200B;以启用Apache Sling引用过滤器允许为空。


#### 基于Apache Felix Jetty的HTTP服务 {#allow-apache-felix-service}

1. 通过AEM实例>锤子图标> **操作** > **Web控制台**&#x200B;导航到&#x200B;**Adobe Experience Manager Web控制台配置**。

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web控制台配置**&#x200B;打开。 搜索基于Apache Felix Jetty的HTTP服务

   若要搜索此属性，请按&#x200B;**Command+F**&#x200B;以搜索&#x200B;**Mac**，然后按&#x200B;**Control+F**&#x200B;以搜索&#x200B;**Windows**。

1. 选中&#x200B;**启用HTTP**&#x200B;选项，如下图所示。

   ![图像](assets/config/config-1.png)

1. 单击&#x200B;**保存**&#x200B;以启用&#x200B;*Http*&#x200B;服务。

#### 为AEM Screens启用Touch UI {#enable-touch-ui-for-aem-screens}

AEM Screens需要使用TOUCH UI，不能用于Adobe Experience Manager (AEM)的经典UI。

1. 导航到`*<yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*`
1. 确保&#x200B;**默认创作UI模式**&#x200B;设置为&#x200B;**触控**，如下图所示

或者，您也可以使用AuthorInstance *>*&#x200B;工具（锤子图标）> **操作** > **Web控制台**&#x200B;执行相同的设置，并搜索&#x200B;**WCM创作UI模式服务**。

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>您始终可以使用用户首选项为特定用户启用经典UI。

#### NOSAMPLECONTENT运行模式中的AEM {#aem-in-nosamplecontent-runmode}

在生产环境中运行AEM会使用&#x200B;**NOSAMPLECONTENT**&#x200B;运行模式。 从删除&#x200B;*X-Frame-Options=SAMEORIGIN*&#x200B;标头（在其他响应标头部分）

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`。

AEM Screens Player需要移除该选项才能播放在线渠道。

#### 密码限制 {#password-restrictions}

如果对&#x200B;***DeviceServiceImpl***&#x200B;进行了最新更改，则无需删除密码限制。

您可以从下面的链接配置&#x200B;***DeviceServiceImpl***，以便在为屏幕设备用户创建密码时启用密码限制：

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

按照以下步骤配置&#x200B;***DeviceServiceImpl***：

1. 通过您的AEM实例>锤子图标> **操作** > **Web控制台**&#x200B;导航到&#x200B;**Adobe Experience Manager Web控制台配置**。

1. **Adobe Experience Manager Web控制台配置**&#x200B;打开。 搜索`*deviceservice*`。 要搜索属性，请按&#x200B;**Command+F**&#x200B;键搜索macOS，按&#x200B;**Control+F**&#x200B;键搜索Microsoft® Windows。

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher 配置 {#dispatcher-configuration}

要了解如何为AEM Screens项目配置Dispatcher，请参阅[为AEM Screens项目配置Dispatcher](dispatcher-configurations-aem-screens.md)。

#### Java™编码 {#java-encoding}

将&#x200B;***Java™编码***&#x200B;设置为Unicode。 例如，`*Dfile.encoding=Cp1252*`不起作用。

>[!NOTE]
>
>在生产中使用用于AEM Screens Server的HTTPS。
