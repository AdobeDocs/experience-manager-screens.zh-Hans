---
title: 实施Windows 10 Player
seo-title: 实施Windows 10 Player
description: 请阅读本页以了解有关配置AEM Screens Windows 10播放器的信息。
seo-description: 请阅读本页以了解有关配置AEM Screens Windows 10播放器的信息。
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: 管理屏幕， Windows Player
role: Administrator
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 1%

---

# 实施Windows 10 Player {#implementing-windows-player}

本节介绍如何配置AEM Screens Windows 10播放器。 它提供了配置文件、可用选项的信息，以及有关开发和测试中要使用的设置的建议。

## 安装Windows Player {#installing-windows-player}

要实施适用于AEM Screens的Windows Player，请安装适用于AEM Screens的Windows Player。

访问&#x200B;[**AEM 6.5 Player下载**](https://download.macromedia.com/screens/)页面。

>[!NOTE]
>Windows播放器中没有窗口模式。 始终为全屏模式。

### 设置AEM Screens 6.5.5 Service Pack {#fp-environment-setup}的环境

>[!NOTE]
>如果您使用的是AEM Screens 6.5.5 Service Pack，则必须为Windows Player设置环境。

将登录令牌Cookie的&#x200B;**SameSite属性从** Lax **设置为**&#x200B;从&#x200B;**Adobe Experience Manager Web控制台的None**
在所有AEM创作实例和发布实例上配置**。**

应遵循以下步骤：

1. 导航到&#x200B;**Adobe Experience Manager Web控制台
使用`http://localhost:4502/system/console/configMgr`进行配置**。

1. 搜索&#x200B;*AdobeGranite令牌身份验证处理程序*。

1. 将登录令牌Cookie的&#x200B;**SameSite属性从** Lax **设置为** None **。**
   ![图像](/help/user-guide/assets/granite-updates.png)

1. 单击&#x200B;**保存**。

### Ad-Hoc方法{#ad-hoc-method}

Ad-Hoc方法允许您安装最新的Windows Player(*.exe*)。 访问&#x200B;[**AEM 6.5播放器下载**](https://download.macromedia.com/screens/)页面。

下载应用程序后，请按照播放器中的步骤完成临时安装：

1. 长按左上角以打开管理面板。
1. 从左侧操作菜单导航到&#x200B;**Configuration** ，输入要连接的AEM实例的位置（地址），然后单击&#x200B;**Save**。
1. 从左侧操作菜单中导航到&#x200B;**Device** **Registration**&#x200B;链接，以检查设备注册过程的状态。

>[!NOTE]
>
>如果&#x200B;**State**&#x200B;为&#x200B;**REGISTERED**，则会注意到将填充&#x200B;**Device id**&#x200B;字段。
>
>如果&#x200B;**State**&#x200B;为&#x200B;**UNRECISTED**，则可以使用&#x200B;**Token**&#x200B;注册设备。

## 在Windows Installer {#changing-default-options}中更改默认选项

请阅读本节内容，了解如何更改Windows Installer中的默认选项和可用自定义列表。

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

实施Windows播放器时，您无需手动配置每个播放器。 相反，您可以在配置JSON文件经过测试并准备好进行部署后，更新该文件。

配置将确保所有播放器ping配置文件中提供的同一服务器。 您仍必须手动注册每个播放器。

按照以下步骤配置Windows 10 Player:

1. 安装Windows Player。
1. 在&#x200B;***%appdata%\com.adobe.aem.screens.player\config.json***&#x200B;下找到配置文件。
1. 使用以下信息更新配置JSON，然后将同一文件夹复制到播放器所在的所有系统。

### 策略属性{#policy-attributes}

下表汇总了具有示例策略JSON的策略属性以供参考：

| **策略名称** | **用途** |
|---|---|
| 服务器 | 指向Adobe Experience Manager(AEM)服务器的URL。 |
| 分辨率 | 设备的分辨率。 |
| rebootSchedule | 重新引导播放器的计划。 |
| enableAdminUI | 启用管理员UI以在站点上配置设备。 在生产环境中完全配置后，将其设置为false。 |
| enableOSD | 启用渠道切换器UI，以便用户在设备上切换渠道。 在完全配置并投入生产后，请考虑将设置为false。 |
| enableActivityUI | 启用以显示下载和同步等活动的进度。 在完全配置并投入生产后，启用以进行故障排除并禁用。 |

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

在部署Windows播放器时，请务必启用Kiosk模式，以便其他应用程序或任务栏不会显示在Windows桌面上。

>[!CAUTION]
>
>Adobe建议使用设备管理解决方案来启用Windows版Kiosk。 如果您没有设备管理解决方案来启用Kiosk模式，请按照以下步骤操作。 此方法使用Windows 10企业版和Edu版中提供的Shell启动器功能。 任何其他微软推荐的非UWP应用方式也可应用于启用Kiosk，尤其是在其他Windows版本上。

按照以下步骤启用Kiosk模式：

>[!NOTE]
>
>在执行以下步骤之前，请确保使用Windows 10企业版或教育版。

1. 启用Shell启动器。

   有关其他信息，请参阅Microsoft Windows支持在&#x200B;**[Shell Launcher](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)**&#x200B;页面中配置Shell Launcher ***一节。***

1. 创建要用于Kiosk的非管理用户（如果您还没有）。 这可以是本地用户或域用户。
1. 从[AEM Screens Player下载](https://download.macromedia.com/screens/)页面为该Kiosk用户安装Windows播放器。
1. 有关详细信息，请参阅[使用Shell启动器创建Windows 10 kiosk](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher)以修改PowerShell脚本。

   修改PowerShell脚本，将用户名替换为您创建的用户名。 确保应用程序可执行文件的路径正确。 这会将自定义shell设置为kiosk用户的windows播放器应用程序，并将其他用户的默认设置为explorer.exe。

1. 以管理员身份运行PowerShell脚本。
1. 重新启动并登录，因为Kiosk用户和播放器应用程序应该直接启动。

### 疑难解答 {#troubleshooting}

如果您以Kiosk用户身份登录时看到黑屏，则意味着您可能错误地指定了Windows播放器可执行文件的路径。 以管理员身份登录，验证并重新运行脚本。

Windows播放器的默认安装路径是：

***C:\Users\&amp;lt；您的用户>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

链接中的示例脚本将启用和禁用自定义Shell。 因此，您可能需要将脚本拆分为两个，并启用/禁用以下适用行：

>[!NOTE]
>
>在某些Windows环境中， PowerShell脚本可能受策略（特别是无符号脚本）的限制。 要运行脚本，您可能需要临时禁用并重新启用此限制才能运行脚本。 打开PowerShell窗口并使用这些命令。
>
>*set-executionpolicy不受限制*  — 可暂时删除限制
>
>*set-executionpolicy受限*  — 在运行脚本后重新启用限制

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```
