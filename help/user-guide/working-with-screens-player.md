---
title: 使用AEM Screens Player
description: 了解如何使用AEM Screens播放器、管理员UI和渠道切换器。
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4faac090-ad8a-4d7e-a502-6fb63f6b2761
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---

# 使用AEM Screens Player

您可以在AEM Screens播放器上管理渠道内容和其他设置。

>[!NOTE]
>
>按&#x200B;***Ctrl+Cmd+F***，以便退出OS X AEM Screens Player的全屏模式。

将渠道分配给显示内容后，AEM Screens Player会显示内容。 您可以使用管理员UI首选项（从仪表板）或播放器本身配置播放器设置。

## 使用设备功能板 {#using-the-device-dashboard}

您可以从设备仪表板配置设备的首选项，可以通过AEM创作实例进行访问。

1. 从您的项目导航到设备仪表板，例如，***测试项目*** > ***设备***。

   从操作栏中单击&#x200B;**设备**&#x200B;和&#x200B;**设备管理器**。

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. 单击设备，以便打开设备仪表板。

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. 检查&#x200B;**首选项**&#x200B;面板。 您可以从这两个选项中为播放器启用或禁用&#x200B;**管理员UI**&#x200B;和&#x200B;**渠道切换器**。

   ![chlimage_1-68](assets/chlimage_1-68.png)

### 管理员UI {#the-admin-ui}

从首选项面板启用&#x200B;**管理员UI**&#x200B;允许用户从Screens播放器打开管理员设置。 此外，如果从设备仪表板禁用此选项，则用户无法从播放器打开管理员UI。

要从Screens播放器查看管理员UI，请在启用了触摸的AEM Screens播放器上或者使用鼠标长按左上角以打开管理员菜单。 完成注册并加载渠道后，将显示信息。

>[!NOTE]
>
>此外，您还可以查看AEM Screens Player应用程序正常运行时间，以检查应用程序运行状况。

![chlimage_1-3](assets/chlimage_1-3.gif)

#### 访问配置菜单选项 {#configuration-options}

如果单击侧菜单中的&#x200B;**配置**&#x200B;选项，则可以更新配置，如下图所示：

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

利用Configuration菜单，可修改以下设置：

* 从此对话框将&#x200B;**固件**、**首选项**&#x200B;或&#x200B;**重置为工厂**。

* 在&#x200B;**最大数量中指定要为AEM Screens Player保留的最大日志文件数。 要保留**&#x200B;的日志文件。

