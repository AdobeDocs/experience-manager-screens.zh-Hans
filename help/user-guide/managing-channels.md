---
title: 创建和管理渠道
seo-title: 管理渠道
description: 可查看本页以了解有关创建和管理渠道的信息。本页还介绍了渠道功能板，以及如何编辑渠道的内容。
seo-description: 可查看本页以了解有关创建和管理渠道的信息。本页还介绍了渠道功能板，以及如何编辑渠道的内容。
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1331'
ht-degree: 42%

---


# 创建和管理渠道 {#creating-and-managing-channels}

渠道显示一系列内容（图像和视频），还显示网站或单页应用程序。

本页显示了如何为AEM Screens创建和管理渠道。

**先决条件**：

* [配置和部署 Screens](configuring-screens-introduction.md)
* [创建和管理Screens项目](creating-a-screens-project.md)

## 创建新渠道 {#creating-a-new-channel}

为AEM Screens创建项目后，请按照以下步骤为项目创建新渠道:

1. 选择 Adobe Experience Manager 链接（左上方），然后选择“屏幕”。或者，您也可以直接导航到`https://localhost:4502/screens.html/content/screens`。

1. 导航到您的Screens项目并选择&#x200B;**渠道**&#x200B;文件夹。

1. 单击操作栏中的&#x200B;**创建**。

   ![demochannel](assets/create-channel1.png)

1. 从&#x200B;**创建**&#x200B;向导中选择&#x200B;**序列渠道**&#x200B;模板，然后单击&#x200B;**下一步**。

   ![demochannel](assets/create-channel2.png)

1. 在标题中输入&#x200B;**ScreensChannel**，然后单击&#x200B;**创建**。

   ![demochannel](assets/create-project4.png)

1. 现在，序列渠道已添加到您的&#x200B;**渠道**&#x200B;文件夹。

### 渠道类型 {#channel-types}

可以在向导中使用以下模板选项，例如：

| **模板选项** | **描述** |
|---|---|
| 渠道文件夹 | 允许创建一个文件夹来存储渠道的集合。 |
| 序列渠道 | 允许创建按顺序（在幻灯片中逐个播放）播放组件的渠道。 |
| 应用程序渠道 | 允许在 Screens 播放器中显示您的自定义 Web 应用程序。 |
| 1x1 分屏渠道 | 允许在单个区域中视图组件。 |
| 1x2 分屏渠道 | 允许视图两个区域中的资产（水平拆分）。 |
| 2X1分屏渠道 | 允许视图两个区域中的资产（垂直拆分）。 |
| 2x2 分屏渠道 | 允许视图四个区域中的资产（在矩阵中水平和垂直拆分）。 |
| 2x3 分屏渠道 | 允许视图两个区域中的资产（水平拆分），其中一个区域大于另一个区域。 |
| 左或右L栏拆分屏幕渠道 | 允许内容作者视图大小合适的区域中不同类型的资源。 |

>[!NOTE]
>
>“拆分屏幕”渠道将显示屏拆分为多个区域，因此您可以同时并排播放多个体验。 体验可以是静态资产/文本或嵌入式序列。

>[!IMPORTANT]
>
> 在创建渠道并向渠道中添加内容后，下一步是创建位置，之后是创建显示屏。此外，您还需要将该渠道分配到显示屏。请参阅此部分末尾的资源以了解更多信息。

## 使用渠道  {#working-with-channels}

您可以编辑、复制、预览和删除渠道，以及查看渠道属性和功能板。


![screen_shot_2019-07-24at103723am](assets/screen_shot_2019-07-24at103723am.png)

### 在渠道中添加/编辑内容 {#adding-editing-content-to-a-channel}

要在渠道中添加或编辑内容，请按照以下步骤操作：

1. 选择要编辑的渠道（如上图所示）。
1. 单击操作栏左上角的&#x200B;**编辑**&#x200B;以编辑渠道属性。 此时会打开编辑器，您可以在其中将资产/组件添加到要发布的渠道。

>[!NOTE]
>您可以向渠道添加组件。 有关详细信息，请参阅&#x200B;**[将组件添加到渠道](adding-components-to-a-channel.md)**。

![demochannel1](assets/demochannel1.gif)

**将视频上传到渠道**

请按照以下步骤将视频上传到渠道：

1. 选择要上传视频的渠道。
1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。
1. 在“资产”下选择&#x200B;**视频**，然后拖放所需的视频。

>[!NOTE]
>如果您在将视频上传到渠道时遇到问题，请参阅[视频疑难解答](troubleshoot-videos.md)。

### 查看属性 {#viewing-properties}

要查看或编辑渠道的属性，请按照以下步骤操作：

1. 单击要编辑的渠道。
1. 单击操作栏中的&#x200B;**属性**&#x200B;以视图/编辑渠道属性。 您可以在以下选项卡中更改选项。

![属性](assets/properties.gif)

### 查看功能板 {#viewing-dashboard}

要查看渠道的功能板，请按照以下步骤操作：

1. 选择要编辑的渠道。
1. 单击操作栏中的&#x200B;**仪表板**&#x200B;以视图仪表板。 将打开&#x200B;**渠道信息**、**已分配显示**&#x200B;和&#x200B;**待定启动项**&#x200B;面板，如下图所示：

