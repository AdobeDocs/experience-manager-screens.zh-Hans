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
source-git-commit: 24157fdc507beaacd46f3d42e8a0a975c729df38
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 1%

---


# 实施Android Player {#implementing-android-player}

本节介绍如何配置Android播放器。 它提供配置文件的信息以及可用的选项，并建议使用哪些设置进行开发和测试。

此外， **Watchdog** 是一种从崩溃中恢复播放器的解决方案。 应用程序需要向监视服务注册自己，然后定期向其处于活动状态的服务发送消息。 如果监视服务在规定时间内未收到保持活动消息，则服务将尝试重新启动设备以进行干净恢复（如果它具有足够的权限）或重新启动应用程序。

## 安装Android Player {#installing-android-player}

要为AEM Screens实施Android Player，请为AEM Screens安装Android Player。

访问AEM [**6.5播放器下载页**](https://download.macromedia.com/screens/) 。

### 为AEM Screens6.5.5功能包及更高版本设置环境 {#fp-environment-setup}

如果您使用的是AEM Screens6.5.5功能包，则必须为Android播放器设置环境。

应遵循以下步骤：

1. 使用导航 **到Adobe Experience ManagerWeb控制台** Configuration `http://localhost:4502/system/console/configMgr`。

1. 搜索 *AdobeGranite令牌身份验证处理程序*。

1. 将登录 **令牌Cookie的SameSite属性从Lax****设置为** None **（无）**。
   ![图像](/help/user-guide/assets/granite-updates.png)

1. 单击&#x200B;**保存**。


### Ad-Hoc方法 {#ad-hoc-method}

通过临时方法，您可以安装最新的Android Player(*.exe*)。 访 [**问AEM 6.5播放器下载页**](https://download.macromedia.com/screens/) 。

下载应用程序后，请按照播放器上的步骤完成临时安装：

1. 长按左上角以打开管理面板。
1. 从左 **侧** 操作菜单导航到配置，输入要连接的AEM实例的位置（地址），然后单击保 **存**。

1. 从左侧操 **作菜** 单导 **航到** “设备注册”链接，检查设备注册过程的状态。

>[!NOTE]
>
>如果状 **态为****REGISTERED**，您将注意 **到设备id** 字段将被填充。
>
>如果状 **态为****UNREGISTERD**，则可以使用 **令牌** 来注册设备。

## 实施Android监视程序 {#implementing-android-watchdog}

由于Android的架构，重新启动设备需要应用程序具有系统权限。 为此，您需要使用制造商的签名密钥对apk进行签名，否则，监视程序将重新启动播放器应用程序，而不会重新启动设备。

### 使用制造商密钥的Android窗格的标牌 {#signage-of-android-apks-using-manufacturer-keys}

要访问Android的某些特权API( *如PowerManager**或HDMIControlServices*)，您需要使用制造商的密钥签署android apk。

>[!CAUTION]
>
>先决条件：
>
>在执行以下步骤之前，您应安装android SDK。

按照以下步骤使用制造商的密钥对android apk进行签名：

1. 从Google Play或从AEM Screens播放器下载页 [面下载apk](https://download.macromedia.com/screens/)
1. 从制造商处获取平台密钥 *以获取pk* 8和 *pem* 文件

1. 在android sdk中使用查找~/Library/Android/sdk/build-tools找到apksigner工具-name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. 在android sdk中查找zip对齐工具的路径
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalpid.apk
1. 使 ***用adb安装*** ，将aemscreensalpid.apk安装到设备

## Android监视程序实施 {#android-watchdog-implementation}

跨Android监视程序服务使用AlarmManager作为cordova插件 *实现*。

下图显示了监视服务的实现：

![chlimage_1-31](assets/chlimage_1-31.png)

**1. 初始化** 在初始化cordova插件时，会检查权限以查看我们是否具有系统权限，从而检查重新启动权限。 如果满足这两个条件，则会创建挂起的重新启动意图，否则将创建挂起的重新启动意图(基于其启动活动)。

**2. 保持活动计时器** “保持活动”计时器用于每15秒触发一次事件。 在该事件中，您需要取消现有的挂起意图（以重新启动或重新启动应用程序），并在将来相同的60秒内注册新的挂起意图（实质上是延迟重新启动）。

>[!NOTE]
>
>在Android中， *AlarmManager* 用于注册pendingIntents, ** 即使应用程序崩溃，并且其警报投放与API 19(Kitkat)不完全一致，它也可以执行。 在计时器的间隔和AlarmManager的pendingIntent的 *闹铃之间**保持一定的间距* 。

**3. 应用程序崩溃** 在发生崩溃时，AlarmManager注册的“重新引导的pendingIntent”不再重置，因此它执行应用程序的重新引导或重新启动（具体取决于cordova插件初始化时可用的权限）。
