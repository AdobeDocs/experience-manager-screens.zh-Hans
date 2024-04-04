---
title: 实施Windows 10 Player
seo-title: Implementing Windows 10 Player
description: 按照本页了解如何配置AEM Screens Windows 10 Player。
seo-description: Follow this page to learn about configuring AEM Screens Windows 10 player.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 1%

---

# 实施Windows 10 Player {#implementing-windows-player}

本节介绍如何配置AEM Screens Windows 10 Player。 它提供了有关配置文件和可用选项的信息，以及开发和测试时要使用的设置的建议。

## 安装Windows Player {#installing-windows-player}

要实施适用于AEM Screens的Windows Player，请安装适用于AEM Screens的Windows Player。

访问 [**AEM 6.5播放器下载**](https://download.macromedia.com/screens/) 页面。

>[!NOTE]
>Windows Player中没有窗口模式。 它始终为全屏模式。

### 为AEM Screens 6.5.5 Service Pack设置环境 {#fp-environment-setup}

>[!NOTE]
>如果您使用AEM Screens 6.5.5 Service Pack，则必须为Windows Player设置环境。

设置 **登录令牌Cookie的SameSite属性** 从 **Lax** 到 **无** 从 **Adobe Experience Manager Web控制台配置** 在所有AEM创作和发布实例上。

应遵循以下步骤：

1. 导航到 **Adobe Experience Manager Web控制台配置** 使用 `http://localhost:4502/system/console/configMgr`.

1. 搜索 *Granite令牌身份验证处理程序Adobe*.

1. 设置 **登录令牌Cookie的SameSite属性** 从 **Lax** 到 **无**.
   ![图像](/help/user-guide/assets/granite-updates.png)

1. 单击&#x200B;**保存**。

### Ad Hoc方法 {#ad-hoc-method}

Ad-Hoc方法允许您安装最新的Windows Player (*.exe*)。 访问 [**AEM 6.5播放器下载**](https://download.macromedia.com/screens/) 页面。

下载应用程序后，请按照播放器上的步骤完成临时安装：

1. 长按左上角以打开管理面板。
1. 导航到 **配置** 从左侧操作菜单中，输入要连接的AEM实例的位置（地址），然后单击 **保存**.
1. 导航至 **设备** **注册** 左侧操作菜单中的链接，用于检查设备注册过程的状态。

>[!NOTE]
>
>如果 **状态** 是 **已注册**，您会注意到 **设备ID** 字段将被填充。
>
>如果 **状态** 是 **未注册**，您可以使用 **令牌** 注册设备。

## 命名Windows Player {#name-windows}

您可以为Windows播放器分配一个用户友好的设备名称，从而将分配的设备名称发送到Adobe Experience Manager (AEM)。 此功能不仅允许您为Windows播放器命名，还允许您轻松分配适当的内容。

>[!NOTE]
>您只能在注册之前选择播放器名称。 注册播放器后，无法再更改播放器名称。

按照以下步骤在Windows Player中配置该名称：

1. 单击 **开始** > **运行**
1. 输入 `system.cpl`
1. 使用计算机名称选项卡设置计算机的主机名

## 更改Windows Installer中的默认选项 {#changing-default-options}

请参阅本节以了解如何更改Windows Installer中的默认选项和可用自定义项的列表。

## 使用CLI进行安装(PowerShell) {#install-powershell}

1. 创建自定义位置 **专用** 例如，对于Screens播放器：
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

## 批量注册Windows Player {#bulk-registration}

实施Windows Player时，您无需手动配置每个播放器。 您可以在配置JSON文件经过测试并准备好部署后进行更新。

该配置将确保所有播放器ping配置文件中提供的同一服务器。 您仍然必须手动注册每个播放器。

按照以下步骤配置Windows 10 Player：

1. 安装Windows Player。
1. 在下找到配置文件 ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. 使用以下信息更新配置JSON，然后将同一文件夹复制到播放器所在的所有系统。

### 策略属性 {#policy-attributes}

下表汇总了策略属性并提供了示例策略JSON以供参考：


| **策略名称** | **用途** |
|---|---|
| 服务器 | Adobe Experience Manager (AEM)服务器的URL。 |
| 注册密钥 | 用于使用预共享密钥批量注册设备。 |
| 分辨率 | 设备的分辨率。 |
| rebootSchedule | 重新启动播放器的计划。 |
| enableAdminUI | 启用管理UI以在站点上配置设备。 在完全配置并投入生产后，设置为false。 |
| enableOSD | 为用户启用通道切换器UI以在设备上切换通道。 完全配置并投入生产后，请考虑将设置为false 。 |
| enableActivityUI | 启用可显示下载和同步等活动的进度。 在完全配置并投入生产后，启用以进行故障排除并禁用。 |
| 云模式 | 如果希望Windows Playeras a Cloud Service连接到Screens，则设置为true。 将设置为false以连接到AMS或本地AEM。 |
| cloudToken | 注册令牌，以针对Screensas a Cloud Service进行注册。 |

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

## 启用Kiosk模式 {#enabling-kiosk-mode}

在部署Windows Player时，启用Kiosk模式非常重要，这样其他应用程序或任务栏就不会出现在Windows桌面上。

>[!CAUTION]
>
>Adobe建议使用设备管理解决方案来为Windows启用Kiosk。 如果您没有设备管理解决方案来启用Kiosk模式，请按照以下步骤操作。 此方法使用Windows 10企业版和Edu中提供的Shell启动器功能。 对于非UWP应用程序，Microsoft推荐的任何其他方法也可以应用于启用Kiosk，尤其是在Windows的其他版本上。

请按照以下步骤启用Kiosk模式：

>[!NOTE]
>
>在执行以下步骤之前，请确保您使用的是Windows 10企业版或教育版。

1. 启用Shell启动器。

   请参阅部分 ***配置Shell启动器*** 在 **[Shell启动器](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** 按Microsoft Windows支持页面查看其他信息。

1. 创建一个非管理用户（如果您还没有该用户）以用于自助订餐亭。 这可以是本地或域用户。
1. 从为该Kiosk用户安装Windows Player [AEM Screens播放器下载](https://download.macromedia.com/screens/) 页面。
1. 请参阅 [使用Shell启动器创建Windows 10网亭](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) 修改PowerShell脚本以获取更多信息。

   修改PowerShell脚本，将用户名替换为您创建的用户名。 确保应用程序可执行文件的路径正确。 这会将自定义shell设置为kiosk用户的Windows Player应用程序，并将其他用户的默认值设置为explorer.exe。

1. 以管理员身份运行PowerShell脚本。
1. 重新启动并以Kiosk用户身份登录，播放器应用程序应立即启动。

### 疑难解答 {#troubleshooting}

如果您在以Kiosk用户身份登录时看到黑屏，则表示您可能未正确指定Windows Player可执行文件的路径。 以管理员身份重新登录，验证并重新运行脚本。

Windows Player的默认安装路径为：

***C:\Users\&amp;lt；您的用户>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

链接中的示例脚本将启用和禁用自定义shell。 因此，您可能需要将脚本拆分为两行，然后启用/禁用以下适用的行：

>[!NOTE]
>
>在某些Windows环境中，PowerShell脚本可能受策略限制（特别是未签名的脚本）。 要运行脚本，您可能需要暂时禁用并重新启用此限制以运行脚本。 打开PowerShell窗口并使用这些命令。
>
>*set-executionpolicy unrestricted*  — 临时删除限制
>
>*set-executionpolicy受限制*  — 在运行脚本后重新启用限制

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### 使用Screens遥控器 {#using-remote-control}

AEM Screens提供远程控制功能。 可在此处详细了解此功能： [屏幕遥控器](implementing-remote-control.md)