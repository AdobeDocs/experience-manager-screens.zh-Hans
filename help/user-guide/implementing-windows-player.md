---
title: 实施Windows 10 Player
seo-title: Implementing Windows 10 Player
description: 请阅读本页以了解有关配置AEM Screens Windows 10播放器的信息。
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
source-git-commit: 97bc64ce3c01ac2de301b17bf9f8610662d45f88
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 1%

---

# 实施Windows 10 Player {#implementing-windows-player}

本节介绍如何配置AEM Screens Windows 10播放器。 它提供了配置文件、可用选项的信息，以及有关开发和测试所使用的设置的建议。

## 安装Windows Player {#installing-windows-player}

要实施适用于AEM Screens的Windows Player，请安装适用于AEM Screens的Windows Player。

访问 [**AEM 6.5播放器下载**](https://download.macromedia.com/screens/) 页面。

>[!NOTE]
>Windows播放器中没有窗口模式。 始终为全屏模式。

### 设置AEM Screens 6.5.5 Service Pack的环境 {#fp-environment-setup}

>[!NOTE]
>如果您使用的是AEM Screens 6.5.5 Service Pack，则必须为Windows Player设置环境。

设置 **登录令牌Cookie的SameSite属性** 从 **Lax** to **无** 从 **Adobe Experience Manager Web控制台配置** 在所有AEM创作和发布实例上。

应遵循以下步骤：

1. 导航到 **Adobe Experience Manager Web控制台配置** 使用 `http://localhost:4502/system/console/configMgr`.

1. 搜索 *AdobeGranite令牌身份验证处理程序*.

1. 设置 **登录令牌Cookie的SameSite属性** 从 **Lax** to **无**.
   ![图像](/help/user-guide/assets/granite-updates.png)

1. 单击&#x200B;**保存**。

### Ad-Hoc方法 {#ad-hoc-method}

Ad-Hoc方法允许您安装最新的Windows播放器(*.exe*)。 访问 [**AEM 6.5播放器下载**](https://download.macromedia.com/screens/) 页面。

下载应用程序后，请按照播放器中的步骤完成临时安装：

1. 长按左上角以打开管理面板。
1. 导航到 **配置** 从左侧操作菜单中，输入要连接到的AEM实例的位置（地址）并单击 **保存**.
1. 导航到 **设备** **注册** 从左侧操作菜单链接以检查设备注册过程的状态。

>[!NOTE]
>
>如果 **州** is **已注册**，您会注意到 **设备ID** 字段。
>
>如果 **州** is **未注册**，则可以使用 **令牌** 来注册设备。

## 命名Windows Player {#name-windows}

您可以为Windows播放器分配用户友好的设备名称，从而将分配的设备名称发送到Adobe Experience Manager(AEM)。 此功能不仅允许您命名Windows播放器，还允许您轻松分配相应的内容。

>[!NOTE]
>只有在注册之前，您才可以选择播放器名称。 注册播放器后，无法再更改播放器名称。

请按照以下步骤在Windows播放器中配置名称：

1. 单击 **开始** —> **运行**
1. 输入 `system.cpl`
1. 使用计算机名称选项卡设置计算机的主机名

## 在Windows Installer中更改默认选项 {#changing-default-options}

请阅读本节内容，了解如何更改Windows Installer中的默认选项和可用自定义列表。

## 使用CLI(PowerShell)进行安装 {#install-powershell}

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

## Windows Player的批量注册 {#bulk-registration}

实施Windows播放器时，您无需手动配置每个播放器。 相反，您可以在配置JSON文件经过测试并准备好进行部署后，更新该文件。

配置将确保所有播放器ping配置文件中提供的同一服务器。 您仍必须手动注册每个播放器。

按照以下步骤配置Windows 10 Player:

1. 安装Windows Player。
1. 在 ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. 使用以下信息更新配置JSON，然后将同一文件夹复制到播放器所在的所有系统。

### 策略属性 {#policy-attributes}

下表汇总了具有示例策略JSON的策略属性以供参考：

| **策略名称** | **用途** |
|---|---|
| 服务器 | 指向Adobe Experience Manager(AEM)服务器的URL。 |
| 分辨率 | 设备的分辨率。 |
| rebootSchedule | 重新引导播放器的计划。 |
| enableAdminUI | 启用管理员UI以在站点上配置设备。 在生产环境中完全配置后，将其设置为false。 |
| enableOSD | 启用渠道切换器UI，以便用户在设备上切换渠道。 在完全配置并投入生产后，请考虑将其设置为false。 |
| enableActivityUI | 启用以显示下载和同步等活动的进度。 在完全配置并投入生产后，启用以进行故障排除并禁用。 |

#### 策略JSON文件示例 {#example-policy-json-file}

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

在部署Windows播放器时，请务必启用Kiosk模式，以便其他应用程序或任务栏不会显示在Windows桌面上。

>[!CAUTION]
>
>Adobe建议使用设备管理解决方案来启用Windows版Kiosk。 如果您没有设备管理解决方案来启用Kiosk模式，请按照以下步骤操作。 此方法使用Windows 10企业版和Edu版中提供的Shell启动器功能。 对于非UWP应用，任何Microsoft推荐的其他方法也可应用于启用Kiosk，尤其是在其他Windows版本上。

按照以下步骤启用Kiosk模式：

>[!NOTE]
>
>在执行以下步骤之前，请确保使用Windows 10企业版或教育版。

1. 启用Shell启动器。

   请参阅一节 ***配置Shell启动器*** in **[壳启动器](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** 页面，以了解其他信息。Microsoft Windows支持。

1. 创建要用于Kiosk的非管理用户（如果您还没有）。 这可以是本地用户或域用户。
1. 从为该Kiosk用户安装Windows播放器 [AEM Screens Player下载](https://download.macromedia.com/screens/) 页面。
1. 请参阅 [使用Shell Launcher创建Windows 10网亭](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) 以修改PowerShell脚本，以了解详细信息。

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
>*set-executionpolicy不受限制*  — 临时删除限制
>
>*set-executionpolicy受限*  — 在运行脚本后重新启用限制

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### 使用Screens远程控制 {#using-remote-control}

AEM Screens提供远程控制功能。 请在此处了解有关此功能的更多信息： [Screens远程控制](implementing-remote-control.md)