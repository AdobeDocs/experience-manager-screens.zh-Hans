---
title: 实施Android播放器
seo-title: Android播放器实施
description: 可查看本页以了解Android Watkdog的实施，该解决方案用于从崩溃中恢复播放器。
seo-description: 可查看本页以了解Android Watkdog的实施，该解决方案用于从崩溃中恢复播放器。
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: 管理屏幕， Android播放器
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1439'
ht-degree: 0%

---


# 实施Android播放器{#implementing-android-player}

本节介绍如何配置Android播放器。 它提供了配置文件、可用选项的信息，以及有关开发和测试中要使用的设置的建议。

此外，**Watchdog**&#x200B;是从崩溃中恢复播放器的解决方案。 应用程序需要在监视服务中注册自己，然后定期向其活动的服务发送消息。 如果监视服务在规定时间内未收到保持活动状态消息，则该服务将尝试重新启动设备以进行干净恢复（如果它具有足够的权限）或重新启动应用程序。

## 安装Android播放器{#installing-android-player}

要实施适用于AEM Screens的Android播放器，请安装适用于AEM Screens的Android播放器。

访问&#x200B;[**AEM 6.5 Player下载**](https://download.macromedia.com/screens/)页面。

### 设置AEM Screens 6.5.5 Service Pack {#fp-environment-setup}的环境

>[!NOTE]
>如果您使用的是AEM Screens 6.5.5 Service Pack，则必须为Android播放器设置环境。

在所有AEM创作和发布实例上，将登录令牌Cookie **的** SameSite属性从&#x200B;**Lax**&#x200B;设置为&#x200B;**从** Adobe Experience Manager Web控制台配置&#x200B;**无**。

应遵循以下步骤：

1. 使用`http://localhost:4502/system/console/configMgr`导航到&#x200B;**Adobe Experience Manager Web控制台配置**。

1. 搜索&#x200B;*AdobeGranite令牌身份验证处理程序*。

1. 将登录令牌Cookie的&#x200B;**SameSite属性从** Lax **设置为** None **。**
   ![图像](/help/user-guide/assets/granite-updates.png)

1. 单击&#x200B;**保存**。


### Ad-Hoc方法{#ad-hoc-method}

Ad-Hoc方法允许您安装最新的Android播放器(*.exe*)。 访问&#x200B;[**AEM 6.5播放器下载**](https://download.macromedia.com/screens/)页面。

下载应用程序后，请按照播放器中的步骤完成临时安装：

1. 长按左上角以打开管理面板。
1. 从左侧操作菜单导航到&#x200B;**Configuration** ，输入要连接的AEM实例的位置（地址），然后单击&#x200B;**Save**。

1. 从左侧操作菜单中导航到&#x200B;**Device** **Registration**&#x200B;链接，以检查设备注册过程的状态。

>[!NOTE]
>
>如果&#x200B;**State**&#x200B;为&#x200B;**REGISTERED**，则会注意到将填充&#x200B;**Device id**&#x200B;字段。
>
>如果&#x200B;**State**&#x200B;为&#x200B;**UNRECISTED**，则可以使用&#x200B;**Token**&#x200B;注册设备。

## 实施Android监视程序{#implementing-android-watchdog}

由于Android的架构，重新启动设备需要应用程序具有系统权限。 为此，您需要使用制造商的签名密钥对apk进行签名，否则，监视程序将重新启动播放器应用程序，而不会重新启动设备。

### 使用制造商键{#signage-of-android-apks-using-manufacturer-keys}的Android Apk标牌

要访问Android的某些特权API，如&#x200B;*PowerManager*&#x200B;或&#x200B;*HDMIControlServices*，您需要使用制造商的密钥对android apk进行签名。

>[!CAUTION]
>
>先决条件：
>
>在执行以下步骤之前，您应该已安装Android SDK。

请按照以下步骤使用制造商的密钥对android应用程序进行签名：

