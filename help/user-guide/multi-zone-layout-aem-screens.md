---
title: 多区域布局
seo-title: 多区域布局
description: 多区域布局允许您创建多个区域内容并使用各种资产，如可组合到单个屏幕中的视频、图像和文本。 可查看本页以了解更多信息。
seo-description: 多区域布局允许您创建多个区域内容并使用各种资产，如可组合到单个屏幕中的视频、图像和文本。 可查看本页以了解更多信息。
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
translation-type: tm+mt
source-git-commit: 2e590d7a73dea9a0445962c2f65cdfa7fef3994d
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 4%

---


# 多区域布局 {#multi-zone-layout}

以下页介绍了多区域布局的用法，并涵盖以下主题：

* 概述
* 创建多区域布局
* 前提条件
* 在一个或多个区域中使用单个资产
* 在一个或多个区域中使用排序的内容

## 概述 {#overview}

***多区域布局*** 允许您创建多个区域内容并使用各种资源，如可组合到单个屏幕中的视频、图像和文本。 您可以拖入图像、视频和文本，使其全部融合在一起，创建直观的数字体验。

根据项目要求，有时您需要在渠道中使用多个区域并将其作为一个完整的单位进行编辑。例如，具有相关社交媒体源的产品序列在单个渠道的三个单独区域中运行。


### 前提条件 {#prerequisites}

在开始实施此功能之前，请确保您对以下方面的概念性知识：

