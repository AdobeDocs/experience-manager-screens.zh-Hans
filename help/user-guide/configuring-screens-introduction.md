---
title: 配置和部署AEM Screens
seo-title: 配置和部署 Screens
description: AEM Screens播放器可用于Android、Chrome OS、iOS和Windows。 本页介绍了AEM Screens的配置和部署，并概括了播放器设备的h/w选择指南。
seo-description: AEM Screens播放器可用于Android、Chrome OS、iOS和Windows。 本页介绍了AEM Screens的配置和部署，并概括了播放器设备的h/w选择指南。
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 1%

---


# Configuring and Deploying AEM Screens {#configuring-and-deploying-aem-screens}

本页说明如何在设备上安装和配置Screens播放器。

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**重要信息**：
>
>AEM Screens播放器未使用跨站点请求伪造(CSRF)令牌。 因此，为了配置和AEM服务器以准备用于AEM Screens，请跳过推荐人过滤器，允许空推荐人。

## 运行状况检查框架 {#health-check-framework}

运行状况检查框架允许用户在运行AEM Screens项目之前检查是否设置了两个必要的配置。

它允许用户验证以下两个配置检查以运行AEM Screens项目，即检查以下两个过滤器的状态：

1. **允许空推荐人**
2. **https**

请按照以下步骤检查是否为AEM Screens启用了以下两个重要配置：

1. 导航到 [Adobe Experience ManagerWeb控制台Sling运行状况检查](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=)。

   ![资产](assets/health-check1.png)


2. 单击“执 **行所选运行状况检查** ”以对以上列出的两个属性运行验证。

   如果同时启用了这两个过滤器, **Screens Configuration Health Service** (Screens配置 **运行状况服务)****将结果** 显示为OK，同时启用这两个配置。

   ![资产](assets/health-check2.png)

   如果一个或两个过滤器被禁用，则会为用户显示警报，如下图所示。

   以下警报会显示是否同时禁用了这两个过滤器:
   ![资产](assets/health-check3.png)

>[!NOTE]
>
>* 要启用Apache **Sling推荐人过滤器**，请参 [阅允许空推荐人请求](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)。
>* 要启用HTTP **服务** ，请参 [阅基于Apache Felix Jetty的HTTP服务](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service)。


### 前提条件 {#prerequisites}

以下要点有助于配置和AEM服务器以随时供AEM Screens使用。

#### 允许空推荐人请求 {#allow-empty-referrer-requests}

1. 通过AEM **实例** —>锤子图标—>操作—> Web Console **，导航到** Adobe Experience Manager **Web Console** Configuration。

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience ManagerWeb控制台配置** 打开。 搜索吊带推荐人。

   要搜索sling推荐人属性， **请按Command** +F( **Mac)****和** Control+F(Windows ****)。

1. 选中“ **允许空** ”选项，如下图所示。

   ![图像](assets/config/empty-ref2.png)

1. 单击 **“保存** ”以启用Apache Sling推荐人过滤器“允许为空”。


#### 基于Apache Felix Jetty的HTTP服务 {#allow-apache-felix-service}

1. 通过AEM **实例** —>锤子图标—>操作—> Web Console **，导航到** Adobe Experience Manager **Web Console** Configuration。

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience ManagerWeb控制台配置** 打开。 搜索基于Apache Felix Jetty的HTTP服务。

   要搜索此属性， **请按Command** +F( **Mac)和** Control **+F(** Windows) **组合**&#x200B;键。

1. 选中 **“启用** HTTP”选项，如下图所示。

   ![图像](assets/config/config-1.png)

1. 单击 **“保存** ”以启 *用http* 服务。

#### 为AEM Screens启用触屏UI {#enable-touch-ui-for-aem-screens}

AEM Screens需要触屏UI，并且不能用于Adobe Experience Manager(AEM)的经典UI。

1. 导航 *到&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. 确保将 **默认的创作UI** 模式 **设置**&#x200B;为TOUCH，如下图所示

或者，您也可以使用AuthorInstance -> *工具* （锤子图标）-> Operations -> **Web Console执行同** 样的设置，并搜索 ******** WCM创作UI模式Service 。

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>您始终可以使用用户首选项为特定用户启用经典UI。

#### AEM在NOSAMPLECONTENT运行模式中 {#aem-in-nosamplecontent-runmode}

在生产中运行AEM使 **用NOSAMPLECONTENT** runmode。 删除 *X-Frame-Options=SAMEORIGIN* header（在其他响应头部分中）

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`。

这是AEM Screens播放器播放在线渠道所必需的。

#### 密码限制 {#password-restrictions}

对DeviceServiceImpl进 ***行最新更***&#x200B;改后，您无需删除密码限制。

您可以通 ***过以下链接*** 配置DeviceServiceImpl，以在为屏幕设备用户创建口令时启用口令限制：

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

请按照以下步骤配 ***置DeviceServiceImpl***:

1. 通过AEM **实例** —>锤子图标—>操作—> Web Console **，导航到** Adobe Experience Manager **Web Console** Configuration。

1. **Adobe Experience ManagerWeb控制台配置**打开。 搜索 *deviceservice*。 要搜索属性，请 **按Command** +F( **Mac****)和** Control+F(Windows ****)。

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher Configuration {#dispatcher-configuration}

要了解如何为AEM Screens项目配置调度程序，请参 [阅为AEM Screens项目配置调度程序](dispatcher-configurations-aem-screens.md)。

#### Java编码 {#java-encoding}

将Java编 ***码设置为*** Unicode。 例如， *Dfile.encoding=Cp1252* 将不起作用。

>[!NOTE]
>
>**推荐:**
>
>建议在生产使用中对AEM Screens服务器使用HTTPS。








