---
title: 多区域布局
seo-title: Multi-zone Layout
description: 多区域布局允许您创建多个区域内容，并使用可组合到单个屏幕中的各种资产，例如视频、图像和文本。 请阅读本页以了解更多信息。
seo-description: Multi-zone Layout allows you to create multiple zone content and use a variety of assets such as videos, images and text that can be combined in a single screen. Follow this page to learn more.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 5%

---

# 多区域布局 {#multi-zone-layout}

以下页面介绍了多区域布局的用法，并涵盖以下主题：

* 概述
* 创建多区域布局
* 前提条件
* 在一个或多个区域中使用单个资产
* 在一个或多个区域中使用已排序的内容

## 概述 {#overview}

***多区域布局*** 允许您创建多个区域内容，并使用可组合到单个屏幕中的各种资产，如视频、图像和文本。 您可以提取图像、视频和文本，以便将所有内容混合在一起，并创建直观的数字体验。

根据项目要求，有时您需要在渠道中使用多个区域并将其作为一个完整的单位进行编辑。例如，具有相关社交媒体信息源的产品序列，该信息源在单个渠道的三个不同区域中运行。


### 前提条件 {#prerequisites}

在开始实施此功能之前，请确保您对以下内容具有概念性知识：

* [创建AEM Screens项目](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [创建显示屏](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [将渠道分配给显示器](/help/user-guide/channel-assignment.md)

## 创建多区域布局 {#creating-multi-zone-layout}

在创建渠道时，您可以使用不同的模板在渠道中创建区域。 您可以添加单个图像、视频或嵌入式渠道，以便按序列显示多个资产。

**创建渠道**

1. 选择 Adobe Experience Manager 链接（左上方），然后选择&#x200B;**屏幕**。或者，您也可以直接转到： `http://localhost:4502/screens.html/content/screens`.
1. 导航到 **渠道** 文件夹，单击 **创建** 中。

1. 选择 **1x2分屏渠道** 从 **创建** 向导。

1. 单击 **下一个** 然后输入 **标题** as **多区域**.

1. 单击 **创建** 以完成渠道创建。

### 在一个或多个区域中使用单个资产 {#using-single-assets-in-one-or-more-zones}

您可以在所有单独的区域中使用单个资产，如图像或视频。 请按照以下步骤进行实施：

1. **向渠道添加内容**

   1. 导航到 **区域** —> **渠道**—> **多区域**.
   1. 选择 **多区域** 渠道并单击 **编辑** 从操作栏中打开编辑器。

1. **向渠道添加图像**

   要在两个区域中播放单个图像或视频，只需在渠道编辑器中将图像拖放到每个区域即可，如下图所示：

   ![图像](/help/user-guide/assets/multi-zone/multizone-img3.png)

### 在一个或多个区域中使用已排序的内容 {#using-sequenced-content-in-one-or-more-zones}

如果希望各个区域在不同区域中显示图像和视频的序列，请按照以下步骤了解详细信息。

1. **创建渠道文件夹**

   1. 导航到 **区域** —> **多区域** —> **渠道** 单击 **创建** 中。
   1. 选择 **渠道文件夹** 从 **创建** 向导，单击 **下一个**.
   1. 在标题中输入 **嵌入式渠道** 单击 **创建**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **向渠道文件夹添加两个渠道**

   1. 导航到 **区域** —> **渠道** —> **嵌入式渠道** 单击 **创建** 中。
   1. 选择 **序列渠道** 从 **创建** 创建标题为 **区域1**.
   1. 选择 **区域1** 单击 **编辑** 从操作栏中打开编辑器。
   1. 将一些图像拖放到此渠道中。
   1. 同样，创建另一个名为的序列渠道 **Zone2** in **嵌入式渠道** 文件夹。
   1. 将视频拖放到此渠道。

   下图显示了渠道 **区域1** 和 **Zone2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   添加到的编辑器中的图像 **区域1** 序列渠道如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   视频已添加到的编辑器 **Zone2** 序列渠道如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **将嵌入式序列（组件）添加到主渠道（多区域）**

   1. 导航到 **区域** —> **渠道** —> **多区域**.
   1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。
   1. 拖放 **嵌入式序列** 组件。
   1. 在其中一个区域中选择嵌入式序列。
   1. 单击 **配置** （扳手）图标添加到编辑器中的某个嵌入式序列。
   1. 将渠道路径选择为 **区域** —> **渠道** —> **嵌入式渠道** —> **区域1**，如下图所示。
   1. 同样，在 **Zone2** 到编辑器中的其他嵌入式序列组件。

      ![图像](/help/user-guide/assets/multi-zone/multizone-3.png)

### 创建位置和显示屏 {#creating-location}

创建一个位置和显示屏，以在Screens播放器中查看内容。

1. **创建位置**

   1. 导航到 **区域** —> **位置** 文件夹。
   1. 选择 **位置** 文件夹，单击 **创建** 中。
   1. 选择 **位置** 从 **创建** 向导，单击 **下一个**.
   1. 输入 **标题** as **圣何塞** 单击 **创建**.

1. **创建显示屏**

   1. 导航到 **区域** —> **位置** 文件夹。
   1. 选择 **圣何塞** 位置，单击 **创建** 中。
   1. 选择 **显示** 从 **创建** 向导，单击 **下一个**.
   1. 输入 **标题** as **大堂** 单击 **创建**.

### 将渠道分配给显示屏 {#channel-channel}

将渠道分配给显示屏以查看内容。 请按照以下步骤将渠道分配给显示屏。

1. **将渠道分配给显示屏**

   1. 导航到 **区域** —> **位置** —> **圣何塞**—> **大堂**.
   1. 选择 **大堂** 显示和单击 **分配渠道** 中。
   1. 输入路径 **多区域** 渠道 **渠道路径**.
   1. 设置 **支持的事件** as **初始加载**, **空闲屏幕**&#x200B;和 **计时器**.
   1. 单击“**保存**”。

      ![图像](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. 同样，您必须分配其他两个嵌入的渠道(**区域1** 和 **Zone2**)显示。
   1. 将所有三个渠道分配给 **大堂** 显示时，您应该能够从显示功能板中查看分配的渠道。

      ![图像](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > 分配主渠道后(在本例中为 **多区域**)，则必须分配其他两个嵌入的渠道 **区域1** 和 **Zone2** 也显示到同一显示屏。

### 注册设备 {#registering-device}

设置位置和显示屏后，请按照以下步骤注册设备并将显示屏分配给设备。

1. **注册设备**

   1. 导航到 **区域** —> **设备** 文件夹。
   1. 选择 **设备** 文件夹，单击 **设备管理器** 中。
   1. 单击 **设备注册** 并从列表中选择待处理设备。

      >[!NOTE]
      > 设备的标题必须与设备令牌(**令牌** 字段) **设备注册** 选项卡。
   1. 如果标题与设备令牌匹配，请选择设备并单击 **注册设备** 中。
   1. 如果注册代码与Screens播放器中的代码匹配 **设备注册** ，单击 **验证** 中。
      ![图像](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. 输入 **标题** as **Chrome-Device1** 单击 **注册**.
   1. 选择 **分配显示** 并选择设备配置的路径。

   >[!NOTE]
   >如果您尝试在Screens播放器中查看内容，请确保单击 **更新离线内容** 从渠道功能板中，查看分配给显示屏的每个渠道。

### 查看结果 {#viewing-the-result}

使用上述步骤实施多区域布局后，将显示以下输出。

选中Screens播放器可查看在两个不同区域中显示内容的输出。 左和右区域（都使用嵌入式序列作为组件）。

左区域是序列渠道，右区域包括视频。

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
