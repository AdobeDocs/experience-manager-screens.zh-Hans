---
title: 使用AEM Screens Player
seo-title: Working with Screens Player
description: 按照此页面了解Screens播放器。 它还介绍了管理员UI和渠道切换器。
seo-description: Follow this page to learn about Screens Player. It also explains the Admin UI and the Channel Switcher.
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4faac090-ad8a-4d7e-a502-6fb63f6b2761
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---

# 使用AEM Screens Player {#working-with-aem-screens-player}

您可以在AEM Screens Player上管理渠道内容和其他设置。

>[!NOTE]
>
>按 ***Ctrl+Cmd+F*** 退出OS X AEM Screens Player的全屏模式。

将渠道分配给显示区后，AEM Screens Player会显示内容。 您可以使用管理员UI的首选项（从仪表板）或播放器本身，为播放器配置设置。

## 使用设备功能板 {#using-the-device-dashboard}

您可以从设备仪表板配置设备的首选项，可以通过AEM创作实例访问。

1. 从项目中导航到设备仪表板，例如， ***测试项目*** —> ***设备***.

   选择 **设备** 和 **设备管理器** 操作栏中的。

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. 单击设备以打开设备仪表板。

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. 查看 **首选项** 面板。 您可以启用/禁用 **管理员UI** 和 **渠道切换器** 从这两个选项为您的播放器提供支持。

   ![chlimage_1-68](assets/chlimage_1-68.png)

### 管理员UI {#the-admin-ui}

启用 **管理员UI** 通过“首选项”面板，用户可以从Screens播放器打开管理员设置。 此外，如果从设备仪表板禁用此选项，则用户无法从播放器打开管理员UI。

要从Screens播放器查看管理员UI，请在左上角长按以打开“管理员”菜单、在启用了触摸的AEM Screens播放器上或者使用鼠标。 它会在注册完成后显示信息并加载渠道。

>[!NOTE]
>
>此外，您还可以查看AEM Screens Player应用程序正常运行时间，以检查应用程序运行状况。

![chlimage_1-3](assets/chlimage_1-3.gif)

#### 访问配置菜单选项 {#configuration-options}

如果选择 **配置** 侧菜单中的选项，如下图所示：

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

利用Configuration菜单，可修改以下设置：

* 重置 **固件**， **首选项**，或 **到工厂** 从该对话框中。

* 指定AEM Screens播放器保留的最大日志文件数 **最大数量 要保留的日志文件**.

