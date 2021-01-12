---
title: 实施Android Player
seo-title: Android Player的实现
description: 可查看本页以了解Android Watchdog的实施，该解决方案用于从崩溃中恢复播放器。
seo-description: 可查看本页以了解Android Watchdog的实施，该解决方案用于从崩溃中恢复播放器。
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
translation-type: tm+mt
source-git-commit: 2b72d9a83735beb327f519a66e8b3c0e8bf04409
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 1%

---


# 实施Android Player {#implementing-android-player}

本节介绍如何配置Android播放器。 它提供配置文件的信息以及可用的选项，并建议使用哪些设置进行开发和测试。

此外，**Watchdog**&#x200B;是从崩溃中恢复播放器的解决方案。 应用程序需要向监视服务注册自己，然后定期向其处于活动状态的服务发送消息。 如果监视服务在规定时间内未收到保持活动消息，则服务将尝试重新启动设备以进行干净恢复（如果它具有足够的权限）或重新启动应用程序。

## 安装Android Player {#installing-android-player}

要为AEM Screens实施Android Player，请为AEM Screens安装Android Player。

访问&#x200B;[**AEM 6.5播放器下载**](https://download.macromedia.com/screens/)页面。

### 为AEM Screens6.5.5 Service Pack设置环境{#fp-environment-setup}

>[!NOTE]
>如果您使用的是AEM Screens6.5.5 Service Pack，则必须为Android播放器设置环境。

在所有AEM作者和发布实例上，将登录令牌cookies **Lax**&#x200B;的&#x200B;**SameSite属性设置为**&#x200B;从&#x200B;**Adobe Experience ManagerWeb控制台配置**&#x200B;的&lt;a4/>None **。**

应遵循以下步骤：

1. 使用`http://localhost:4502/system/console/configMgr`导航到&#x200B;**Adobe Experience ManagerWeb控制台配置**。

1. 搜索&#x200B;*AdobeGranite令牌身份验证处理程序*。

1. 将登录令牌cookies **Lax**&#x200B;的&#x200B;**SameSite属性设置为**&#x200B;无&#x200B;**。**
   ![图像](/help/user-guide/assets/granite-updates.png)

1. 单击&#x200B;**保存**。


### Ad-Hoc方法{#ad-hoc-method}

使用临时方法，您可以安装最新的Android播放器(*.exe*)。 访问&#x200B;[**AEM 6.5 Player下载**](https://download.macromedia.com/screens/)页面。

下载应用程序后，请按照播放器上的步骤完成临时安装：

1. 长按左上角以打开管理面板。
1. 从左侧操作菜单导航到&#x200B;**配置**，输入要连接到的AEM实例的位置（地址），然后单击&#x200B;**保存**。

1. 从左侧操作菜单导航到&#x200B;**设备** **注册**&#x200B;链接以检查设备注册过程的状态。

>[!NOTE]
>
>如果&#x200B;**State**&#x200B;是&#x200B;**REGISTERED**，您将注意到将填充&#x200B;**Device id**&#x200B;字段。
>
>如果&#x200B;**状态**&#x200B;是&#x200B;**UNREGISTERED**，则可以使用&#x200B;**令牌**&#x200B;注册设备。

## 实施Android监视程序{#implementing-android-watchdog}

由于Android的架构，重新启动设备需要应用程序具有系统权限。 为此，您需要使用制造商的签名密钥对apk进行签名，否则，监视程序将重新启动播放器应用程序，而不会重新启动设备。

### 使用制造商密钥{#signage-of-android-apks-using-manufacturer-keys}的Android窗格的标牌

要访问某些Android的特权API，如&#x200B;*PowerManager*&#x200B;或&#x200B;*HDMIControlServices*，您需要使用制造商的密钥对android apk进行签名。

>[!CAUTION]
>
>先决条件：
>
>在执行以下步骤之前，您应安装android SDK。

按照以下步骤使用制造商的密钥对android apk进行签名：

