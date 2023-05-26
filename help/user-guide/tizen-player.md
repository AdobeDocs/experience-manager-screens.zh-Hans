---
title: Tizen播放器
description: 本页介绍Tizen Player的安装和工作。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '1242'
ht-degree: 1%

---

# 实施Tizen Player {#tizen-player}

## 安装Tizen播放器 {#installing-tizen-player}

请按照以下步骤实施适用于AEM Screens的Tizen Player：

1. 导航到 [AEM Screens播放器下载](https://download.macromedia.com/screens/) 页面下载Tizen播放器。

1. 安装Tizen播放器 *(.zip)* 文件来自本地计算机。

## 设置http服务器 {#setting-local-server}

>[!NOTE]
> 解压缩zip文件，并通过 `http server`. (此 `http server` 不要求为本地或Apache Server)。

应遵循以下步骤：

1. 复制两个提取的文件，例如 `AEMScreensPlayer.wgt` 和 `sssp_config.xml` 到本地Apache Web Server的根目录。

   >[!NOTE]
   >此 `AEMScreensPlayer.wgt`是实际的Tizen播放器应用程序和 `sssp_config.xml` 包含有关此映射的信息，可帮助您在Tizen设备上安装此映射。

1. 获取本地HTTP服务器的IP或URL（如果解压缩到子文件夹而不是根文件夹，则在步骤2中获取包含解压缩文件的文件夹的路径）

1. Tizen播放器从本地服务器下载安装程序。

### 命名Tizen播放器 {#name-tizen}

您可以为Tizen播放器分配一个用户友好的设备名称，从而将分配的设备名称发送到Adobe Experience Manager (AEM)。 此功能不仅允许您为Tizen播放器命名，还允许您轻松分配适当的内容。

>[!NOTE]
>您只能在注册之前选择播放器名称。 注册播放器后，无法再更改播放器名称。

按照以下步骤在Tizen播放器中配置名称：

1. 单击遥控器上的菜单按钮。
1. 导航到 **网络** —> **设备名称** 为播放器分配名称。

### 在Samsung设备上配置更新 {#config-updates}

在Samsung设备上执行以下步骤，在该设备上完成AEM Screens播放器的安装：

1. 导航到您的Samsung设备并打开。

1. 单击 **菜单** 按钮并向下滚动到 **系统** 左侧导航栏中的。

1. 向下滚动并选择 **播放方式** 选项并将其更改为 **URL启动器** 选项。
   ![图像](/help/user-guide/assets/tizen/rms-2.png)

1. 设置URL启动器后，按 **主页** 遥控器上的按钮。

1. 导航到 **URL启动器设置** 并输入本地主机服务器的IP地址，然后单击 **完成**.
   >[!NOTE]
   >Tizen播放器应能够连接到http服务器。

1. AEM Screens Player现在应自动在Samsung设备上安装和启动。

   >[!NOTE]
   >Tizen设备和 `http` 服务器应该能够相互连接，也就是说，服务器应该可以连接到Tizen播放器。


## 免除具有SameSite Cookie问题的用户代理 {#exempting-user-agents}

>[!IMPORTANT]
>**本部分适用于从Adobe Experience Manager (AEM) 6.5.5到AEM 6.5.7的版本**
>有一些浏览器引擎与 *SameSite=None* 由AEM 6.5颁发给AEM 6.7的登录令牌中使用的属性。通常，将浏览器升级到最新可用版本即可解决此问题。 在某些情况下，可能无法进行此类升级，例如使用智能显示器、机顶盒或其他具有嵌入式浏览引擎的设备。

执行以下步骤，在使用时免除这些不兼容的客户端 *SameSite=None*：

1. 升级到Adobe Experience Manager (AEM) Service Pack 6.5.7。

1. AEM重新启动后，转到 `/system/console/configMgr` 和搜索 **Granite令牌身份验证处理程序Adobe**. 设置值 **SameSite** 值至 **无**.

1. 您应该会看到一个新选项 *要免除samesite属性的用户代理*. 使用对应于用户代理（与不兼容）的正则表达式填充此代码 *SameSite=None* 属性。
   >[!NOTE]
   >参见 [SameSite=None：已知的不兼容客户端](https://www.chromium.org/updates/same-site/incompatible-clients) 了解更多详细信息。 对于Tizen播放器，使用正则表达式： `(.*)Tizen(.*)`.

1. 针对您的AEM 6.5.5及更高版本实例注册Tizen播放器，它应该可以正常注册和显示内容。

## 远程配置Tizen播放器 {#remote-provisioning}

通过远程配置Tizen Player，您可以轻松部署成百上千的Samsung Tizen显示器。 它避免了为每个播放器配置服务器URL和批量注册代码或其他参数(如果Screensas a Cloud Service配置云模式和云令牌)的繁重手动工作。

此功能允许您远程配置Tizen播放器，并在需要时集中更新这些配置。 您只需使用 `HTTP` 用于托管Tizen应用程序的服务器 `(wgt and xml file)` 和一个文本编辑器来保存 `config.json` 使用适当的参数。

确保您已在Tizen设备上配置了URL启动器地址，即“主页”按钮 — > URL启动器设置。
在 `HTTP` 托管Tizen应用程序的服务器，放置文件 `config.json` 与相同的位置 `wgt` 文件。 文件名称必须为 `config.json`。Tizen播放器将安装，并在启动时（以及每次重新启动）检查并应用 `config.json` 文件。

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
>策略配置是严格强制实施的，不会在播放器的管理员UI中手动覆盖。 要允许对特定策略进行手动播放器配置，请不要在策略配置中指定该策略，例如，如果要允许手动配置重新启动计划，请不要指定键 `rebootSchedule` 在策略配置中。 每次重新加载播放器时都会读取策略配置。

| **策略名称** | **用途** |
|---|---|
| 服务器 | Adobe Experience Manager (AEM)服务器的URL。 |
| 注册密钥 | 用于使用预共享密钥批量注册设备。 |
| 分辨率 | 设备的分辨率。 |
| rebootSchedule | 重新启动播放器的计划。 |
| enableAdminUI | 启用管理UI以在站点上配置设备。 在完全配置并投入生产后，设置为false。 |
| enableOSD | 为用户启用频道切换器UI以在设备上切换频道。 完全配置并投入生产后，请考虑将设置为false 。 |
| enableActivityUI | 启用可显示下载和同步等活动的进度。 启用以进行故障排除，并在完全配置并投入生产后禁用。 |
| cloudMode | 如果希望Tizen播放器as a Cloud Service连接到Screens，则设置为true。 设置为false以连接到AMS或本地AEM。 |
| cloudToken | 注册令牌，用于根据Screensas a Cloud Service进行注册。 |


## 正在将Tizen设备注册到Samsung远程管理服务(RMS) {#enroll-tizen-device-rms}

按照以下步骤将Tizen设备注册到Samsung远程管理服务(RMS)并远程配置URL启动器：

>[!NOTE]
>验证网络设置和显示器。

1. 导航到 **菜单** -> **网络** -> **服务器网络设置** 并按 **输入**.

1. 导航到服务器地址，然后键入MagicInfo URL access ，然后按 **完成**.

1. 设置TLS（如果需要）。 导航到端口并从服务器中选择端口号，然后单击 **保存**.

1. 导航到 **设备** 选项卡，然后检查您刚刚配置的设备。 找到设备后，单击该复选框并选择 **批准**.

   >![图像](/help/user-guide/assets/tizen/rms-3.png)

1. 填写所需信息并选择设备组。 单击 **确定** 以完成批准流程。

   >![图像](/help/user-guide/assets/tizen/rms-7.png)

1. 设备获得批准后，应会显示在“Device List”（设备列表）中。 单击 *信息* 按钮的位置，即 **i**，如下图所示。

   >![图像](/help/user-guide/assets/tizen/rms-6.png)

1. 将显示“设备信息”对话框。 选择 **设备信息** 选项卡，然后单击 **编辑**.

   >![图像](/help/user-guide/assets/tizen/rms-5.png)

1. 编辑设备选项并选择 **设置** 选项卡。 导航到 **URL启动器** 部分并输入托管wgt和的URL `SSSP config file` 安装 `SSSP` 应用程序，如下图所示。

   ![图像](/help/user-guide/assets/tizen/rms-9.png)

1. 单击 **保存** 才能使更改显示在显示屏幕上。

### 使用Screens遥控器 {#using-remote-control}

AEM Screens提供远程控制功能。 可在此处详细了解此功能： [屏幕远程控制](implementing-remote-control.md)
