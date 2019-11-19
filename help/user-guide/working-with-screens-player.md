---
title: 使用AEM Screens播放器
seo-title: 使用 Screens 播放器
description: 可查看本页以了解 Screens 播放器。本页还介绍了管理员 UI 和渠道切换程序。
seo-description: 可查看本页以了解 Screens 播放器。本页还介绍了管理员 UI 和渠道切换程序。
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Working with AEM Screens Player {#working-with-aem-screens-player}

您可以管理AEM Screens播放器上的渠道内容和其他设置。

>[!NOTE]
>
>按住 ***Ctrl+Cmd+F**可退出 OS X AEM Screens 播放器的全屏模式。*

将渠道分配给显示屏后，AEM Screens 播放器会显示内容。您可以使用管理员 UI 的首选项（在功能板中）或从播放器本身配置播放器的设置。

## 使用设备功能板 {#using-the-device-dashboard}

您可以从设备功能板中配置设备的首选项，设备功能板可通过 AEM 创作实例进行访问。

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --&gt; ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. 单击设备以打开设备功能板。

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Check the **PREFERENCES** panel. You can enable/disable the **Admin UI** and **Channel Switcher** for your player from these two options.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### 管理员 UI {#the-admin-ui}

Enabling the **Admin UI** from the preferences panel allows the user to open the admin settings from the Screens Player. 此外，如果您从设备功能板禁用此选项，则用户无法从播放器打开管理员 UI。

要从 Screens 播放器查看管理员 UI，请长按左上角打开“管理员”菜单（在 AEM Screens 触屏优化播放器中），或者使用鼠标打开该菜单。注册完成并加载渠道后，将显示信息。

>[!NOTE]
>
>此外，您还可以查看 AEM Screens 播放器应用程序的运行时间，以检查应用程序运行状况。

![chlimage_1-3](assets/chlimage_1-3.gif)

如果从侧面菜单 **中选择** Configuration **（配置）选项，则还可以从此对话框重置Firmware**（固件）、Preferences（首选项） **，或****** To Factory（至出厂）。

此外，您还可以在“最大否”中指定AEM Screens播放器要保留的最大日志 **文件数。 保存的日志文件**。 有关更多详细信息，请参阅以下屏幕截图。

>[!NOTE]
>
>“更 **新固件** ”选项仅适用于cordova，如Android播放器。

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

您可以从 AEM Screens 播放器内的管理员 UI 中清除渠道和应用程序缓存。

从侧边栏中选择&#x200B;**内容缓存**&#x200B;可更新缓存。

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### 渠道切换程序 {#the-channel-switcher}

Enabling the **Channel Switcher** from the preferences panel allows the user to open the channel selection/settings from the Screens Player.

此外，如果您从设备功能板禁用此选项，则用户无法从 Screens 播放器控制渠道首选项。

您可以从 Screens 播放器切换和控制渠道的设置。

要从播放器查看渠道切换程序，请长按左下角以打开渠道切换程序，以便切换渠道和执行其他功能。

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>您还可以从 Screens 播放器启用或禁用播放器的管理员菜单和渠道切换程序。
>
>（请参阅下面部分所述的“从 Screens 播放器更改首选项”**）。

### 从 AEM Screens 播放器管理首选项 {#managing-preferences-from-the-aem-screens-player}

您还可以从播放器本身更改管理员 UI 和渠道切换程序的设置。

请按照以下步骤从播放器更改首选项：

1. 长按空闲渠道的左上角以打开管理员面板。
1. Navigate to **Configuration** from the left action menu.
1. Enable/disable configuration for **Admin UI** or **Channel Switcher**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## AEM Screens 播放器故障诊断 {#troubleshooting-aem-screens-player}

您可以对与 AEM Screens 播放器（硬件和软件）相关的各种问题进行故障诊断：

| **问题** | **推荐** |
|---|---|
| 播放器存储已满 | 消除不必要的文件 |
| 播放器丢失网络 | 使用Cat-5/Cat-6电缆。 对于wifi，减少从路由器到播放器设备的距离 |
| AEM Screens播放器崩溃 | 建议使用一个监视应用程序，以确保AEM Screens播放器始终运行 |
| AEM Screens播放器丢失设置 | 检查与AEM服务器的连接 |
| AEM Screens播放器在播放器重新启动／重新启动后不会自动启动 | 检查操作系统启动文件夹或初始化过程 |
| AEM Screens播放器显示错误／旧内容 | 检查网络连接 |

### AEM Screens 播放器的更新 {#updates-for-aem-screens-player}

AEM Screens 播放器有两种类型的更新：

| **方法** | **详细信息** | **通过远程** | **自动化** | **0停机时间** |
|---|---|---|---|---|
| 固件更新 | 通过远程命令应用于现有已安装的播放器。 更新后，播放器将自动重新加载现有内容。 | 是 | 自定义 | 近- 1-3秒 |
| 播放器Shell更新 | 这是要在播放器上部署的新可执行文件。 这需要在播放器上远程复制新的二进制文件，然后停止当前运行的版本并启动新版本。这可能需要重新下载包的预加载内容。 | 是（通过远程Shell） | 自定义 | 否 |

## 播放器设备的硬件选择准则 {#hardware-selection-guidelines-for-player-device}

以下部分为Screens项目提供了硬件选择指南：

* 始终为PC ***播放器和********* “Display Panel”（显示面板）或“Projector”（投影仪）提供商业级或工业级组件。

* 始终与为数字标牌市场提供服务的供应商互动。
* 总是考虑环境温度和相对湿度等环境因素。
* 始终查看电源要求和电源调节。
* 仔细查看应用程序所需的性能需求和I/O端口。

下表总结了AEM Screens项目的硬件配置和典型用例：

<table>
 <tbody>
  <tr>
   <td>播放器配置</td>
   <td>处理器</td>
   <td>内存</td>
   <td>存储固态硬盘</td>
   <td>GPU</td>
   <td>显示器</td>
   <td>I/O</td>
   <td>典型用例</td>
  </tr>
  <tr>
   <td>基本</td>
   <td>双核、i3或入门级四核英特尔®凌动处理器</td>
   <td><p>4GB内存</p> <p>2MB高速缓存</p> </td>
   <td><p>·ChromeOS 32 GB</p> <p>·Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920 x 1080</td>
   <td>DVI，以太网<br /> /无线，<br /> 2xUSB</td>
   <td>
    <ul>
     <li>标准全屏循环<br /> </li>
     <li>分时段</li>
    </ul> </td>
  </tr>
  <tr>
   <td>标准</td>
   <td>四核，英特尔®酷睿i5处理器</td>
   <td><p>8GB内存</p> <p>4MB高速缓存</p> </td>
   <td>128 GBB</td>
   <td>OnBoard</td>
   <td>3840x2160(4K)</td>
   <td>DVI、HDMI<br /> Ethernet/Wireless<br /> 、2xUSB</td>
   <td>
    <ul>
     <li>单源动态内容</li>
     <li>简单的交互</li>
     <li>1-3区域布局</li>
    </ul> </td>
  </tr>
  <tr>
   <td>高级</td>
   <td>四核超线程，英特尔®酷睿i7处理器</td>
   <td><p>16GB内存</p> <p>8MB高速缓存</p> </td>
   <td>256 GB</td>
   <td>专用图形GPU</td>
   <td>3840x2160(4K)</td>
   <td>DVI、HDMI<br /> Ethernet/Wireless<br /> 、4xUSB</td>
   <td>
    <ul>
     <li>4个或更多内容区域，并发视频播放</li>
     <li>多页交互式</li>
     <li>多源数据触发器</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
