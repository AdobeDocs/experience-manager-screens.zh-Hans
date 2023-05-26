---
title: 创建和管理渠道
seo-title: Managing Channels
description: 请按照本页面了解如何创建和管理渠道。 它还介绍了渠道功能板和渠道的编辑内容。
seo-description: Follow this page to learn about creating and managing channels. It also explains channel dashboard and editing content for a channel.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 7bbd211a-f54f-42b9-a1b3-516efe6fb579
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1303'
ht-degree: 3%

---

# 创建和管理渠道 {#creating-and-managing-channels}

渠道可显示一系列内容（图像和视频），还可显示网站或单页应用程序。

本页显示如何为AEM Screens创建和管理渠道。

**先决条件**：

* [配置和部署Screens](configuring-screens-introduction.md)
* [创建和管理屏幕项目](creating-a-screens-project.md)

## 创建新渠道 {#creating-a-new-channel}

为AEM Screens创建项目后，请按照以下步骤为您的项目创建新渠道：

1. 选择Adobe Experience Manager链接（左上方），然后选择Screens。 或者，您可以直接导航到 `https://localhost:4502/screens.html/content/screens`.

1. 导航到屏幕项目并选择 **渠道** 文件夹。

1. 单击 **创建** 操作栏中的。

   ![demochannel](assets/create-channel1.png)

1. 选择 **序列渠道** 模板来自 **创建** 向导并单击 **下一个**.

   ![demochannel](assets/create-channel2.png)

1. 输入标题为 **ScreensChannel** 并单击 **创建**.

   ![demochannel](assets/create-project4.png)

1. 序列渠道现已添加到您的 **渠道** 文件夹。

### 渠道类型 {#channel-types}

在使用向导时，可以使用以下模板选项，例如：

| **模板选项** | **描述** |
|---|---|
| 渠道文件夹 | 允许创建用于存储渠道集合的文件夹。 |
| 序列渠道 | 允许创建一个按顺序播放组件的渠道（在幻灯片中逐一播放）。 |
| 应用程序渠道 | 允许在Screens播放器中显示您的自定义Web应用程序。 |
| 1x1 分屏渠道 | 允许在单个区域中查看组件。 |
| 1x2 分屏渠道 | 允许查看两个区域（水平拆分）中的资产。 |
| 2X1分屏渠道 | 允许查看两个区域（垂直拆分）中的资产。 |
| 2x2 分屏渠道 | 允许查看四个区域中的资产（在矩阵中水平拆分和垂直拆分）。 |
| 2x3 分屏渠道 | 允许查看两个区域（水平拆分）中的资产，其中一个区域大于另一个区域。 |
| 左或右L栏分屏渠道 | 允许内容作者在大小合适的区域中查看不同类型的资产。 |

>[!NOTE]
>
>分屏渠道将显示分成多个区域，以便您可以并排同时播放多个体验。 体验可以是静态资源/文本或嵌入序列。

>[!IMPORTANT]
>
> 创建内容并将其添加到渠道后，下一步是创建一个位置，然后创建一个显示。 此外，您需要将该渠道分配给显示。 有关更多信息，请参阅本节末尾的以下资源。

## 使用渠道 {#working-with-channels}

您可以编辑、查看属性和功能板，复制、预览和删除渠道。


![screen_shot_2019-07-24at103723am](assets/screen_shot_2019-07-24at103723am.png)

### 向渠道添加/编辑内容 {#adding-editing-content-to-a-channel}

要在渠道中添加或编辑内容，请执行以下步骤：

1. 选择要编辑的频道（如上图所示）。
1. 单击 **编辑** 从操作栏的左上角编辑渠道属性。 编辑器将打开，允许您向要发布的渠道添加资产/组件。

>[!NOTE]
>您可以将组件添加到渠道。 请参阅 **[将组件添加到渠道](adding-components-to-a-channel.md)** 了解更多详细信息。

![demochannel1](assets/demochannel1.gif)

**正在将视频上传到渠道**

请按照以下步骤将视频上传到您的频道：

1. 选择要上传视频的频道。
1. 单击 **编辑** 以打开编辑器。
1. 选择 **视频** 在“资产”下，拖放所需的视频。

>[!NOTE]
>如果您在渠道中上传视频时遇到问题，请参阅 [视频疑难解答](troubleshoot-videos.md).

### 查看属性 {#viewing-properties}

要查看或编辑渠道的属性，请执行以下步骤：

1. 单击要编辑的渠道。
1. 单击 **属性** 以查看/编辑渠道属性。 以下选项卡允许您更改选项。

![属性](assets/properties.gif)

### 查看功能板 {#viewing-dashboard}

要查看渠道的控制面板，请执行以下步骤：

1. 选择要编辑的渠道。
1. 单击 **仪表板** 操作栏中查看功能板。 此 **渠道信息**，**已分配显示区**、和 **待处理启动项** 面板打开，如下图所示：

![仪表板](assets/dashboard.gif)

### 渠道信息 {#channel-information}

“渠道信息”面板描述了渠道属性，以及渠道预览。 此外，它还为您提供有关渠道是离线还是在线的信息。

单击(**...**)中的 **渠道信息** 操作栏，用于查看属性、编辑内容或更新渠道的缓存（离线内容）。