![仪表板](assets/dashboard.gif)

### 渠道信息 {#channel-information}

“渠道信息”面板描述渠道属性以及渠道的预览。 此外，该面板还提供了有关渠道是处于脱机还是联机状态的信息。

单击(**...**)中的“渠道信息”**操作栏中的“视图”属性、编辑内容或更新渠道的缓存（脱机内容）。**

![screen_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

#### 查看清单{#view-manifest}

您可以从渠道仪表板视图清单。

>[!IMPORTANT]
>此选项仅在AEM 6.4 Feature Pack 8或AEM 6.5 Feature Pack 4中可用。

请按照以下步骤从“渠道”仪表板启用此选项：

1. **将渠道设置为脱机**
   1. 选择渠道，然后从操作栏中选择&#x200B;**属性**
   1. 导航到&#x200B;**渠道**&#x200B;选项卡，并确保取消选中&#x200B;**开发者模式(强制渠道联机)**&#x200B;选项
   1. 单击&#x200B;**保存并关闭**
1. **更新脱机内容**
   1. 选择渠道，然后从操作栏中选择&#x200B;**仪表板**
   1. 导航到&#x200B;**渠道信息**&#x200B;面板，然后单击&#x200B;*...*
   1. 单击&#x200B;**更新脱机内容**

您应当在渠道仪表板的&#x200B;**视图信息**&#x200B;面板中看到&#x200B;**渠道清单**&#x200B;选项。

![image1](assets/channel-one.png)


### 联机和脱机渠道 {#online-and-offline-channels}

>[!NOTE]
>默认情况下，创建渠道时，它为“脱机”。

创建渠道时，可以将其定义为联机渠道或脱机渠道。

“联机渠道”******&#x200B;将会在实时环境中显示更新的内容，而“脱机渠道”******&#x200B;则会显示缓存的内容。

请按照以下步骤使渠道处于联机状态：

1. 导航到渠道（**TestProject** --> **渠道** --> **TestChannel**）。

   选择渠道。

   ![screen_shot_2019-08-01at31406pm](assets/screen_shot_2019-08-01at31406pm.png)

   单击操作栏中的&#x200B;**仪表板**&#x200B;以视图播放器的状态。 **渠道信息**&#x200B;面板提供了有关渠道是处于联机还是脱机状态的信息。

   ![screen_shot_2019-08-01at31458pm](assets/screen_shot_2019-08-01at31458pm.png)

1. 单击操作栏中的&#x200B;**属性**，然后导航到&#x200B;**渠道**&#x200B;选项卡，如下所示：

   ![screen_shot_2019-08-01at31542pm](assets/screen_shot_2019-08-01at31542pm.png)

1. 检查&#x200B;**开发人员** **模式(强制渠道联机)**&#x200B;以使渠道联机。

   单击&#x200B;**保存并关闭**&#x200B;以保存您的选项。

   ![screen_shot_2019-08-01at31658pm](assets/screen_shot_2019-08-01at31658pm.png)

   导航回渠道仪表板，现在&#x200B;**渠道信息**&#x200B;面板显示播放器的联机状态。

   ![screen_shot_2019-08-01at31821pm](assets/screen_shot_2019-08-01at31821pm.png)

>[!NOTE]
>如果要再次将渠道配置为脱机，请从&#x200B;**属性**&#x200B;选项卡(如步骤(3)所示)中取消选中“开发者模式”选项，然后从&#x200B;**渠道信息**&#x200B;面板单击&#x200B;**更新脱机内容**，如下图所示。

![仪表板2](assets/dashboard2.gif)

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
   <td>在线渠道更改</td>
   <td>内容自动更新</td>
   <td><p>内容已在“设备：推送配置”</p> <p>或者，</p> <p>在<strong><i>设备上更新的内容：重新启动</i></strong></p> </td>
  </tr>
  <tr>
   <td>脱机渠道中的更改，但渠道“推送内容”未触发（无脱机包重新创建）</td>
   <td>无内容更新</td>
   <td>无内容更新</td>
  </tr>
  <tr>
   <td>脱机渠道更改和渠道“推送内容”被触发（新的脱机包）</td>
   <td>内容自动更新</td>
   <td><p>在<strong><i>设备上更新的内容：推送配置</i></strong></p> <p>或者，</p> <p>在<strong><i>设备上更新的内容：重新启动</i></strong></p> </td>
  </tr>
  <tr>
   <td><p>配置更改</p>
    <ul>
     <li>显示(强制渠道)</li>
     <li>设备</li>
     <li>渠道分配(新渠道，已删除渠道)</li>
     <li>渠道分配(角色、事件、计划)</li>
    </ul> </td>
   <td>配置已自动更新</td>
   <td><p>在<strong><i>设备上更新了配置：推送配置</i></strong></p> <p>或者，</p> <p>在<strong><i>设备上更新了配置：重新启动</i></strong></p> </td>
  </tr>
 </tbody>
</table>

### 已指定显示 {#assigned-displays}

“已指定显示”面板显示了与渠道关联的显示屏。该面板提供了分配的显示屏的快照以及分辨率。

关联的显示屏将列在&#x200B;**已指定显示**&#x200B;面板中，如下所示：

![chlimage_1-27](assets/chlimage_1-27.png)

>[!NOTE]
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

