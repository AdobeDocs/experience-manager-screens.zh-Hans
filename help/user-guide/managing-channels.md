---
title: 创建和管理渠道
seo-title: 管理渠道
description: 可查看本页以了解有关创建和管理渠道的信息。本页还介绍了渠道功能板，以及如何编辑渠道的内容。
seo-description: 可查看本页以了解有关创建和管理渠道的信息。本页还介绍了渠道功能板，以及如何编辑渠道的内容。
uuid: cdf09ced-9089-4249-ba51-471d6fa0e507
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: a8006686-8ee5-4971-ab79-0c7b01f108f2
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 创建和管理渠道 {#creating-and-managing-channels}

渠道可显示一系列内容以及显示的图像和视频，但也可以显示网站或单页应用程序。

本页显示了如何为 Screens 创建和管理渠道。

**先决条件**：

* [配置和部署 Screens](configuring-screens-introduction.md)
* [创建和管理Screens项目](creating-a-screens-project.md)

## 创建新渠道 {#creating-a-new-channel}

创建 Screens 项目后，请按照以下步骤为 Screens 项目创建新渠道：

1. 选择 Adobe Experience Manager 链接（左上方），然后选择“屏幕”。Alternatively, you can ﻿go directly to: `https://localhost:4502/screens.html/content/screens`.
1. Navigate to Screens project and click **Channels**.
1. Click **Create** next to the plus icon in the action bar. 此时会打开一个向导（请参阅“渠道类型”以了解更多信息&#x200B;**）。

1. Select the template from the wizard and click **Next**.
1. Enter the properties for **Title and Tags**, **More Titles and Description**, **On/Off Time**, and **Vanity URL**.

1. 单击&#x200B;**创建**，随即会创建渠道并将其添加到渠道文件夹中。

### 渠道类型 {#channel-types}

可以在向导中使用以下模板选项，例如：

| **模板选项** | **描述** |
|---|---|
| 渠道文件夹 | 允许创建一个文件夹来存储渠道的集合。 |
| 序列渠道 | 允许创建按顺序播放组件（在幻灯片中逐个播放）的渠道。 |
| 应用程序渠道 | 允许在 Screens 播放器中显示您的自定义 Web 应用程序。 |
| 1x1 分屏渠道 | 允许在单个区域中查看组件。 |
| 1x2 分屏渠道 | 允许在两个区域（水平拆分）中查看资产。 |
| 2X1分屏通道 | 允许在两个区域（垂直拆分）中查看资产。 |
| 2x2 分屏渠道 | 允许在四个区域（在矩阵中水平和垂直拆分）中查看资产。 |
| 2x3 分屏渠道 | 允许查看两个区域（水平拆分）中的资产，其中一个区域大于另一个区域。 |
| 左右L栏分屏渠道 | 允许内容作者查看大小适当的区域中不同类型的资产。 |

>[!NOTE]
>
>“分屏”通道将显示屏拆分为多个区域，这样您可以同时并排播放多个体验。 体验可以是静态资产／文本或嵌入式序列。

The following example shows the creation of a Sequence Channel (C *hannelOne*) for a Screens project (*DemoProject*).

![demochannel](assets/demochannel.gif)

>[!NOTE]
>
>您可以使用模板选项（例如上面所述的 1x2 分屏渠道、2x2 分屏渠道或 2x3 分屏渠道）创建不同的区域。

***重要说明***:

在创建渠道并向渠道中添加内容后，下一步是创建位置，之后是创建显示屏。此外，您还需要将该渠道分配到显示屏。请参阅此部分末尾的资源以了解更多信息。

## 使用渠道 {#working-with-channels}

您可以编辑、复制、预览和删除渠道，以及查看渠道属性和功能板。

>[!NOTE]
>
>单击左侧的图标可选择某个项目。例如，单击渠道图标后，可执行以下操作，如下图所示。

![screen_shot_2019-07-24at103723am](assets/screen_shot_2019-07-24at103723am.png)

### 在渠道中添加/编辑内容 {#adding-editing-content-to-a-channel}

要在渠道中添加或编辑内容，请按照以下步骤操作：

1. 单击要编辑的渠道（如上图所示）。
1. Click **Edit** from the top left corner of the action bar to edit the channel properties. 此时会打开编辑器，您可以在其中将资产/组件添加到要发布的渠道。

>[!NOTE]
>
>您可以向渠道添加组件。 有关更多 **[详细信息，请参阅将组件添加到渠道](adding-components-to-a-channel.md)** 。

![demochannel1](assets/demochannel1.gif)

**将视频上传到渠道** 按照以下步骤将视频上传到渠道：

1. 选择要上传视频的渠道。
1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。
1. 在“资产”下选择&#x200B;**视频**，然后拖放所需的视频。

>[!NOTE]
>
>If you encounter issues uploading videos in your channel, see [Troubleshooting Videos](troubleshoot-videos.md).

### 查看属性 {#viewing-properties}

要查看或编辑渠道的属性，请按照以下步骤操作：

1. 单击要编辑的渠道。
1. Click **Properties** from the action bar to view/edit the channel properties. 您可以在以下选项卡中更改选项。

![属性](assets/properties.gif)

### 查看功能板 {#viewing-dashboard}

要查看渠道的功能板，请按照以下步骤操作：

1. 单击要编辑的渠道。
1. Click **Dashboard** from the action bar to view the dashobard. The **CHANNEL INFORMATION**,**ASSIGNED DISPLAYS**, and **PENDING LAUNCHES** panel opens, as shown in the figure below:

![仪表板](assets/dashboard.gif)

### 渠道信息 {#channel-information}

“渠道信息”面板描述了渠道属性以及渠道的预览。 此外，该面板还提供了有关渠道是处于脱机还是联机状态的信息。

单击&#x200B;**渠道信息**&#x200B;操作栏中的 (**...**) 可查看渠道属性、编辑渠道内容或更新渠道缓存（脱机内容）。

![screen_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

### 联机和脱机渠道 {#online-and-offline-channels}

>[!NOTE]
>
>默认情况下，当您创建渠道时，该渠道为脱机。

创建渠道时，可以将其定义为联机渠道或脱机渠道。

An ***Online Channel***, will show the updated content in the real time environment whereas an ***Offline Channel***, shows the cached content.

请按照以下步骤使渠道处于联机状态：

1. 导航到渠道（**TestProject** --&gt; **渠道** --&gt; **TestChannel**）。

   选择渠道。

   ![screen_shot_2019-08-01at31406pm](assets/screen_shot_2019-08-01at31406pm.png)

   Click **Dashboard** from the action bar to view the status of the player. **渠道信息**面板提供有关渠道是联机还是脱机的信息。

   ![screen_shot_2019-08-01at31458pm](assets/screen_shot_2019-08-01at31458pm.png)

1. 单击操作栏中的&#x200B;**属性**，然后导航到&#x200B;**渠道**&#x200B;选项卡，如下所示：

   ![screen_shot_2019-08-01at31542pm](assets/screen_shot_2019-08-01at31542pm.png)

1. 选中“开 **发人** 员”模式 **（强制渠道联机）** ，使渠道联机。

   单击&#x200B;**保存并关闭**&#x200B;以保存您的选项。

   ![screen_shot_2019-08-01at31658pm](assets/screen_shot_2019-08-01at31658pm.png)

   Navigate back to the channel dashboard and now the **CHANNEL INFORMATION** panel shows the online status of the player.

   ![screen_shot_2019-08-01at31821pm](assets/screen_shot_2019-08-01at31821pm.png)

>[!NOTE]
>
>如果要再次将渠道配置为脱机，请从“属性”选项卡(如第(3)步所示)中取消选中“开发人员模式”选项，然后从“渠道信息 **”面板中单击“** 更新脱机内容 ********”，如下图所示。

![dashboard2](assets/dashboard2.gif)

#### 设备功能板中的自动更新与手动更新 {#automatic-versus-manual-updates-from-the-device-dashboard}

下表总结了与设备功能板中的自动更新和手动更新相关的事件。

<table>
 <tbody>
  <tr>
   <td><strong>事件</strong></td>
   <td><strong>设备自动更新</strong></td>
   <td><strong>设备手动更新</strong></td>
  </tr>
  <tr>
   <td>在线渠道的更改</td>
   <td>内容已自动更新</td>
   <td><p>在“设备：推送配置”</p> <p>或者，</p> <p>设备上更新的 <strong><i>内容：重新启动</i></strong></p> </td>
  </tr>
  <tr>
   <td>脱机渠道中的更改，但不会触发渠道“推送内容”（无脱机包重新创建）</td>
   <td>无内容更新</td>
   <td>无内容更新</td>
  </tr>
  <tr>
   <td>将触发脱机渠道和渠道“推送内容”中的更改（新的脱机包）</td>
   <td>内容已自动更新</td>
   <td><p>设备上更新的 <strong><i>内容：推送配置</i></strong></p> <p>或者，</p> <p>设备上更新的 <strong><i>内容：重新启动</i></strong></p> </td>
  </tr>
  <tr>
   <td><p>配置更改</p>
    <ul>
     <li>显示（强制渠道）</li>
     <li>设备</li>
     <li>渠道分配（新渠道，已删除渠道）</li>
     <li>渠道分配（角色、事件、计划）</li>
    </ul> </td>
   <td>配置已自动更新</td>
   <td><p>在设备上更新 <strong><i>的配置：推送配置</i></strong></p> <p>或者，</p> <p>在设备上更新 <strong><i>的配置：重新启动</i></strong></p> </td>
  </tr>
 </tbody>
</table>

### 已指定显示 {#assigned-displays}

“已指定显示”面板显示了与渠道关联的显示屏。该面板提供了分配的显示屏的快照以及分辨率。

关联的显示屏将列在&#x200B;**已指定显示**&#x200B;面板中，如下所示：

![chlimage_1-27](assets/chlimage_1-27.png)

>[!NOTE]
>
>要了解如何在位置创建显示屏，请参阅：
>
>* [创建和管理位置](managing-locations.md)
>* [创建和管理显示屏](managing-displays.md)
>



此外，单击&#x200B;**已指定显示**&#x200B;面板中的显示屏可查看显示屏信息，如下所示：

![chlimage_1-28](assets/chlimage_1-28.png)

### 后续步骤 {#the-next-steps}

创建渠道并在渠道中添加/编辑内容后，下一步是了解如何创建位置和显示屏。此外，还需将渠道分配到该显示屏。

有关后续步骤，请参阅以下资源：

* [创建和管理渠道](managing-channels.md)
* [创建和管理位置](managing-locations.md)
* [创建和管理显示屏](managing-displays.md)