![screen_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

#### 查看清单 {#view-manifest}

您可以从渠道仪表板查看清单。

>[!IMPORTANT]
>此选项仅在AEM 6.4 Feature Pack 8或AEM 6.5 Feature Pack 4中可用。

按照以下步骤从渠道功能板中启用此选项：

1. **将渠道设置为脱机**
   1. 选择渠道并选择 **属性** 操作栏中的
   1. 导航到 **渠道** 按Tab键并确保取消选中 **开发人员模式（强制渠道联机）** option
   1. 单击 **保存并关闭**
1. **更新脱机内容**
   1. 选择渠道并选择 **仪表板** 操作栏中的
   1. 导航到 **渠道信息** 面板并单击 *...*
   1. 单击 **更新离线内容**

您应会看到 **查看清单** 选项来自 **渠道信息** 面板中。

![image1](assets/channel-one.png)


### 在线和离线渠道 {#online-and-offline-channels}

>[!NOTE]
>默认情况下，创建渠道时，该渠道为“脱机”。

创建渠道时，可以将其定义为在线或离线渠道。

An ***在线渠道***，将在实时环境中显示更新的内容，而 ***脱机渠道***，显示缓存的内容。

请按照以下步骤使渠道联机：

1. 导航到渠道为 **测试项目** —> **渠道** —> **TestChannel**.

   选择渠道。

   ![screen_shot_2019-08-01at31406pm](assets/screen_shot_2019-08-01at31406pm.png)

   单击 **仪表板** 查看播放器的状态。 此 **渠道信息** 面板提供有关渠道是在线还是离线的信息。

   ![screen_shot_2019-08-01at31458pm](assets/screen_shot_2019-08-01at31458pm.png)

1. 单击 **属性** 操作，然后导航到 **渠道** 选项卡，如下所示：

   ![screen_shot_2019-08-01at31542pm](assets/screen_shot_2019-08-01at31542pm.png)

1. 查看 **开发人员** **模式（强制渠道联机）** 使渠道联机。

   单击 **保存并关闭** 以保存您的选项。

   ![screen_shot_2019-08-01at31658pm](assets/screen_shot_2019-08-01at31658pm.png)

   导航回渠道功能板，现在转到 **渠道信息** 面板显示播放器的联机状态。

   ![screen_shot_2019-08-01at31821pm](assets/screen_shot_2019-08-01at31821pm.png)

>[!NOTE]
>如果要再次将渠道配置为脱机，请从取消选中开发人员模式选项 **属性** 选项卡(如步骤(3)中所示)，然后从 **渠道信息** 面板点击 **更新离线内容**，如下图所示。

![dashboard2](assets/dashboard2.gif)

#### 从设备仪表板进行自动更新与手动更新 {#automatic-versus-manual-updates-from-the-device-dashboard}

下表总结了与设备仪表板中的自动和手动更新关联的事件。

<table>
 <tbody>
  <tr>
   <td><strong>Event</strong></td>
   <td><strong>设备自动更新</strong></td>
   <td><strong>设备手动更新</strong></td>
  </tr>
  <tr>
   <td>在线渠道中的更改</td>
   <td>内容已自动更新</td>
   <td><p>在“设备：推送配置”上更新了内容</p> <p>或者,</p> <p>内容更新日期 <strong><i>设备：重新启动</i></strong></p> </td>
  </tr>
  <tr>
   <td>脱机渠道中的更改，但未触发渠道“推送内容”（不重新创建脱机包）</td>
   <td>无内容更新</td>
   <td>无内容更新</td>
  </tr>
  <tr>
   <td>离线渠道和渠道“推送内容”中的更改已触发（新的离线包）</td>
   <td>内容已自动更新</td>
   <td><p>内容更新日期 <strong><i>设备：推送配置</i></strong></p> <p>或者,</p> <p>内容更新日期 <strong><i>设备：重新启动</i></strong></p> </td>
  </tr>
  <tr>
   <td><p>配置中的更改</p>
    <ul>
     <li>显示（强制渠道）</li>
     <li>设备</li>
     <li>渠道分配（新渠道、已删除的渠道）</li>
     <li>渠道分配（角色、事件、计划）</li>
    </ul> </td>
   <td>自动更新配置</td>
   <td><p>配置更新日期 <strong><i>设备：推送配置</i></strong></p> <p>或者,</p> <p>配置更新日期 <strong><i>设备：重新启动</i></strong></p> </td>
  </tr>
 </tbody>
</table>

### 已指定显示 {#assigned-displays}

分配的显示面板显示与渠道关联的显示。 它提供已分配显示的快照以及分辨率。

关联的显示将在 **已分配的显示区** 面板，如下所示：

![chlimage_1-27](assets/chlimage_1-27.png)

>[!NOTE]
>要了解如何在位置中创建显示，请参阅：
>
>* [创建和管理位置](managing-locations.md)
>* [创建和管理显示区](managing-displays.md)
>


此外，单击 **已分配显示区** 面板，查看显示信息，如下所示：

![chlimage_1-28](assets/chlimage_1-28.png)

### 后续步骤 {#the-next-steps}

创建渠道并在渠道中添加/编辑内容后的下一个步骤是了解如何创建位置和显示。 此外，还可以为该显示分配一个渠道。

有关后续步骤，请参阅以下资源：

* [创建和管理渠道](managing-channels.md)
* [创建和管理位置](managing-locations.md)
* [创建和管理显示区](managing-displays.md)
