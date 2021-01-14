---
title: Tizen Player
description: 本页介绍Tizen Player的安装和工作。
translation-type: tm+mt
source-git-commit: c1e7187ad3841cde08377d6daf700885d17706ba
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---


# 实现Tizen Player {#tizen-player}

## 安装Tizen Player {#installing-tizen-player}

请按照以下步骤为AEM Screens实施Tizen Player:

1. 导航至[AEM 6.5 Player下载](https://download.macromedia.com/screens/)页面以下载Tizen Player。

1. 从本地计算机安装Tizen播放器&#x200B;*(.zip)*&#x200B;文件。

## 设置本地服务器并解压Zip文件{#setting-local-server}

请按照以下步骤设置本地服务器并复制解压缩的文件：

1. 获取本地计算机的IP地址。
   >[!NOTE]
   >请查看官方文档，了解如何在您的平台上启用本地服务器。

1. 从终端，导航到解压缩的安装程序文件夹的同一目录，并验证localhost是否正在工作。

1. Tizen播放器将从本地服务器下载安装程序。

1. 将两个解压缩的文件（如`AEMScreensPlayer.wgt`和`sssp_config.xml`）复制到本地Apache Web服务器的根目录中。

   >[!NOTE]
   >`AEMScreensPlayer.wgt`是实际的Tizen播放器应用程序，`sssp_config.xml`包含有关此映射的信息，可帮助您将其安装在Tizen设备上。

### 在Samsung设备{#config-updates}上配置更新

按照Samsung设备上的以下步骤在设备上完成AEM Screens播放器的安装：

1. 导航到Samsung设备并打开。

1. 单击设备远程设备上的&#x200B;**MENU**&#x200B;按钮，并从左侧导航栏向下滚动到&#x200B;**System**。

1. 向下滚动并选择“通过URL启动器播放&#x200B;**”选项。**
   ![图像](/help/user-guide/assets/tizen/url-launcher.png)

1. 按遥控器上的&#x200B;**Home**&#x200B;按钮。

1. 输入本地主机服务器的IP地址。

1. 从&#x200B;**开发者模式**&#x200B;中选择&#x200B;**远程**。

1. 单击设备远程设备中的&#x200B;**主页**&#x200B;按钮并选择&#x200B;**URL Launcher**。

1. 现在，AEM Screens播放器应自动在您的Samsung设备上安装和启动。

## Tizen Player的批量配置{#bulk-provisioning-tizen-player}

>[!NOTE]
>在大量设备的每台设备的管理员UI中手动输入AEM服务器的地址可能非常繁琐。 建议使用Samsung远程管理(RMS)解决方案来部署和管理该解决方案。 有关更多详细信息，请参阅[将Tizen设备登记到Samsung远程管理服务(RMS)](#enroll-tizen-device-rm)。

请按照以下步骤批量配置启动时指向AEM作者实例的应用程序：

1. 下载并安装[Tizen Studio](https://developer.tizen.org/development/tizen-studio/download)。
1. 使用Tizen Studio打开`wgt`文件。
1. 打开文件`firmware-platform.js`并搜索`DEFAULT_PREFERENCES`，将服务器URL更改为AEM作者URL并保存。
1. 构建新的`wgt`文件。

   >[!NOTE]
   >您可能需要创建或设置签名证书。

1. 部署此新的`wgt`文件RMS，当播放器启动时，它应自动指向服务器，因此您无需为每个设备手动输入它。

### 将Tizen设备登记到Samsung远程管理服务(RMS){#enroll-tizen-device-rms}

请按照以下步骤将Tizen设备注册到Samsung Remote Management Service(RMS)并远程配置URL Launcher:

>[!NOTE]
>验证网络设置和监视器。

1. 导航至&#x200B;**Menu** -> **Network** -> **Server Network Settings**，然后按&#x200B;**Enter**。

   >[!NOTE]
   >验证屏幕是否设置为“通过URL启动器播放”。

1. 导航到“服务器地址”并键入MagicInfo URL访问权限，然后按“完成”。

1. 根据情况设置要使用或不使用的TLS
   1. 转到端口并从服务器中选择端口号。
   1. 选项准备就绪后，单击“保存”。

1. 登录到MIS后，导航到设备选项卡
   1. 查看IP地址和／或其Mac地址，查找您刚刚配置的设备。
   1. 找到某台设备后，单击该复选框并选择批准。

1. 单击“已批准”按钮后，将显示以下弹出窗口
   1. 填写所需信息
   1. 选择设备组
   1. 单击“确定”按钮以完成审批过程。

1. 设备获得批准后，在设备列表上应显示如下。
   1. 单击设备框“i”上的“信息”按钮

1. 设备信息弹出窗口将如下所示，然后单击编辑按钮。

1. 编辑设备选项，然后选择&#x200B;**设置**&#x200B;选项卡。

1. 导航到&#x200B;**URL Launcher**&#x200B;部分，并输入承载wgt的URL和`SSSP config file`以安装`SSSP`应用程序，如下图所示。

   ![图像](/help/user-guide/assets/tizen/rms-9.png)

1. 单击&#x200B;**保存**&#x200B;以使更改在显示屏上生效。