1. 从Google Play或[AEM Screens Player下载](https://download.macromedia.com/screens/)页面下载apk
1. 从制造商获取平台密钥，以获取&#x200B;*pk8*&#x200B;和&#x200B;*pem*&#x200B;文件

1. 在android sdk中使用查找~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;找到apksigner工具
1. &lt;pathto> /apksigner符号 — key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. 在android sdk中查找zip对齐工具的路径
1. &lt;pathto> /zipalign -fv 4 aemscreenplayer.apk aemscreensalsid.apk
1. 使用adb安装到设备，安装&#x200B;***aemscreensalpid.apk***

## 了解Android监视程序服务{#android-watchdog-services}

跨Android监视程序服务使用&#x200B;*AlarmManager*&#x200B;作为cordova插件实施。

下图显示了监视程序服务的实现：

![chlimage_1-31](assets/chlimage_1-31.png)

**1. 初始化**&#x200B;在初始化cordova插件时，将检查权限以查看我们是否具有系统权限，进而检查重新启动权限。 如果满足这两个条件，则会创建挂起的重新启动意图，否则会创建挂起的重新启动应用程序意图（基于应用程序的启动活动）。

**2.保持活动计时器**&#x200B;保持活动计时器用于每15秒触发一次事件。 在该事件中，您需要取消现有的挂起意图（重新启动或重新启动应用程序），并在将来的相同60秒内注册新的挂起意图（实质上是延迟重新启动）。

>[!NOTE]
>
>在Android中，使用&#x200B;*AlarmManager*&#x200B;来注册&#x200B;*pendingIntents*，即使应用程序崩溃且其警报传送不准确来自API 19(Kitkat)，也可以执行该pendingIntents。 在计时器的间隔和&#x200B;*AlarmManager的* *pendingIntent的*&#x200B;警报之间保留一些间隔。

**3.应用程序崩溃**&#x200B;在发生崩溃时，AlarmManager中注册的“重新引导的pendingIntent”不再重置，因此它会执行应用程序的重新引导或重新启动（具体取决于cordova插件初始化时可用的权限）。

## 批量配置Android播放器{#bulk-provision-android-player}

批量推出Android播放器时，需要配置播放器以指向AEM实例，并配置其他属性，而无需在管理员UI中手动输入这些属性。

>[!NOTE]
>Android播放器42.0.372中提供了此功能。

请按照以下步骤在Android播放器中允许批量配置：

1. 创建名为`player-config.default.json`的配置JSON文件。
请参阅[示例JSON策略](#example-json)以及描述各种[策略属性](#policy-attributes)的用法的表。

1. 使用MDM、ADB或Android Studio文件资源管理器将此策略JSON文件拖放到Android设备上的&#x200B;*sdcard*&#x200B;文件夹中。

1. 部署文件后，使用MDM安装播放器应用程序。

1. 当播放器应用程序启动时，它将读取此配置文件，并指向适用的AEM服务器，可在该服务器中注册并随后进行控制。

   >[!NOTE]
   >此文件在首次启动应用程序时为&#x200B;*只读*，不能用于后续配置。 如果在删除配置文件之前启动了播放器，则只需在设备上卸载并重新安装应用程序即可。

### 策略属性{#policy-attributes}

下表汇总了具有示例策略JSON的策略属性以供参考：

| **策略名称** | **用途** |
|---|---|
| *服务器* | 指向Adobe Experience Manager服务器的URL。 |
| *分辨率* | 设备的分辨率。 |
| *rebootSchedule* | 重新启动的计划适用于所有平台。 |
| *enableAdminUI* | 启用管理员UI以在站点上配置设备。 在生产环境中完全配置后，将其设置为&#x200B;*false*。 |
| *enableOSD* | 启用渠道切换器UI，以便用户在设备上切换渠道。 在完全配置并投入生产后，请考虑将设置为&#x200B;*false*。 |
| *enableActivityUI* | 启用以显示下载和同步等活动的进度。 在完全配置并投入生产后，启用以进行故障排除并禁用。 |
| *enableNativeVideo* | 启用以对视频播放使用本机硬件加速（仅限Android）。 |

### JSON策略示例{#example-json}

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
>无论是否插入实际的&#x200B;*sdcard*，所有Android设备都具有&#x200B;*sdcard*&#x200B;文件夹。 此文件在部署后将与Downloads文件夹处于同一级别。 某些MDM（如Samsung Knox）可能将此&#x200B;*sdcard*&#x200B;文件夹位置称为&#x200B;*内部存储*。

## 使用企业移动管理{#bulk-provisioning}批量配置Android播放器

批量部署Android播放器时，使用AEM手动注册每个播放器会很繁琐。 强烈建议使用EMM（企业移动性管理）解决方案（如VMWare Airwatch、MobileIron或Samsung Knox）来远程配置和管理您的部署。 AEM Screens Android播放器支持行业标准EMM AppConfig，以允许进行远程配置。

### 使用企业移动管理实施Android播放器的批量配置 {#implementation}

请按照以下步骤在Android播放器中允许批量配置：

1. 确保您的Android设备支持Google Play服务。
1. 使用您最喜爱的支持AppConfig的EMM解决方案注册Android播放器设备。
1. 登录EMM控制台，并从Google Play中提取AEM Screens Player应用程序。
1. 选择托管配置或相关选项。
1. 此时您应会看到可配置的播放器选项列表，例如服务器和批量注册代码。
1. 配置这些参数，保存策略并将其部署到设备。

   >[!NOTE]
   >设备应会接收应用程序以及配置，并指向正确的AEM服务器（具有选定的配置）。 如果您选择配置批量注册代码并将其保留为与在AEM中配置的代码相同，则播放器应该能够自动注册自己。 如果您配置了默认显示屏，则还可以下载和显示一些默认内容（稍后可根据您的方便情况更改这些内容）。

此外，您还应与EMM供应商确认AppConfig支持。 最受欢迎的产品，如[VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、[Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)、[SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)、[Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)、[IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)和[Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)等，均支持此行业标准。
