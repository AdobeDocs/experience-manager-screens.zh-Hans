---
title: 配置和部署AEM Screens
seo-title: 配置和部署 Screens
description: AEM Screens播放器可用于Android、Chrome OS、iOS和Windows。 本页介绍了AEM Screens的配置和部署，并总结了播放器设备的高／低选择准则。
seo-description: AEM Screens播放器可用于Android、Chrome OS、iOS和Windows。 本页介绍了AEM Screens的配置和部署，并总结了播放器设备的高／低选择准则。
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Configuring and Deploying AEM Screens {#configuring-and-deploying-aem-screens}

本页说明如何在您的设备上安装和配置Screens播放器。

## 安装AEM Screens播放器 {#installing-aem-screens-player}

AEM Screens播放器可用于Android、Chrome OS、iOS和Windows。

要下载 **AEM Screens Player**，请访问 [**AEM 6.5播放器下载页**](https://download.macromedia.com/screens/) 。

>[!NOTE]
>
>下载最新的播放器(*.exe*)后，请按照播放器上的步骤完成临时安装：
>
>1. 长按左上角以打开管理面板。
>1. 从左侧 **操作菜单导航到** “配置”，然后在 **Server** 中输入AEM实例的位置地址，然后单击“保 **存”**。
>1. 单击左侧操 **作菜单中** 的“注册”链接和以下步骤以完成设备注册过程。
>



### 其他资源 {#additional-resources}

有关详细信息，请参阅以下主题：

* 要下载Android Player，请访 **问Google Play**。 要了解如何实施Android监视程序，请参阅 [实施Android播放器](implementing-android-player.md)。

* 要实施Chrome OS Player，请参阅 [Chrome管理控制台](implementing-chrome-os-player.md) ，以了解更多信息。

* 要配置AEM Screens Windows播放器，请参阅实 [施Windows播放器](implementing-windows-player.md)。

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**重要信息**：
>
>AEM Screens播放器不使用跨站点请求伪造(CSRF)令牌。 因此，要配置AEM服务器并使其准备好用于AEM Screens，请通过允许空引用来跳过引用过滤器。

### 前提条件 {#prerequisites}

以下要点可帮助配置AEM服务器并使其准备好用于AEM Screens:

#### 允许空的引用请求 {#allow-empty-referrer-requests}

1. 通过AEM实例—&gt;锤子图标—&gt;操作—&gt; web控制台，导航到**Adobe Experience Manager Web Console配置** ********。

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **Adobe Experience Manager Web Console配置将打开** 。 搜索sling引用。

   要搜索sling referrer属性，请按 **Command+F** ( **Mac** )和 **Control+F(****** Windows)。

   ![screen_shot_2019-07-31at91728am](assets/screen_shot_2019-07-31at91728am.png)

1. 选中“允许空”**选项，如下图所示。

   ![screen_shot_2019-07-31at91807am](assets/screen_shot_2019-07-31at91807am.png)

1. 单击 **保存** ，以启用Apache Sling引用过滤器允许空。

#### 为AEM Screens启用触屏UI {#enable-touch-ui-for-aem-screens}

AEM Screens需要触屏UI，并且不能用于Adobe Experience Manager(AEM)的经典UI。

1. 导航到 *&lt;yourAuthorInstance&gt;/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. 确保将“默 **认创作UI** ”模式设 **置为“TOUCH**”，如下图所示

或者，您也可以使用*&lt;yourAuthorInstance&gt; *-&gt;工具* （锤子图标）* -&gt; **Operations** -&gt;** Web Console**执行相同的设置，并搜索 **WCM创作UI模式服务**。

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>您始终可以使用用户首选项为特定用户启用经典UI。

#### NOSAMPLECONTENT运行模式中的AEM {#aem-in-nosamplecontent-runmode}

在生产中运行AEM使用 **NOSAMPLECONTENT运行模式** 。 从&#x200B;*RemovetheX-Frame-Options=SAMEORIGIN* header（在其他响应头部分）

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

AEM Screens播放器必须具备此功能才能播放联机渠道。

#### 密码限制 {#password-restrictions}

对 ***DeviceServiceImpl进行最新更改***，您不必删除密码限制。

您可以通过 ***以下链接配置DeviceServiceImpl*** ，以在为屏幕设备用户创建口令时启用口令限制：

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

请按照以下步骤配置 ***DeviceServiceImpl***:

1. 通过AEM实例—&gt;锤子图标—&gt;操作—&gt; web控制台，导航到**Adobe Experience Manager Web Console配置** ********。

1. **Adobe Experience Manager web控制台配置**打开。 搜索deviceservice. 要搜索属性，请 **按Command+F** ( **Mac)和** Control+F(Windows) ********(Windows)。

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher Configuration {#dispatcher-configuration}

要了解如何为AEM Screens项目配置调度程序，请参阅为AEM Screens项 [目配置调度程序](dispatcher-configurations-aem-screens.md)。

#### Java编码 {#java-encoding}

将 ***Java编码设置为*** Unicode。 例如， *Dfile.encoding=Cp1252* 将不起作用。

>[!NOTE]
>
>**推荐:**
>
>建议在生产使用中对AEM Screens服务器使用HTTPS。