* [创建AEM Screens项目](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [创建显示屏](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [将渠道分配给显示屏](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## 创建多区域布局 {#creating-multi-zone-layout}

创建渠道时，您可以使用不同的模板在渠道中创建区域。 您可以添加单个图像、视频或嵌入式渠道，该允许在序列中显示多个资产。

**创建渠道**

1. 选择 Adobe Experience Manager 链接（左上方），然后选择&#x200B;**屏幕**。Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.
1. 导航到 **渠道** 文件夹，然 **后单** 击操作栏中的创建。

1. 从 **创建向导中选择** 1x2分 **屏渠道** 。

1. 单 **击** “下一步 **”，然后输** 入Multi **Zone**&#x200B;标题。

1. 单击 **创建** ，以完成渠道创建。

### 在一个或多个区域中使用单个资产 {#using-single-assets-in-one-or-more-zones}

您可以在所有三个不同区域中使用单个资产，如图像或视频。 请按照以下步骤实施：

1. **向渠道添加内容**

   1. 导航到 **Zones** —> **渠道**— **>** MultiZone。
   1. Select the **MultiZone** channel and click **Edit** from the action bar to open the editor.

1. **向渠道添加图像**

   要在两个区域中播放单个图像或视频，只需在渠道编辑器中将图像拖放到每个区域，如下图所示：

   ![图像](/help/user-guide/assets/multi-zone/multizone-img3.png)

### 在一个或多个区域中使用排序的内容 {#using-sequenced-content-in-one-or-more-zones}

如果希望区域在两个不同区域中显示图像和视频的序列，请按照以下步骤了解详细信息。

1. **创建渠道文件夹**

   1. 导航到 **Zones** —> **MultiZone** —> **渠道，然** 后单击 **** 操作栏中的创建。
   1. Select **Channels Folder** from the **Create** wizard and click **Next**.
   1. Enter the title as **EmbeddedChannels** and click **Create**.
   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **将两个渠道添加到渠道文件夹**

   1. 导航到 **Zones** —> **渠道****—>** EmbeddedChannels **，然** 后单击操作栏中的创建。
   1. 从创 **建向导** 中选 **择序列渠道** ，以创建标题为 **Zone1的渠道**。
   1. Select **Zone1** and click **Edit** from the action bar to open the editor.
   1. 将很少的图像拖放到此渠道。
   1. 同样，在EmbeddedChannels文件夹中创建另一个标 **题为** Zone2 **的序列** 渠道。
   1. 将视频拖放到此渠道。
   下图显示了渠道 **Zone1** 和 **Zone2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   添加到Zone1序列渠道 **编辑器** 的图像如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   添加到Zone2序列渠道 **编辑器** 的视频如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **将嵌入式序列（组件）添加到主渠道(MultiZone)**

   1. 导航到 **Zones** —> **渠道** — **>** MultiZone。
   1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。
   1. 将嵌入式序 **列组件拖放** 到这两个区域。
   1. 选择其中一个区域中的嵌入式序列。
   1. 单击编 **辑器** 中某个嵌入式序列的“配置（扳手）”图标。
   1. 选择渠道路径 **作为** Zones **—>** BemdeddedChannels **—** Zone1渠道，如 ****&#x200B;下图所示。
   1. 同样，将Zone2添 **加到** 编辑器中的另一个嵌入式序列组件。

      ![图像](/help/user-guide/assets/multi-zone/multizone-3.png)

### 创建位置和显示屏 {#creating-location}

您必须创建一个位置和显示屏来视图Screens播放器中的内容。 按照以下步骤创建位置和显示屏。

1. **创建位置**

   1. 导航到 **Zones** —> **位置** 文件夹。
   1. 选择位 **置文** 件夹，然后 **单击操** 作栏中的“创建”。
   1. Select **Location** from the **Create** wizard and click **Next**.
   1. Enter the **Title** as **SanJose** and click **Create**.

1. **创建显示屏**

   1. 导航到 **Zones** —> **位置** 文件夹。
   1. 选择SanJose **位置** ，然后 **单击操** 作栏中的“创建”。
   1. Select **Display** from the **Create** wizard and click **Next**.
   1. Enter the **Title** as **Lobby** and click **Create**.

### 将渠道分配给显示屏 {#channel-channel}

您必须为显示屏分配渠道，才能视图内容。 请按照以下步骤将渠道分配给显示屏。

1. **将渠道分配给显示屏**

   1. 导航到 **Zones** —>位 **置** —> **SanJose**— ****>大堂。
   1. 选择“ **休息室** ”显示屏，然 **后单击操** 作栏中的“分配渠道”。
   1. 在“渠道路径” **中输入** MultiZone **渠道的路径**。
   1. 将支持 **的事件设** 置为 **初始负**&#x200B;载、Idle Screen **和** Timer **Dimer**。
   1. 单击&#x200B;**保存**。

      ![图像](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. 同样，您必须将其他两个嵌入渠道(**Zone1****和Zone2**)分配给此显示屏。
   1. 将所有三个渠道分配给“休 **息室** ”显示屏后，您应该能够从显示仪表板视图分配的渠道。

      ![图像](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!I重要]
      > 一旦将主渠道(本例中为 **MultiZone**)分配给显示屏，则必须将另外两个嵌入的渠道Zone **1和****** Zone2也分配给同一显示屏。

### 注册设备 {#registering-device}

设置位置和显示屏后，请按照以下步骤注册设备并为设备分配显示屏。

1. **注册设备**

   1. 导航到 **Zones** —>设 **备文** 件夹。
   1. Select the **Devices** folder and click **Device Manager** from the action bar.
   1. 单击 **“设备注册** ”，然后从列表中选择待定设备。
      >[!NOTE]
      > 设备的标题必须与设备注册选项卡中显&#x200B;**示的设备** 令牌(令牌 **字段)匹配** 。
   1. 如果标题与设备令牌匹配，则选择设备，然后单 **击操作栏** 中的注册设备。
   1. 如果注册代码与Screens播放器的“设备注册”选 **项卡中的代码** 相匹配，请 **单击操作** 栏中的“验证”。
      ![图像](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Enter the **Title** as **Chrome-Device1** and click **Register**.
   1. 选 **择指定显** 示，然后选择设备配置的路径。
   >[!NOTE]
   >如果尝试视图Screens播放器中的内容，请确保单击“更 **新脱机内容** ”渠道仪表板。

#### 查看结果 {#viewing-the-result}

使用上述步骤实施多区域布局后，将显示以下输出。

选中Screens播放器以视图显示两个不同区域中的内容的输出。 左侧和右侧区域（两者都使用嵌入式序列作为组件）。

左侧区域是序列渠道，右侧区域包括视频。

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)