* 启用或禁用 **管理员菜单**， **渠道切换器**、和 **活动UI** 用于屏幕播放器。

   如果 **活动UI** 已启用，从 **配置** 菜单，AEM Screens播放器会显示 *播放器活动通知* 播放器右上角的位置，如下图所示。

   ![图像](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>此 **更新固件** 选项仅适用于cordova，例如Android播放器。

>[!NOTE]
>
>建议 **管理员UI** 在生产部署中被禁用。

#### 访问内容缓存菜单选项 {#content-cache-options}

您可以从AEM Screens播放器中的管理员UI中清除渠道和应用程序的缓存。

选择 **内容缓存** 以更新缓存。

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### 渠道切换器 {#the-channel-switcher}

启用 **渠道切换器** 通过“首选项”面板，用户可以从Screens播放器打开渠道选择/设置。

此外，如果从设备仪表板禁用此选项，则用户无法从Screens播放器控制渠道首选项。

您可以从Screens播放器切换和控制渠道设置。

要从播放器查看频道切换器，请在左下角长按以打开允许切换频道和其他功能的频道切换器。

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>您还可以在Screens播放器中启用或禁用播放器的管理菜单和渠道切换器。
>
>(请参阅 *从Screens播放器更改首选项* （如下节所述）。

### 从AEM Screens Player管理首选项 {#managing-preferences-from-the-aem-screens-player}

您还可以从播放器本身更改管理员UI和渠道切换器的设置。

按照以下步骤更改播放器的首选项：

1. 长按空闲频道左上角以打开“管理”面板。
1. 导航到 **配置** 从左侧的“操作”菜单中。
1. 启用/禁用配置 **管理员UI** 或 **渠道切换器**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## AEM Screens Player疑难解答 {#troubleshooting-aem-screens-player}

您可以对与AEM Screens Player（硬件和软件）相关的各种问题进行故障诊断：

| **问题** | **推荐** |
|---|---|
| 播放器存储空间已满 | 消除不必要的文件 |
| 播放器丢失网络 | 使用Cat-5/Cat-6缆线。 对于Wifi，请缩短路由器与播放器设备之间的距离 |
| AEM Screens Player崩溃 | 建议设置一个监视程序应用程序，以确保AEM Screens Player始终运行 |
| AEM Screens Player丢失设置 | 检查与AEM服务器的连接 |
| AEM Screens Player不会在播放器重新启动/重新引导后自动启动 | 检查操作系统启动文件夹或初始化过程 |
| AEM Screens Player显示错误/旧的内容 | 检查网络连接 |

### AEM Screens Player更新 {#updates-for-aem-screens-player}

AEM Screens Player有两种类型的更新：

| **方法** | **详细信息** | **通过远程** | **自动** | **0停机** |
|---|---|---|---|---|
| 固件更新 | 通过远程命令应用于现有安装的播放器。 更新后，播放器将自动重新加载现有内容。 | 是 | 自定义 | 几乎 — 1-3秒 |
| 播放器外壳更新 | 这是要在播放器上部署的新可执行文件。 这需要在播放器上远程复制新二进制文件，并停止当前运行并启动新版本。 这可能需要重新下载预加载的包。 | 是（通过远程shell） | 自定义 | 否 |

## 播放器设备的硬件选择准则 {#hardware-selection-guidelines-for-player-device}

以下部分提供了Screens项目的硬件选择准则：

* 始终源 ***商业*** 或 ***工业*** PC播放器和显示面板或投影仪的等级组件。

* 始终与服务数字标牌市场的供应商接洽。
* 请务必考虑环境因素，如环境温度和相对湿度。
* 请务必查看电源要求和电源调节。
* 仔细审查应用程序所需的性能需求和I/O端口。

下表总结了AEM Screens项目的硬件配置以及典型用例：

<table>
 <tbody>
  <tr>
   <td>播放器配置</td>
   <td>处理器</td>
   <td>内存</td>
   <td>存储SSD</td>
   <td>GPU</td>
   <td>显示器</td>
   <td>I/O</td>
   <td>典型用例</td>
  </tr>
  <tr>
   <td>基本</td>
   <td>双核、i3或入门级四核英特尔®凌动处理器</td>
   <td><p>4GB内存</p> <p>2MB高速缓存</p> </td>
   <td><p>·ChromeOS 32 GB</p> <p>·Windows 128GB</p> </td>
   <td>板载</td>
   <td>1920x1080</td>
   <td>DVI、<br /> 以太网/无线、<br /> 2个USB</td>
   <td>
    <ul>
     <li>标准全屏循环<br /> </li>
     <li>日划分</li>
    </ul> </td>
  </tr>
  <tr>
   <td>标准</td>
   <td>四核、英特尔®酷睿i5处理器</td>
   <td><p>8GB内存</p> <p>4MB缓存</p> </td>
   <td>128 GBB</td>
   <td>板载</td>
   <td>3840x2160 (4K)</td>
   <td>DVI、HDMI<br /> 以太网/无线、<br /> 2个USB</td>
   <td>
    <ul>
     <li>单一来源动态内容</li>
     <li>简单交互式</li>
     <li>1-3区域布局</li>
    </ul> </td>
  </tr>
  <tr>
   <td>高级</td>
   <td>四核超线程，英特尔®酷睿i7处理器</td>
   <td><p>16 GB内存</p> <p>8MB缓存</p> </td>
   <td>256 GB</td>
   <td>专用图形GPU</td>
   <td>3840x2160 (4K)</td>
   <td>DVI、HDMI<br /> 以太网/无线、<br /> 4个USB</td>
   <td>
    <ul>
     <li>4个或更多内容区域，并发视频播放</li>
     <li>多页交互式</li>
     <li>多源数据触发器</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
