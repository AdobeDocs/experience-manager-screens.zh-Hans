---
title: Tizen播放器
description: 了解Tizen播放器的安装和工作。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 1%

---

# 实施Tizen播放器 {#tizen-player}

## 安装Tizen播放器 {#installing-tizen-player}

请按照以下步骤实施AEM Screens的Tizen播放器：

1. 导航到[AEM Screens播放器下载](https://download.macromedia.com/screens/)页面，以便下载Tizen播放器。

1. 从本地计算机安装Tizen播放器&#x200B;*(.zip)*&#x200B;文件。

## 设置http服务器 {#setting-local-server}

>[!NOTE]
> 解压缩zip文件，并通过`http server`使Tizen播放器可用。 （`http server`不需要是本地或Apache服务器）。

应遵循以下步骤：

1. 将两个提取的文件（如`AEMScreensPlayer.wgt`和`sssp_config.xml`）复制到本地Apache Web Server的根目录。

   >[!NOTE]
   >`AEMScreensPlayer.wgt`是实际的Tizen播放器应用程序，`sssp_config.xml`包含有关此映射的信息以帮助您在Tizen设备上安装它。

1. 获取本地HTTP服务器的IP或URL（以及步骤2中包含已提取文件的文件夹的路径，如果已提取到子文件夹而不是根文件夹）。

1. Tizen播放器将从本地服务器下载安装程序。

### 命名Tizen播放器 {#name-tizen}

您可以为Tizen播放器分配一个用户友好的设备名称，然后将分配的设备名称发送到Adobe Experience Manager (AEM)。 此功能不仅允许您为Tizen播放器命名，还允许您轻松分配相应的内容。

>[!NOTE]
>您只能在注册之前选择播放器名称。 注册播放器后，无法再更改播放器名称。

按照以下步骤在Tizen播放器中配置名称：

1. 单击遥控器上的菜单按钮。
1. 导航到&#x200B;**网络** > **设备名称**，以便为播放器分配名称。

### 在Samsung设备上配置更新 {#config-updates}

在Samsung设备上执行以下步骤，以便在该设备上完成AEM Screens Player的安装：

1. 导航到您的Samsung设备并打开。
1. 单击设备遥控器上的&#x200B;**菜单**&#x200B;按钮，然后从左侧导航栏向下滚动到&#x200B;**系统**。
1. 向下滚动，单击&#x200B;**通过**&#x200B;播放选项，并将其更改为&#x200B;**URL启动器**&#x200B;选项。
   ![图像](/help/user-guide/assets/tizen/rms-2.png)
1. 设置URL启动器后，按遥控器上的&#x200B;**主页**&#x200B;按钮。
1. 导航到&#x200B;**URL启动器设置**，输入本地主机服务器的IP地址，然后单击&#x200B;**完成**。

   >[!NOTE]
   >Tizen播放器应能够连接到HTTP服务器。

1. AEM Screens Player会自动在您的Samsung设备上安装和启动。

   >[!NOTE]
   >Tizen设备和`http`服务器都应该能够相互连接，也就是说，服务器应该可以访问Tizen播放器。


## 免除具有SameSite Cookie问题的用户代理 {#exempting-user-agents}

>[!IMPORTANT]
>**本部分适用于Adobe Experience Manager (AEM) 6.5.5至AEM 6.5.7**
>
>有一些浏览器引擎与AEM 6.5.5颁发给AEM 6.5.7的登录令牌中使用的&#x200B;*`SameSite=None`*&#x200B;属性不兼容。通常，将浏览器升级到最新可用版本即可解决此问题。 有时，可能无法进行此类升级，例如使用智能显示屏、机顶盒或其他具有嵌入式浏览引擎的设备。

使用&#x200B;*SameSite=None*&#x200B;时，请按照以下步骤免除这些不兼容的客户端：

1. 升级到Adobe Experience Manager (AEM) Service Pack 6.5.7。

1. AEM重新启动后，转到`/system/console/configMgr`并搜索&#x200B;**Adobe Granite令牌身份验证处理程序**。 将&#x200B;**SameSite**&#x200B;的值设置为&#x200B;**无**。

1. 您应该会看到一个新选项&#x200B;*`User agents to be exempted from samesite attribute`*。 使用与&#x200B;*SameSite=None*&#x200B;属性不兼容的用户代理对应的正则表达式填充此选项。

   >[!NOTE]
   >
   >有关更多详细信息，请参阅[SameSite=None：已知的不兼容客户端](https://www.chromium.org/updates/same-site/incompatible-clients)。 对于Tizen播放器，请使用正则表达式： `(.*)Tizen(.*)`。

1. 针对您的AEM 6.5.5及更高版本实例注册Tizen播放器，它应该可以正常注册并显示内容。

## 远程配置Tizen播放器 {#remote-provisioning}

通过远程配置Tizen播放器，您可以轻松部署成百上千个Samsung Tizen显示器。 它避免手动为每个播放器配置服务器URL和批量注册代码或其他参数。 如果有AEM Screens as a Cloud Service，则还要配置云模式和云令牌。

此功能允许您远程配置Tizen播放器，并在必要时集中更新这些配置。 您只需要用于托管Tizen应用程序`(wgt and xml file)`的`HTTP`服务器和一个文本编辑器，以便使用适当的参数保存`config.json`。

确保您已在Tizen设备上配置URL启动器地址。 单击“Home”（主页）按钮>“URL Launcher settings”（URL启动器设置）。
在托管Tizen应用程序的`HTTP`服务器上，将文件`config.json`放在与`wgt`文件相同的位置。 文件名必须为`config.json`。
Tizen播放器在启动时（以及每次重新启动）安装并应用`config.json`文件中的设置。

### 示例JSON策略 {#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### 策略属性和目的 {#policy-attributes}

下表总结了策略及其功能。

>[!NOTE]
>播放器的管理员UI策略配置是严格强制的，不会手动覆盖。 要允许为特定策略手动配置播放器，请不要在策略配置中指定该策略。
>&#x200B;>例如，如果要允许手动配置重新启动计划，请不要在策略配置中指定键`rebootSchedule`。 每次重新加载播放器时都会读取策略配置。

| **策略名称** | **用途** |
|---|---|
| 服务器 | Adobe Experience Manager (AEM)服务器的URL。 |
| 注册密钥 | 用于使用预共享密钥批量注册设备。 |
| 分辨率 | 设备的分辨率。 |
| rebootSchedule | 重新启动播放器的计划。 |
| enableAdminUI | 启用管理UI以在站点上配置设备。 在完全配置并投入生产后，设置为false。 |
| enableOSD | 为用户启用通道切换器UI以在设备上切换通道。 在完全配置并投入生产后，请考虑将其设置为false 。 |
| enableActivityUI | 启用，以便显示活动的进度，例如下载和同步。 在完全配置并投入生产后，启用以进行故障排除并禁用。 |
| 云模式 | 如果希望Tizen播放器连接到Screens as a Cloud Service，则设置为true。 设置为false以连接到AMS或本地AEM。 |
| cloudToken | 注册令牌以针对Screens as a Cloud Service进行注册。 |


## 正在将Tizen设备注册到Samsung远程管理服务(RMS) {#enroll-tizen-device-rms}

按照以下步骤将Tizen设备注册到Samsung远程管理服务(RMS)并远程配置URL启动器：

>[!NOTE]
>验证网络设置和监视器。

1. 导航到&#x200B;**菜单** -> **网络** -> **服务器网络设置**，然后按&#x200B;**Enter**。

1. 导航到服务器地址并键入MagicInfo URL访问，然后按&#x200B;**完成**。

1. 设置TLS（如有必要）。 导航到端口，单击服务器上的端口号，然后单击&#x200B;**保存**。

1. 导航到&#x200B;**设备**&#x200B;选项卡并检查您配置的设备。 找到设备后，单击该复选框，然后单击&#x200B;**批准**。

   >![图像](/help/user-guide/assets/tizen/rms-3.png)

1. 填写所需信息并单击设备组。 单击&#x200B;**确定**。

   >![图像](/help/user-guide/assets/tizen/rms-7.png)

1. 设备获得批准后，就会出现在“Device List（设备列表）”中。 单击设备框上的&#x200B;*信息*，如下所示。

   >![图像](/help/user-guide/assets/tizen/rms-6.png)

1. 将显示“设备信息”对话框。 单击&#x200B;**设备信息**&#x200B;选项卡，然后单击&#x200B;**编辑**。

   >![图像](/help/user-guide/assets/tizen/rms-5.png)

1. 编辑设备选项，然后单击&#x200B;**设置**&#x200B;选项卡。 导航到&#x200B;**URL启动器**&#x200B;部分，然后输入托管wgt的URL和`SSSP config file`，以便您可以安装`SSSP`应用程序，如下图所示。

   ![图像](/help/user-guide/assets/tizen/rms-9.png)

1. 单击&#x200B;**保存**。

### 使用Screens远程控制 {#using-remote-control}

AEM Screens提供远程控制功能。 在此处了解有关此功能的更多信息：[Screens远程控制](implementing-remote-control.md)
