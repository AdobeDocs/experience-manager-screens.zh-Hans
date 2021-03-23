---
title: 实施Windows 10 Player
seo-title: 实施Windows 10 Player
description: 可查看本页以了解有关配置AEM Screens Windows 10播放器的信息。
seo-description: 可查看本页以了解有关配置AEM Screens Windows 10播放器的信息。
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: 管理屏幕，Windows Player
role: 管理员
level: 中间
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 1%

---


# 实施Windows 10 Player {#implementing-windows-player}

本节介绍如何配置AEM Screens Windows 10播放器。 它提供配置文件的信息以及可用选项，以及用于开发和测试的设置的建议。

## 安装Windows Player {#installing-windows-player}

要实施Windows Player for AEM Screens，请安装Windows Player for AEM Screens。

访问&#x200B;[**AEM 6.5 Player下载**](https://download.macromedia.com/screens/)页面。

>[!NOTE]
>Windows播放器中没有窗口模式。 始终为全屏模式。

### 设置AEM Screens 6.5.5 Service Pack {#fp-environment-setup}的环境

>[!NOTE]
>如果您使用的是AEM Screens 6.5.5 Service Pack，则必须为Windows播放器设置环境。

将登录令牌Cookie的&#x200B;**SameSite属性从** Lax **设置为** Adobe Experience Manager Web控制台的&#x200B;**None**
在所有AEM作者和发布实例上配置**。**

应遵循以下步骤：

1. 导航到&#x200B;**Adobe Experience Manager Web控制台
使用`http://localhost:4502/system/console/configMgr`的配置**。

1. 搜索&#x200B;*AdobeGranite令牌身份验证处理程序*。

1. 将登录令牌Cookie的&#x200B;**SameSite属性从** Lax **设置为** None **。**
   ![图像](/help/user-guide/assets/granite-updates.png)

1. 单击&#x200B;**保存**。

### Ad-Hoc方法{#ad-hoc-method}

Ad-Hoc方法允许您安装最新的Windows播放器(*.exe*)。 请访问&#x200B;[**AEM 6.5 Player下载**](https://download.macromedia.com/screens/)页面。

下载应用程序后，请按照播放器上的步骤完成临时安装：

1. 长按左上角以打开管理面板。
1. 从左侧操作菜单导航到&#x200B;**Configuration**，然后输入要连接到的AEM实例的位置（地址）并单击&#x200B;**Save**。
1. 从左侧操作菜单导航到&#x200B;**设备** **注册**&#x200B;链接，以检查设备注册过程的状态。

>[!NOTE]
>
>如果&#x200B;**State**&#x200B;为&#x200B;**REGISTERED**，您会注意到将填充&#x200B;**Device id**&#x200B;字段。
>
>如果&#x200B;**State**&#x200B;为&#x200B;**UNREGISTERED**，则可以使用&#x200B;**Token**&#x200B;注册设备。

## 更改Windows Installer {#changing-default-options}中的默认选项

可查看本节以了解如何更改Windows安装程序中的默认选项以及可用自定义项的列表。

## 使用CLI(PowerShell){#install-powershell}进行安装

1. 为Screens播放器创建自定义位置&#x200B;**专用**，例如：
   `C:\Users\User\screens-player`)
1. 安装
   `aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\screens-player`
1. 打开
   `Start-Process C:\Users\User\screens-player\AEMScreensPlayer.exe`

**示例**

```shell
C:\Users\User\Downloads> mkdir screens-player

C:\Users\User\Downloads> .\aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\Downloads\screens-player

C:\Users\User\Downloads> Start-Process C:\Users\User\Downloads\screens-player\AEMScreensPlayer.exe
```

## Windows Player {#bulk-registration}的批量注册

实施windows播放器时，您无需手动配置每个播放器。 相反，您可以在配置JSON文件经过测试并准备好进行部署后更新它。

配置将确保所有播放器ping配置文件中提供的同一服务器。 您仍必须手动注册每个播放器。

请按照以下步骤配置Windows 10播放器：

1. 安装Windows Player。
1. 在&#x200B;***%appdata%\com.adobe.aem.screens.player\config.json***&#x200B;下查找配置文件。
1. 使用以下信息更新配置JSON，然后将同一文件夹复制到播放器所在的所有系统。

### 策略属性{#policy-attributes}

下表汇总了包含示例策略JSON的策略属性以供参考：

| **策略名称** | **用途** |
|---|---|
| 服务器 | 指向Adobe Experience Manager(AEM)服务器的URL。 |
| 分辨率 | 设备的分辨率。 |
| rebootSchedule | 重新启动播放器的计划。 |
| enableAdminUI | 启用管理员UI以在站点上配置设备。 在完全配置后在生产中设置为false。 |
| enableOSD | 启用渠道切换器UI，让用户在设备上切换渠道。 在完全配置后，在生产中考虑将其设置为false。 |
| enableActivityUI | 启用以显示下载和同步等活动的进度。 在完全配置并投入生产后启用故障排除和禁用。 |

#### 策略JSON文件{#example-policy-json-file}示例

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

## 启用Kiosk模式{#enabling-kiosk-mode}

当您部署Windows播放器时，启用Kiosk模式以使其他应用程序或任务栏不显示在Windows桌面上很重要。

>[!CAUTION]
>
>Adobe建议使用设备管理解决方案来启用Kiosk for Windows。 如果您没有设备管理解决方案来启用Kiosk模式，请按照以下步骤操作。 此方法使用Windows 10企业版和教育版中提供的Shell Launcher功能。 Microsoft推荐的任何非UWP应用程序的其他方法也可用于启用Kiosk，特别是在其他版本的Windows上。

请按照以下步骤启用Kiosk模式：

>[!NOTE]
>
>在执行以下步骤之前，请确保使用Windows 10企业版或教育版。

1. 启用Shell启动器。

   有关详细信息，请参阅Microsoft Windows支持的&#x200B;**[Shell Launcher](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)**&#x200B;页中的“配置Shell Launcher ***”部分。***

1. 创建一个非管理用户（如果您还没有）用于Kiosk。 此用户可以是本地用户或域用户。
1. 从[AEM Screens Player下载](https://download.macromedia.com/screens/)页面为该Kiosk用户安装windows播放器。
1. 有关详细信息，请参阅[使用Shell Launcher创建Windows 10 kiosk](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher)以修改PowerShell脚本。

   修改PowerShell脚本，将用户名替换为您创建的用户名。 确保应用程序可执行文件的路径正确。 这会将自定义shell设置为kiosk用户的windows播放器应用程序，并将其他用户的默认设置设置为explorer.exe。

1. 以管理员身份运行PowerShell脚本。
1. 重新启动并登录，因为Kiosk用户和播放器应用程序应立即开始。

### 疑难解答 {#troubleshooting}

如果您以Kiosk用户身份登录时出现黑屏，则表示您可能错误地指定了Windows播放器可执行文件的路径。 以管理员身份登录，验证并重新运行脚本。

Windows播放器的默认安装路径为：

***C:\Users\&amp;lt；您的用户>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

链接中的示例脚本将启用和禁用自定义外壳程序。 因此，您可能需要将脚本拆分为两个，并启用/禁用以下适用行：

>[!NOTE]
>
>在某些窗口环境中，PowerShell脚本可能受策略（尤其是未签名脚本）限制。 要运行脚本，您可能需要临时禁用并重新启用此限制以运行脚本。 打开PowerShell窗口并使用这些命令。
>
>*set-executionpolicy instrected* - to timperally remove restrictions
>
>*set-executionpolicy restricted*  — 在运行脚本后重新启用限制

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

