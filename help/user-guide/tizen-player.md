---
title: 蒂森球员
description: 本页介绍Tizen Player的安装和工作。
feature: 管理屏幕、播放器
role: Administrator
level: Intermediate
source-git-commit: 7fa4207be0d89a6c7d0d9d9a04722cd40d035634
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 1%

---


# 实现Tizen播放器{#tizen-player}

## 安装Tizen Player {#installing-tizen-player}

请按照以下步骤为AEM Screens实施Tizen Player:

1. 导航到[AEM Screens Player下载](https://download.macromedia.com/screens/)页面以下载Tizen Player。

1. 从本地计算机安装Tizen播放器&#x200B;*(.zip)*&#x200B;文件。

## 设置本地服务器并解压Zip文件{#setting-local-server}

>[!NOTE]
> 解压缩zip文件，并通过`http server`使Tizen播放器可用。 （`http server`不是本地或Apache服务器所必需的）。

应遵循以下步骤：

1. 将提取的两个文件（如`AEMScreensPlayer.wgt`和`sssp_config.xml`）复制到本地Apache Web服务器的根目录中。

   >[!NOTE]
   >`AEMScreensPlayer.wgt`是实际的Tizen播放器应用程序，`sssp_config.xml`包含有关此映射的信息，可帮助您在Tizen设备上安装该映射。

1. 获取本地HTTP服务器的IP或URL(以及包含步骤2中提取文件的文件夹的路径（如果已提取到子文件夹，而不是根文件夹）

1. Tizen播放器将从本地服务器下载安装程序。

### 命名Tizen播放器{#name-tizen}

您可以为Tizen播放器分配用户友好的设备名称，从而将分配的设备名称发送到Adobe Experience Manager(AEM)。 此功能不仅允许您命名Tizen播放器，还允许您轻松分配相应的内容。

请按照以下步骤在Tizen播放器中配置名称：

1. 单击遥控器上的菜单按钮。
1. 导航到&#x200B;**network** —> **设备名称** ，以为播放器分配名称。

### 在Samsung设备{#config-updates}上配置更新

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


## 使用SameSite Cookie问题{#exempting-user-agents}免除用户代理

>[!IMPORTANT]
>**本节适用于Adobe Experience Manager(AEM)6.5.5到AEM 6.5.7**
>某些浏览器引擎与AEM 6.5到AEM 6.7发布的登录令牌中使用的&#x200B;*SameSite=None*&#x200B;属性不兼容。在大多数情况下，可通过将浏览器升级到最新的可用版本来解决此问题。 在某些情况下，可能无法进行此类升级，例如使用智能显示器、机顶盒或具有嵌入式浏览引擎的其他设备。

使用&#x200B;*SameSite=None*&#x200B;时，请按照以下步骤免除这些不兼容的客户端：

1. 升级到Adobe Experience Manager(AEM)Service Pack 6.5.7。

1. AEM重新启动后，转到`/system/console/configMgr`并搜索&#x200B;**AdobeGranite令牌身份验证处理程序**。 将&#x200B;**SameSite**&#x200B;值的值设置为&#x200B;**None**。

1. 您应会看到新选项&#x200B;*要从samesite属性*&#x200B;中免除用户代理。 使用与与&#x200B;*SameSite=None*&#x200B;属性不兼容的用户代理对应的正则表达式填充该变量。
   >[!NOTE]
   >请参阅[SameSite=None:已知不兼容的客户端](https://www.chromium.org/updates/same-site/incompatible-clients)以了解更多详细信息。 对于Tizen播放器，请使用正则表达式：`(.*)Tizen(.*)`。

1. 针对您的AEM 6.5.5及更高版本实例注册Tizen播放器，该播放器应正常注册和显示内容。

## 批量配置Tizen播放器{#bulk-provisioning-tizen-player}

>[!NOTE]
>在大量设备的每个设备的管理员UI中手动输入AEM服务器地址可能是一项繁琐的工作。 建议使用Samsung远程管理(RMS)解决方案来部署和管理大型解决方案。 有关更多详细信息，请参阅[将Tizen设备注册到Samsung远程管理服务(RMS)](#enroll-tizen-device-rm)。

请按照以下步骤批量配置应用程序，以在应用程序启动时指向AEM创作实例：

1. 下载并安装[Tizen Studio](https://developer.tizen.org/development/tizen-studio/download)。
1. 使用Tizen Studio打开`wgt`文件。
1. 打开文件`firmware-platform.js`并搜索`DEFAULT_PREFERENCES`，将服务器URL更改为AEM创作URL并保存。
1. 生成新的`wgt`文件。

   >[!NOTE]
   >您可能需要创建或设置签名证书。

1. 使用RMS或URL启动器部署此新的`wgt`文件，当播放器启动时，它应自动指向您的服务器，这样您就无需为每个设备手动输入它。

### 将Tizen设备注册到Samsung远程管理服务(RMS){#enroll-tizen-device-rms}

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

