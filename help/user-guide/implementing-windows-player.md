---
title: 实施Windows 10 Player
seo-title: 实施Windows 10 Player
description: 可查看本页以了解有关配置AEM ScreensWindows 10播放器的信息。
seo-description: 可查看本页以了解有关配置AEM ScreensWindows 10播放器的信息。
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
translation-type: tm+mt
source-git-commit: 24157fdc507beaacd46f3d42e8a0a975c729df38
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---


# 实施Windows 10 Player {#implementing-windows-player}

本节介绍如何配置AEM ScreensWindows 10播放器。 它提供配置文件的信息以及可用的选项，并建议使用哪些设置进行开发和测试。

## 安装Windows Player {#installing-windows-player}

要实施适用于AEM Screens的Windows播放器，请安装适用于AEM Screens的Windows播放器。

访问AEM [**6.5播放器下载页**](https://download.macromedia.com/screens/) 。

### 为AEM Screens6.5.5功能包及更高版本设置环境 {#fp-environment-setup}

如果您使用的是AEM Screens6.5.5功能包，则必须设置Windows播放器环境。

应遵循以下步骤：

1. 使用导航 **到Adobe Experience ManagerWeb控制台** Configuration `http://localhost:4502/system/console/configMgr`。

1. 搜索 *AdobeGranite令牌身份验证处理程序*。

1. 将登录 **令牌Cookie的SameSite属性从Lax****设置为** None **（无）**。
   ![图像](/help/user-guide/assets/granite-updates.png)

1. 单击&#x200B;**保存**。

### Ad-Hoc方法 {#ad-hoc-method}

通过临时方法，您可以安装最新的Windows Player(*.exe*)。 访 [**问AEM 6.5播放器下载页**](https://download.macromedia.com/screens/) 。

下载应用程序后，请按照播放器上的步骤完成临时安装：

1. 长按左上角以打开管理面板。
1. 从左 **侧** 操作菜单导航到配置，输入要连接的AEM实例的位置（地址），然后单击保 **存**。
1. 从左侧操 **作菜** 单导 **航到** “设备注册”链接，检查设备注册过程的状态。

>[!NOTE]
>
>如果状 **态为****REGISTERED**，您将注意 **到设备id** 字段将被填充。
>
>如果状 **态为****UNREGISTERD**，则可以使用 **令牌** 来注册设备。

### 批量服务器配置：使用一个配置注册多个Windows 10播放器 {#bulk-server-configuration-registering-multiple-windows-players-with-one-configuration}

安装Windows播放器后，可以使用一个配置注册多个播放器。

>[!NOTE]
>
>**Windows Player批量注册**
>
>实施Windows播放器时，您无需手动配置每个播放器。 相反，您可以在配置JSON文件经过测试并准备好进行部署后更新它。
>
>配置将确保所有播放器ping配置文件中提供的同一服务器。 您仍必须手动注册每个播放器。

请按照以下步骤配置Windows 10播放器：

1. 安装Windows Player。
1. 在%appdata%\com. ***adobe.aem.screens.player\config.json下查找配置文件***。
1. 使用以下信息更新配置JSON，然后将同一文件夹复制到播放器所在的所有系统。

### 策略属性 {#policy-attributes}

下表总结了具有示例策略JSON的策略属性以供参考：

| **策略名称** | **用途** |
|---|---|
| 服务器 | Adobe Experience Manager(AEM)服务器的URL。 |
| 分辨率 | 设备的分辨率。 |
| rebootSchedule | 重新启动播放器的计划。 |
| enableAdminUI | 启用管理员UI以在站点上配置设备。 在完全配置并投入生产后，将其设置为false。 |
| enableOSD | 启用渠道切换器UI，让用户在设备上切换渠道。 在完全配置并投入生产时，请考虑将其设置为false。 |
| enableActivityUI | 启用以显示下载和同步等活动的进度。 在完全配置并投入生产后启用故障排除和禁用。 |

#### 示例策略JSON文件 {#example-policy-json-file}

```
{
    "server": "https://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

## 启用自助终端模式 {#enabling-kiosk-mode}

当您部署Windows播放器时，启用Kiosk模式以使其他应用程序或任务栏不出现在Windows桌面上很重要。

>[!CAUTION]
>
>Adobe建议使用设备管理解决方案来启用Kiosk for Windows。 如果您没有设备管理解决方案，请按照以下步骤启用Kiosk模式。 此方法使用Windows 10企业版和教育版中提供的Shell Launcher功能。 对于非UWP应用程序，Microsoft推荐的任何其他方法也可以应用，以启用Kiosk，尤其是在其他版本的Windows上。

请按照以下步骤启用自助终端模式：

>[!NOTE]
>
>在执行以下步骤之前，请确保使用Windows 10 Enterprise或Education。

1. 启用Shell启动器。

   有关其他信 ***息，请参阅*** Microsoft Windows支 **[持在Shell Launcher页](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** 中配置Shell Launcher一节。

1. 创建一个非管理用户（如果您还没有）用于Kiosk。 此用户可以是本地用户或域用户。
1. 从AEM Screens播放器下载页面为该Kiosk用户 [安装windows播放](https://download.macromedia.com/screens/) 器。
1. 有关详 [细信息，请参阅使用Shell Launcher创建Windows 10自动终端](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) ，以修改PowerShell脚本。

   修改PowerShell脚本，将用户名替换为您创建的用户名。 确保应用程序可执行文件的路径正确。 这会将自定义外壳程序设置为kiosk用户的windows播放器应用程序，并将其他用户的默认设置为explorer.exe。

1. 以管理员身份运行PowerShell脚本。
1. 重新启动并登录Kiosk用户，播放器应用程序应立即开始。

### 疑难解答 {#troubleshooting}

如果您以Kiosk用户身份登录时出现黑屏，则意味着您可能错误地指定了Windows播放器可执行文件的路径。 以管理员身份登录，验证并重新运行脚本。

Windows播放器的默认安装路径为：

***C:\Users\&amp;lt；您的用户>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM ScreensPlayer.exe***

链接中的示例脚本将启用和禁用自定义外壳程序。 因此，您可能需要将脚本拆分为两个，并启用／禁用以下适用行：

>[!NOTE]
>
>在某些窗口环境下，PowerShell脚本可能受策略（尤其是未签名脚本）限制。 要运行脚本，您可能需要临时禁用并重新启用此限制才能运行脚本。 打开PowerShell窗口并使用这些命令。
>
>*set-execution* -policy unresticed - to timperially remove restrictions
>
>*set-executionpolicy restricted* —— 在运行脚本后重新启用限制

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

