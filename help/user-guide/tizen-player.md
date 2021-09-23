---
title: 蒂森球员
description: 本页介绍Tizen Player的安装和工作。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 0f99b96e90f0aac6bf923343ecefa1708d5cfd17
workflow-type: tm+mt
source-wordcount: '1222'
ht-degree: 1%

---

# 实施Tizen播放器 {#tizen-player}

## 安装Tizen Player {#installing-tizen-player}

请按照以下步骤为AEM Screens实施Tizen Player:

1. 导航到[AEM Screens Player下载](https://download.macromedia.com/screens/)页面以下载Tizen Player。

1. 从本地计算机安装Tizen播放器&#x200B;*(.zip)*&#x200B;文件。

## 设置http服务器 {#setting-local-server}

>[!NOTE]
> 解压缩zip文件，并通过`http server`使Tizen播放器可用。 （`http server`不是本地或Apache服务器所必需的）。

应遵循以下步骤：

1. 将提取的两个文件（如`AEMScreensPlayer.wgt`和`sssp_config.xml`）复制到本地Apache Web服务器的根目录中。

   >[!NOTE]
   >`AEMScreensPlayer.wgt`是实际的Tizen播放器应用程序，`sssp_config.xml`包含有关此映射的信息，可帮助您在Tizen设备上安装该映射。

1. 获取本地HTTP服务器的IP或URL(以及包含步骤2中提取文件的文件夹的路径（如果已提取到子文件夹，而不是根文件夹）

1. Tizen播放器从本地服务器下载安装程序。

### 命名Tizen播放器 {#name-tizen}

您可以为Tizen播放器分配用户友好的设备名称，从而将分配的设备名称发送到Adobe Experience Manager(AEM)。 此功能不仅允许您命名Tizen播放器，还允许您轻松分配相应的内容。

>[!NOTE]
>只有在注册之前，您才可以选择播放器名称。 注册播放器后，无法再更改播放器名称。

请按照以下步骤在Tizen播放器中配置名称：

1. 单击遥控器上的菜单按钮。
1. 导航到&#x200B;**network** —> **设备名称** ，以为播放器分配名称。

### 在Samsung设备上配置更新 {#config-updates}

按照Samsung设备上的以下步骤，在设备上完成AEM Screens播放器的安装：

1. 导航到您的Samsung设备并打开。

1. 单击设备远程中的&#x200B;**MENU**&#x200B;按钮，然后从左侧导航栏向下滚动到&#x200B;**System**。

1. 向下滚动并选择&#x200B;**通过**&#x200B;播放选项，并将其更改为&#x200B;**URL启动器**选项。
   ![图像](/help/user-guide/assets/tizen/rms-2.png)

1. 设置URL启动器后，从远程按&#x200B;**Home**&#x200B;按钮。

1. 导航到&#x200B;**URL启动器设置**，输入本地主机服务器的IP地址，然后单击&#x200B;**完成**。
   >[!NOTE]
   >Tizen播放器应该能够连接到http服务器。

1. 现在，AEM Screens Player应该在您的Samsung设备上自动安装并启动。

   >[!NOTE]
   >Tizen设备和`http`服务器应能够相互连接，即服务器应该可以连接到Tizen播放器。


## 使用SameSite Cookie问题免除用户代理 {#exempting-user-agents}

>[!IMPORTANT]
>**本节适用于Adobe Experience Manager(AEM)6.5.5到AEM 6.5.7**
>某些浏览器引擎与AEM 6.5到AEM 6.7发布的登录令牌中使用的&#x200B;*SameSite=None*&#x200B;属性不兼容。通常，可通过将浏览器升级到最新的可用版本来解决此问题。 在某些情况下，可能无法进行此类升级，例如使用智能显示器、机顶盒或具有嵌入式浏览引擎的其他设备。

使用&#x200B;*SameSite=None*&#x200B;时，请按照以下步骤免除这些不兼容的客户端：

1. 升级到Adobe Experience Manager(AEM)Service Pack 6.5.7。

1. AEM重新启动后，转到`/system/console/configMgr`并搜索&#x200B;**AdobeGranite令牌身份验证处理程序**。 将&#x200B;**SameSite**&#x200B;值的值设置为&#x200B;**None**。

1. 您应会看到新选项&#x200B;*要从samesite属性*&#x200B;中免除用户代理。 使用与&#x200B;*SameSite=None*&#x200B;属性不兼容的用户代理对应的正则表达式填充该变量。
   >[!NOTE]
   >请参阅[SameSite=None:已知不兼容的客户端](https://www.chromium.org/updates/same-site/incompatible-clients)以了解更多详细信息。 对于Tizen播放器，请使用正则表达式：`(.*)Tizen(.*)`。

1. 针对您的AEM 6.5.5及更高版本实例注册Tizen播放器，该播放器应正常注册和显示内容。

## 远程配置Tizen播放器 {#remote-provisioning}

远程配置Tizen Player使您能够无需付出多大努力即可部署成千上万的三星Tizen显示屏。 它避免了使用服务器URL和批量注册代码或其他参数配置每个播放器的繁琐手动操作，在将Screens用作配置云模式和云令牌的Cloud Service时也是如此。

此功能允许您远程配置Tizen播放器，并根据需要集中更新这些配置。 您只需使用`HTTP`服务器来托管Tizen应用程序`(wgt and xml file)`，并使用相应参数来保存`config.json`的文本编辑器即可。

确保已在“Tizen Device”（显示主页按钮 — > URL启动器设置）上配置了URL启动器地址。
在托管Tizen应用程序的`HTTP`服务器上，将文件`config.json`放置到与`wgt`文件相同的位置。 文件名必须为`config.json`。
Tizen播放器将安装，在启动时（以及每次重新引导时）将检查并应用`config.json`文件中的设置。

### JSON策略示例 {#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### 策略属性和用途 {#policy-attributes}

下表概述了策略及其功能。

>[!NOTE]
>策略配置是严格强制执行的，不会在播放器的管理员UI中手动覆盖。 要允许为特定策略进行手动播放器配置，请不要在策略配置中指定策略，例如，如果要允许手动配置重新启动计划，请不要在策略配置中指定键`rebootSchedule`。 每次重新加载播放器时都会读取策略配置。

| **策略名称** | **用途** |
|---|---|
| 服务器 | 指向Adobe Experience Manager(AEM)服务器的URL。 |
| registrationKey | 用于使用预共享密钥批量注册设备。 |
| 分辨率 | 设备的分辨率。 |
| rebootSchedule | 重新引导播放器的计划。 |
| enableAdminUI | 启用管理员UI以在站点上配置设备。 在生产环境中完全配置后，将其设置为false。 |
| enableOSD | 启用渠道切换器UI，以便用户在设备上切换渠道。 在完全配置并投入生产后，请考虑将设置为false。 |
| enableActivityUI | 启用以显示下载和同步等活动的进度。 在完全配置并投入生产后，启用以进行故障排除并禁用。 |
| cloudMode | 如果您希望Tizen播放器作为Cloud Service连接到Screens，则设置为true。 设置为false，以便连接到AMS或内部AEM。 |
| cloudToken | 要在Screens中注册为Cloud Service的注册令牌。 |


## 将Tizen设备注册到Samsung远程管理服务(RMS) {#enroll-tizen-device-rms}

请按照以下步骤将Tizen设备注册到Samsung远程管理服务(RMS)并远程配置URL启动器：

>[!NOTE]
>验证网络设置和监视器。

1. 导航到&#x200B;**Menu** -> **Network** -> **服务器网络设置**&#x200B;并按&#x200B;**Enter**。

1. 导航到服务器地址并键入MagicInfo URL访问，然后按&#x200B;**Done**。

1. 设置TLS（如果需要）。 导航到该端口并从服务器中选择端口号，然后单击&#x200B;**Save**。

1. 导航到&#x200B;**Device**&#x200B;选项卡，并检查您刚刚配置的设备。 找到设备后，单击复选框并选择&#x200B;**批准**。

   >![图像](/help/user-guide/assets/tizen/rms-3.png)

1. 填写所需信息并选择设备组。 单击&#x200B;**OK**&#x200B;以完成批准过程。

   >![图像](/help/user-guide/assets/tizen/rms-7.png)

1. 设备获得批准后，应会显示在设备列表中。 单击位于设备框上的&#x200B;*信息*&#x200B;按钮，即&#x200B;**i**，如下图所示。

   >![图像](/help/user-guide/assets/tizen/rms-6.png)

1. 此时将显示设备信息对话框。 选择&#x200B;**设备信息**&#x200B;选项卡，然后单击&#x200B;**编辑**。

   >![图像](/help/user-guide/assets/tizen/rms-5.png)

1. 编辑设备选项并选择&#x200B;**设置**&#x200B;选项卡。 导航到&#x200B;**URL Launcher**&#x200B;部分，然后输入托管wgt的URL和`SSSP config file`以安装`SSSP`应用程序，如下图所示。

   ![图像](/help/user-guide/assets/tizen/rms-9.png)

1. 单击&#x200B;**Save**，将所做的更改显示在显示屏上。