* 为Screens播放器启用或禁用&#x200B;**管理员菜单**、**渠道切换器**&#x200B;和&#x200B;**活动UI**。

  如果从&#x200B;**配置**&#x200B;菜单启用了&#x200B;**活动UI**，AEM Screens播放器在播放器的右上角将显示&#x200B;*播放器活动通知*，如下图所示。

  ![图像](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>**更新固件**&#x200B;选项仅适用于Cordova，例如Android™播放器。

>[!NOTE]
>
>建议在生产部署中禁用&#x200B;**管理员UI**。

#### 访问内容缓存菜单选项 {#content-cache-options}

您可以从AEM Screens Player的管理界面中清除渠道和应用程序的缓存。

单击侧边栏中的&#x200B;**内容缓存**，以便更新缓存。

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### 渠道切换器 {#the-channel-switcher}

从首选项面板启用&#x200B;**渠道切换器**&#x200B;可让用户从Screens播放器打开渠道选择设置。

此外，如果从设备仪表板禁用此选项，则用户无法从Screens播放器控制渠道首选项。

您可以从Screens播放器切换和控制渠道设置。

要从播放器查看频道切换器，请长按左下角以打开允许切换频道和其他功能的频道切换器。

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>您还可以在Screens播放器中启用或禁用播放器的管理菜单和渠道切换器。
>
>(请参阅以下部分中所述的&#x200B;*从Screens Player更改首选项*)。

### 从AEM Screens播放器管理首选项

您还可以在播放器本身中更改管理员UI和渠道切换器的设置。

要更改播放器的首选项，请执行以下操作：

1. 长按空闲频道左上角以打开管理面板。
1. 从左侧操作菜单中导航到&#x200B;**配置**。
1. 启用或禁用&#x200B;**管理员UI**&#x200B;或&#x200B;**渠道切换器**&#x200B;的配置。

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## AEM Screens Player疑难解答

您可以对与AEM Screens Player（硬件和软件）相关的各种问题进行故障诊断：

| **问题** | **Recommendations** |
|---|---|
| 播放器存储空间已满 | 消除不必要的文件 |
| 播放器丢失网络 | 使用Cat-5或Cat-6电缆。 对于WiFi，缩短路由器与播放器设备之间的距离 |
| AEM Screens Player崩溃 | 建议使用监视程序应用程序来确保AEM Screens Player始终运行 |
| AEM Screens Player设置丢失 | 检查与AEM服务器的连接 |
| AEM Screens Player在播放器重新启动或重新启动后不会自动启动 | 检查操作系统启动文件夹或初始化过程 |
| AEM Screens Player显示错误或旧内容 | 检查网络连接 |

### AEM Screens Player更新

AEM Screens Player有两种类型的更新：

| **方法** | **详细信息** | 通过Remote **的** | **自动** | **0停机时间** |
|---|---|---|---|---|
| 固件更新 | 通过远程命令应用于现有安装的播放器。 更新后，播放器将自动重新加载现有内容。 | 是 | 自定义 | 几乎 — 1-3秒 |
| 播放器外壳更新 | 在播放器上部署的新可执行文件。 此功能要求您在播放器上远程复制新的二进制文件，并停止当前正在运行的二进制文件以及启动新版本。 它可能需要再次下载预加载的包。 | 是（通过远程shell） | 自定义 | 否 |

## 播放器设备的硬件选择准则 {#hardware-selection-guidelines-for-player-device}

以下部分提供了Screens项目的硬件选择准则：

* 始终为PC播放器和显示面板或投影仪提供&#x200B;***商业***&#x200B;或&#x200B;***工业***&#x200B;级组件。

* 始终与为数字标牌市场提供服务的供应商接洽。
* 始终考虑环境因素，如环境温度和相对湿度。
* 始终查看电源要求和电源调节。
* 仔细查看应用程序所需的性能需求和I/O端口。

下表总结了AEM Screens项目的硬件配置以及典型用例：

<table>
 <tbody>
  <tr>
   <td>播放器配置</td>
   <td>处理器</td>
   <td>内存</td>
   <td>存储SSD</td>
   <td>GPU</td>
   <td>显示区</td>
   <td>I/O</td>
   <td>典型用例</td>
  </tr>
  <tr>
   <td>基本</td>
   <td>双核、i3或入门级四核英特尔®凌动处理器</td>
   <td><p>4 GB内存</p> <p>2 MB缓存</p> </td>
   <td><p>*ChromeOS 32 GB</p> <p>*Windows 128 GB</p> </td>
   <td>板载</td>
   <td>1920 x 1080</td>
   <td>DVI<br />以太网/无线<br /> 2个USB</td>
   <td>
    <ul>
     <li>标准全屏循环<br /> </li>
     <li>日划分</li>
    </ul> </td>
  </tr>
  <tr>
   <td>标准</td>
   <td>四核、英特尔®酷睿™ i5处理器</td>
   <td><p>8 GB内存</p> <p>4 MB缓存</p> </td>
   <td>128 GB</td>
   <td>板载</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI、HDMI<br />以太网/无线、<br /> 2个USB</td>
   <td>
    <ul>
     <li>单个Source动态内容</li>
     <li>简单交互式</li>
     <li>1-3区域布局</li>
    </ul> </td>
  </tr>
  <tr>
   <td>高级</td>
   <td>四核，带超线程，英特尔®酷睿™ i7处理器</td>
   <td><p>16 GB内存</p> <p>8 MB缓存</p> </td>
   <td>256 GB</td>
   <td>专用显卡GPU</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI、HDMI<br />以太网/无线、<br /> 4个USB</td>
   <td>
    <ul>
     <li>4个或更多内容区域，并行视频播放</li>
     <li>多页交互式</li>
     <li>多Source数据触发器</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