1. 从Google Play或[AEM Screens播放器下载](https://download.macromedia.com/screens/)页面下载apk
1. 从制造商处获取平台密钥以获得&#x200B;*pk8*&#x200B;和&#x200B;*pem*&#x200B;文件

1. 在android sdk中使用查找~/Library/Android/sdk/build-tools找到apksigner工具-name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. 在android sdk中查找zip对齐工具的路径
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalpid.apk
1. 使用adb安装在设备上安装&#x200B;***aemscreensalpid.apk***

## 了解Android监视程序服务{#android-watchdog-services}

跨Android监视程序服务使用&#x200B;*AlarmManager*&#x200B;作为cordova插件实现。

下图显示了监视服务的实现：

![chlimage_1-31](assets/chlimage_1-31.png)

**1. 初始化**&#x200B;在初始化cordova插件时，将检查权限以查看我们是否具有系统权限，从而检查重新启动权限。 如果满足这两个条件，则会创建挂起的重新启动意图，否则将创建挂起的重新启动意图(基于其启动活动)。

**2.保持活动计时器**&#x200B;保持活动计时器用于每15秒触发一次事件。 在该事件中，您需要取消现有的挂起意图（以重新启动或重新启动应用程序），并在将来相同的60秒内注册新的挂起意图（实质上是延迟重新启动）。

>[!NOTE]
>
>在Android中，*AlarmManager*&#x200B;用于注册&#x200B;*pendingIntents*，即使应用程序崩溃且其警报投放与API 19(Kitkat)不精确，也可以执行该操作。 在计时器的间隔和&#x200B;*AlarmManager的* *pendingIntent的*&#x200B;警报之间保持一定的间距。

**3.应用程序崩溃**&#x200B;如果发生崩溃，AlarmManager注册的“重新引导的挂起意图”不再重置，因此它将执行应用程序的重新启动或重新启动（具体取决于初始化cordova插件时可用的权限）。

## Android Player {#bulk-provision-android-player}的批量配置

批量推出Android播放器时，需要设置播放器以指向AEM实例，并配置其他属性，而无需在管理员UI中手动输入这些属性。

>[!NOTE]
>此功能可从Android播放器42.0.372中获取。

请按照以下步骤在Android播放器中允许批量配置：

1. 创建名为`player-config.default.json`的配置JSON文件。
请参阅[示例JSON策略](#example-json)以及描述各种[策略属性](#policy-attributes)的使用情况的表。

1. 使用MDM、ADB或Android Studio文件资源管理器将此策略JSON文件放到Android设备上的&#x200B;*sdcard*&#x200B;文件夹。

1. 部署文件后，使用MDM安装播放器应用程序。

1. 当播放器应用程序启动时，它将读取此配置文件并指向相应的AEM服务器，在该服务器中可以注册并随后进行控制。

   >[!NOTE]
   >首次启动应用程序时，此文件为&#x200B;*只读*，不能用于后续配置。 如果在删除配置文件之前启动播放器，只需卸载应用程序并在设备上重新安装。

### 策略属性{#policy-attributes}

下表总结了具有示例策略JSON的策略属性以供参考：

| **策略名称** | **用途** |
|---|---|
| *服务器* | 指向Adobe Experience Manager服务器的URL。 |
| *分辨率* | 设备的分辨率。 |
| *rebootSchedule* | 要重启的计划适用于所有平台。 |
| *enableAdminUI* | 启用管理员UI以在站点上配置设备。 完全配置并投入生产后，设置为&#x200B;*false*。 |
| *enableOSD* | 启用渠道切换器UI，让用户在设备上切换渠道。 完全配置并投入生产后，请考虑将其设置为&#x200B;*false*。 |
| *enableActivityUI* | 启用以显示下载和同步等活动的进度。 在完全配置并投入生产后启用故障排除和禁用。 |
| *enableNativeVideo* | 启用以对视频回放使用本机硬件加速（仅限Android）。 |

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
>无论是否插入了实际的&#x200B;*sdcard*，所有Android设备都有一个&#x200B;*sdcard*&#x200B;文件夹。 部署时此文件将与“下载”文件夹处于同一级别。 某些MDM（如Samsung Knox）可能将此&#x200B;*sdcard*&#x200B;文件夹位置称为&#x200B;*内部存储*。