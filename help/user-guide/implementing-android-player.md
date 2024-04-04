---
title: 实施Android Player
seo-title: Implementation of Android Player
description: 请参阅此页面，了解Android Watchdog的实施情况，该解决方案可在发生崩溃时恢复播放器。
seo-description: Follow this page to learn implementation of Android Watchdog, a solution to recover the player from crashes.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 0%

---

# 实施Android Player {#implementing-android-player}

本节介绍如何配置Android播放器。 它提供了有关配置文件和可用选项的信息，以及开发和测试时要使用的设置的建议。

此外， **监视程序** 是一个用于从崩溃中恢复播放器的解决方案。 应用程序需要向监视程序服务注册自己，然后定期向服务发送其处于活动状态的消息。 如果watchdog服务在规定的时间内未收到保持活动状态消息，该服务将尝试重新启动设备以进行干净恢复（如果它有足够的权限）或重新启动应用程序。

## 安装Android Player {#installing-android-player}

要实施Android Player for AEM Screens，请安装适用于AEM Screens的Android Player。

访问 [**AEM 6.5播放器下载**](https://download.macromedia.com/screens/) 页面。

### 为AEM Screens 6.5.5 Service Pack设置环境 {#fp-environment-setup}

>[!NOTE]
>如果您使用AEM Screens 6.5.5 Service Pack，则必须为Android player设置环境。

设置 **登录令牌Cookie的SameSite属性** 从 **Lax** 到 **无** 从 **Adobe Experience Manager Web控制台配置** 在所有AEM创作和发布实例上。

应遵循以下步骤：

1. 导航到 **Adobe Experience Manager Web控制台配置** 使用 `http://localhost:4502/system/console/configMgr`.

1. 搜索 *Granite令牌身份验证处理程序Adobe*.

1. 设置 **登录令牌Cookie的SameSite属性** 从 **Lax** 到 **无**.
   ![图像](/help/user-guide/assets/granite-updates.png)

1. 单击&#x200B;**保存**。


### Ad Hoc方法 {#ad-hoc-method}

通过Ad-Hoc方法，可安装最新的Android Player (*.exe*)。 访问 [**AEM 6.5播放器下载**](https://download.macromedia.com/screens/) 页面。

下载应用程序后，请按照播放器上的步骤完成临时安装：

1. 长按左上角以打开管理面板。
1. 导航到 **配置** 从左侧操作菜单中，输入要连接的AEM实例的位置（地址），然后单击 **保存**.

1. 导航至 **设备** **注册** 左侧操作菜单中的链接，用于检查设备注册过程的状态。

>[!NOTE]
>
>如果 **状态** 是 **已注册**，您会注意到 **设备ID** 字段将被填充。
>
>如果 **状态** 是 **未注册**，您可以使用 **令牌** 注册设备。

## 实施Android监视程序 {#implementing-android-watchdog}

由于Android的架构，重新启动设备要求应用程序具有系统权限。 为此，您需要使用制造商的签名密钥对应用程序进行签名，否则，监视程序将重新启动播放器应用程序而不重新启动设备。

### 使用制造商密钥的Android应用程序标牌 {#signage-of-android-apks-using-manufacturer-keys}

访问Android的某些特权API，例如 *PowerManager* 或 *Hdmicontrolservices*，您需要使用制造商的密钥对android apk进行签名。

>[!CAUTION]
>
>先决条件：
>
>您应该先安装Android SDK，然后再执行以下步骤。

按照以下步骤使用制造商的密钥对Android应用程序进行签名：

1. 从Google Play或下载应用程序 [AEM Screens播放器下载](https://download.macromedia.com/screens/) 页面
1. 从制造商处获取平台密钥，以获取 *pk8* 和 *pem* 文件

1. 使用“查找~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;，在android sdk中找到apksigner工具
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. 在android sdk中查找zip对齐工具的路径
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. 安装 ***aemscreensaligned.apk*** 将adb install用于设备

## 了解Android监视程序服务 {#android-watchdog-services}

使用将跨Android监视程序服务作为Cordova插件实现 *警报管理器*.

下图显示了监视程序服务的实现：

![chlimage_1-31](assets/chlimage_1-31.png)

**1. 初始化** 在初始化cordova插件时，将检查权限以查看我们是否具有系统权限，从而检查是否具有Reboot权限。 如果满足这两个条件，则会创建挂起的重启意图，否则会创建挂起的重启应用程序意图（基于其启动活动）。

**2. 保持活动状态计时器** 保持活动状态计时器用于每15秒触发一次事件。 在该情况下，您需要取消现有的挂起意图（重新启动或重新启动应用程序）并在以后的60秒内注册新的挂起意图（实际上是推迟重新启动）。

>[!NOTE]
>
>在Android中， *警报管理器* 用于注册 *pendingIntents* 即使应用程序崩溃并且其警报交付与API 19 (Kitkat)不精确也可以执行。 在计时器的间隔和 *警报管理器的* *pendingIntent的* 警报。

**3. 应用程序崩溃** 如果发生崩溃，则在AlarmManager中注册的pendingIntent for Reboot将不再重置，因此它将执行应用程序重新启动或重新启动（取决于初始化cordova插件时可用的权限）。

## 批量配置Android Player {#bulk-provision-android-player}

批量推出Android播放器时，需要配置播放器以指向AEM实例，并配置其他资产，而无需在管理员UI中手动输入这些资产。

>[!NOTE]
>此功能在Android播放器42.0.372上可用。

执行以下步骤，在Android播放器中允许批量配置：

1. 创建名为的配置JSON文件 `player-config.default.json`.
请参阅 [示例JSON策略](#example-json) 以及描述各种 [策略属性](#policy-attributes).

1. 使用MDM、ADB或Android Studio文件资源管理器将此策略JSON文件拖放到 *sdcard* Android设备上的文件夹。

1. 部署文件后，使用MDM安装播放器应用程序。

1. 当播放器应用程序启动时，它将读取此配置文件，并指向相应的AEM服务器，可以在其中注册并随后对其进行控制。

   >[!NOTE]
   >此文件为 *只读* 首次启动应用程序时，无法用于后续配置。 如果在删除配置文件之前启动播放器，则只需在设备上卸载并重新安装应用程序即可。

### 策略属性 {#policy-attributes}

下表汇总了策略属性并提供了示例策略JSON以供参考：

| **策略名称** | **用途** |
|---|---|
| *server* | Adobe Experience Manager服务器的URL。 |
| *resolution* | 设备的分辨率。 |
| *rebootSchedule* | 重新启动计划适用于所有平台。 |
| *enableAdminUI* | 启用管理UI以在站点上配置设备。 设置为 *false* 在完全配置并投入生产后。 |
| *enableOSD* | 为用户启用通道切换器UI以在设备上切换通道。 考虑将设置为 *false* 在完全配置并投入生产后。 |
| *enableActivityUI* | 启用可显示下载和同步等活动的进度。 在完全配置并投入生产后，启用以进行故障排除并禁用。 |
| *enableNativeVideo* | 启用时为视频播放使用本机硬件加速（仅限Android）。 |

### 示例JSON策略 {#example-json}

```java
{
  "server": "https://author-screensdemo.adobecqms.net",
"device": "",
"user": "",
"password": "",
"resolution": "auto",
"rebootSchedule": "at 4:00 am",
"maxNumberOfLogFilesToKeep": 10,
"logLevel": 3,
"enableAdminUI": true,
"enableOSD": true,
"enableActivityUI": false,
"enableNativeVideo": false,
"enableAutoScreenshot": false,
"cloudMode": false,
"cloudUrl": "https://screens.adobeioruntime.net",
"cloudToken": "",
"enableDeveloperMode": true
}
```

>[!NOTE]
>所有Android设备都具有 *sdcard* 文件夹，无论实际是 *sdcard* 是否插入。 此文件在部署时将与Downloads文件夹处于同一级别。 一些MDM如Samsung Knox可能会引用此词 *sdcard* 文件夹位置 *内部存储*.

## 使用企业移动性管理批量预配Android Player {#bulk-provisioning}

批量部署Android播放器时，手动向AEM注册每个播放器会变得繁琐起来。 强烈建议使用EMM（企业移动性管理）解决方案（如VMWare Airwatch、MobileIron或Samsung Knox）来远程配置和管理您的部署。 AEM Screens Android播放器支持行业标准EMM AppConfig以允许远程配置。

## 命名Android Player {#name-android}

您可以为Android播放器分配一个用户友好的设备名称，从而将分配的设备名称发送到Adobe Experience Manager (AEM)。 此功能不仅允许您为Android播放器命名，还允许您轻松分配适当的内容。

>[!NOTE]
>您只能在注册之前选择播放器名称。 注册播放器后，无法再更改播放器名称。

请按照以下步骤在Android Player中配置名称：

1. 导航到 **设置** > **关于设备**
1. 编辑设备名称并将其设置为命名您的Android播放器

### 使用企业移动性管理实施Android Player批量预配 {#implementation}

执行以下步骤可在Android Player中进行批量配置：

1. 确保Android设备支持Google Play服务。
1. 使用您喜爱的可支持AppConfig的EMM解决方案注册Android播放器设备。
1. 登录EMM控制台并从Google Play中提取AEM Screens Player应用程序。
1. 选择托管配置或相关选项。
1. 您现在应该会看到可配置的播放器选项列表，例如服务器和批量注册代码。
1. 配置这些参数，保存策略并将其部署到设备。

   >[!NOTE]
   >设备应接收应用程序以及配置，并使用选定的配置指向正确的AEM服务器。 如果您选择配置批量注册代码并将其与AEM中配置的代码相同，则播放器应该能够自动注册自身。 如果您已配置默认显示，则它还可以下载并显示某些默认内容（稍后可以根据您的方便进行更改）。

此外，您还应就AppConfig支持与您的EMM供应商进行核实。 最受欢迎的内容，例如 [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)， [Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)， [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)， [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)， [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) 和 [Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) 其中也支持此行业标准。

### 使用Screens遥控器 {#using-remote-control}

AEM Screens提供远程控制功能。 可在此处详细了解此功能： [屏幕遥控器](implementing-remote-control.md)
