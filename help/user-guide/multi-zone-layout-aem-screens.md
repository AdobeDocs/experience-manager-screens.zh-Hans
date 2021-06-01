---
title: 多区域布局
seo-title: 多区域布局
description: 多区域布局允许您创建多个区域内容，并使用可组合到单个屏幕中的各种资产，例如视频、图像和文本。 请阅读本页以了解更多信息。
seo-description: 多区域布局允许您创建多个区域内容，并使用可组合到单个屏幕中的各种资产，例如视频、图像和文本。 请阅读本页以了解更多信息。
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: 创作屏幕
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 6%

---


# 多区域布局{#multi-zone-layout}

以下页面介绍了多区域布局的用法，并涵盖以下主题：

* 概述
* 创建多区域布局
* 前提条件
* 在一个或多个区域中使用单个资产
* 在一个或多个区域中使用已排序的内容

## 概述 {#overview}

***多区域布局*** 允许您创建多个区域内容，并使用各种资产，如可在单个屏幕中组合的视频、图像和文本。您可以提取图像、视频和文本，以便将所有内容混合在一起，并创建直观的数字体验。

根据项目要求，有时您需要在渠道中使用多个区域并将其作为一个完整的单位进行编辑。例如，某个产品序列具有相关社交媒体信息源，该信息源在单个渠道的三个不同区域中运行。


### 前提条件 {#prerequisites}

在开始实施此功能之前，请确保您对以下内容具有概念性知识：

* [创建AEM Screens项目](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [创建显示屏](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [将渠道分配给显示器](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## 创建多区域布局{#creating-multi-zone-layout}

在创建渠道时，您可以使用不同的模板在渠道中创建区域。 您可以添加单个图像、视频或嵌入式渠道，以便按序列显示多个资产。

**创建渠道**

1. 选择 Adobe Experience Manager 链接（左上方），然后选择&#x200B;**屏幕**。或者，您也可以直接转到：`http://localhost:4502/screens.html/content/screens`。
1. 导航到&#x200B;**Channels**&#x200B;文件夹，然后单击操作栏中的&#x200B;**创建**。

1. 从&#x200B;**创建**&#x200B;向导中选择&#x200B;**1x2分屏渠道**。

1. 单击&#x200B;**Next**&#x200B;并输入&#x200B;**title**&#x200B;作为&#x200B;**MultiZone**。

1. 单击&#x200B;**创建**&#x200B;以完成渠道创建。

### 在一个或多个区域中使用单个资产{#using-single-assets-in-one-or-more-zones}

您可以在所有单独的区域中使用单个资产，如图像或视频。 请按照以下步骤进行实施：

1. **向渠道添加内容**

   1. 导航到&#x200B;**Zones** —> **渠道**—> **MultiZone**。
   1. 选择&#x200B;**MultiZone**&#x200B;渠道，然后单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。

1. **向渠道添加图像**

   要在两个区域中播放单个图像或视频，只需在渠道编辑器中将图像拖放到每个区域中即可，如下图所示：

   ![图像](/help/user-guide/assets/multi-zone/multizone-img3.png)

### 在一个或多个区域{#using-sequenced-content-in-one-or-more-zones}中使用已排序的内容

如果希望各个区域在不同区域中显示图像和视频的序列，请按照以下步骤了解详细信息。

1. **创建渠道文件夹**

   1. 导航到&#x200B;**Zones** —> **MultiZone** —> **渠道** ，然后单击操作栏中的&#x200B;**创建**。
   1. 从&#x200B;**创建**&#x200B;向导中选择&#x200B;**通道文件夹**，然后单击&#x200B;**下一步**。
   1. 输入&#x200B;**EmbeddedChannels**&#x200B;标题，然后单击&#x200B;**创建**。

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **向渠道文件夹添加两个渠道**

   1. 导航到&#x200B;**Zones** —> **渠道** —> **EmbeddedChannels** ，然后单击操作栏中的&#x200B;**创建**。
   1. 从&#x200B;**创建**&#x200B;向导中选择&#x200B;**序列渠道**&#x200B;以创建标题为&#x200B;**Zone1**&#x200B;的渠道。
   1. 选择&#x200B;**Zone1**&#x200B;并单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。
   1. 将一些图像拖放到此渠道中。
   1. 同样，在&#x200B;**EmbeddedChannels**&#x200B;文件夹中创建另一个名为&#x200B;**Zone2**&#x200B;的序列渠道。
   1. 将视频拖放到此渠道。

   下图显示了通道&#x200B;**Zone1**&#x200B;和&#x200B;**Zone2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   添加到&#x200B;**Zone1**&#x200B;序列渠道编辑器的图像如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   添加到&#x200B;**Zone2**&#x200B;序列渠道编辑器的视频如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **将嵌入式序列（组件）添加到主渠道（多区域）**

   1. 导航到&#x200B;**Zones** —> **渠道** —> **MultiZone**。
   1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。
   1. 将&#x200B;**嵌入式序列**&#x200B;组件拖放到这两个区域。
   1. 在其中一个区域中选择嵌入式序列。
   1. 在编辑器中，单击&#x200B;**配置**（扳手）图标以查看其中一个嵌入式序列。
   1. 选择通道路径作为&#x200B;**Zones** —> **通道** —> **EmbeddedChannels** —> **Zone1**，如下图所示。
   1. 同样，将&#x200B;**Zone2**&#x200B;添加到编辑器中的其他嵌入式序列组件。

      ![图像](/help/user-guide/assets/multi-zone/multizone-3.png)

### 创建位置和显示屏{#creating-location}

您必须创建一个位置和显示屏，才能在Screens播放器中查看内容。 请按照以下步骤创建位置和显示屏。

1. **创建位置**

   1. 导航到&#x200B;**Zones** —> **位置**&#x200B;文件夹。
   1. 选择&#x200B;**位置**&#x200B;文件夹，然后单击操作栏中的&#x200B;**创建**。
   1. 从&#x200B;**创建**&#x200B;向导中选择&#x200B;**位置**，然后单击&#x200B;**下一步**。
   1. 在&#x200B;**标题**&#x200B;中输入&#x200B;**SanJose**，然后单击&#x200B;**创建**。

1. **创建显示屏**

   1. 导航到&#x200B;**Zones** —> **位置**&#x200B;文件夹。
   1. 选择&#x200B;**SanJose**&#x200B;位置，然后单击操作栏中的&#x200B;**创建**。
   1. 从&#x200B;**创建**&#x200B;向导中选择&#x200B;**显示**，然后单击&#x200B;**下一步**。
   1. 在&#x200B;**标题**&#x200B;中输入&#x200B;**Lobby**，然后单击&#x200B;**创建**。

### 将渠道分配给显示器{#channel-channel}

您必须将渠道分配给显示屏才能查看内容。 请按照以下步骤将渠道分配给显示屏。

1. **将渠道分配给显示屏**

   1. 导航到&#x200B;**Zones** —> **位置** —> **SanJose**—> **Lobby**。
   1. 选择&#x200B;**Lobby**&#x200B;显示屏，然后单击操作栏中的&#x200B;**Assign Channel**。
   1. 在&#x200B;**渠道路径**&#x200B;中输入&#x200B;**MultiZone**&#x200B;渠道的路径。
   1. 将&#x200B;**支持的事件**&#x200B;设置为&#x200B;**初始加载**、**空闲屏幕**&#x200B;和&#x200B;**计时器**。
   1. 单击&#x200B;**保存**。

      ![图像](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. 同样，您必须将其他两个嵌入的通道（**Zone1**&#x200B;和&#x200B;**Zone2**）分配给此显示屏。
   1. 将所有三个渠道分配给&#x200B;**Lobby**&#x200B;显示屏后，您应该能够从显示仪表板查看分配的渠道。

      ![图像](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > 在将主通道（在本例中为&#x200B;**MultiZone**）分配给显示屏后，必须将其他两个嵌入的通道&#x200B;**Zone1**&#x200B;和&#x200B;**Zone2**&#x200B;也分配给同一显示屏。

### 注册设备{#registering-device}

设置位置和显示屏后，请按照以下步骤注册设备并将显示屏分配给设备。

1. **注册设备**

   1. 导航到&#x200B;**Zones** —> **Devices**&#x200B;文件夹。
   1. 选择&#x200B;**Devices**&#x200B;文件夹，然后单击操作栏中的&#x200B;**Device Manager**。
   1. 单击&#x200B;**设备注册**，然后从列表中选择待定设备。

      >[!NOTE]
      > 设备的标题必须与&#x200B;**设备注册**&#x200B;选项卡中显示的设备令牌（**令牌**&#x200B;字段）匹配。
   1. 如果标题与设备令牌匹配，请选择设备，然后单击操作栏中的&#x200B;**注册设备** 。
   1. 如果注册代码与Screens播放器&#x200B;**设备注册**&#x200B;选项卡中的代码匹配，请单击操作栏中的&#x200B;**验证** 。
      ![图像](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. 将&#x200B;**标题**&#x200B;输入为&#x200B;**Chrome-Device1**，然后单击&#x200B;**注册**。
   1. 选择&#x200B;**指定显示**&#x200B;并选择设备配置的路径。

   >[!NOTE]
   >如果您尝试在Screens播放器中查看内容，请确保单击渠道功能板中分配给显示屏的每个渠道的&#x200B;**更新离线内容** 。

### 查看结果{#viewing-the-result}

使用上述步骤实施多区域布局后，将显示以下输出。

选中Screens播放器可查看在两个不同区域中显示内容的输出。 左和右区域（都使用嵌入式序列作为组件）。

左区域是序列渠道，右区域包括视频。

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)


