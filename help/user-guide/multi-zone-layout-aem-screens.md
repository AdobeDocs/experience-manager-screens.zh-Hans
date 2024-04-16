---
title: 多区域布局
description: 了解如何在AEM Screens中创建多个区域内容并使用各种资源，例如可合并到单个屏幕中的视频、图像和文本。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# 多区域布局 {#multi-zone-layout}

以下页面介绍了多区域布局的使用情况，并涵盖了以下主题：

* 概述
* 创建多区域布局
* 先决条件
* 在一个或多个区域中使用单个资产
* 在一个或多个区域中使用序列内容

## 概述 {#overview}

***多区域布局*** 让您能够创建多个区域内容，并使用可以在单个屏幕中组合的各种资产，例如视频、图像和文本。 您可以纳入图像、视频和文本，使它们能够混合在一起，创建直观的数字体验。

根据项目要求，有时您需要在一个渠道中拥有多个区域，并将它们编辑为一个完整的单元。 例如，在单个渠道的三个独立区域中运行的具有相关社交媒体馈送的产品序列。

>[!NOTE]
>在多区域渠道中，由于潜在的冲突和意外行为，不建议进行资产级计划。 如果需要进行资产级计划，建议创建一个单独的序列渠道并在该渠道中应用计划逻辑。 接下来，将序列通道嵌入到多区域通道中。

### 先决条件 {#prerequisites}

在开始实施此功能之前，请确保您对以下内容具有概念性知识：

* [创建AEM Screens项目](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project)
* [创建显示](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays)
* [将渠道分配给显示](/help/user-guide/channel-assignment.md)

## 创建多区域布局 {#creating-multi-zone-layout}

在创建渠道时，您可以使用不同的模板在渠道中创建区域。 您可以添加单个图像、视频或嵌入式渠道，以便按顺序显示多个资产。

**创建渠道**

1. 选择Adobe Experience Manager链接（左上方），然后 **Screens**. 或者，您可以直接转到： `http://localhost:4502/screens.html/content/screens`.
1. 导航到 **渠道** 文件夹并选择 **创建** 从操作栏中。

1. 选择 **1x2分屏渠道** 从 **创建** 向导。

1. 选择 **下一个** 并输入 **标题** 作为 **多区**.

1. 选择 **创建** 以完成渠道创建。

### 在一个或多个区域中使用单个资产 {#using-single-assets-in-one-or-more-zones}

您可以在所有单独的区域中使用单个资产，例如图像或视频。 要实施，请执行以下步骤：

1. **向渠道添加内容**

   1. 导航到 **区域** > **渠道**> **多区**.
   1. 选择 **多区** 渠道和选择 **编辑** 从操作栏中。

1. **将图像添加到渠道**

   要在两个区域播放单个图像或视频，只需将图像拖放到渠道编辑器中的每个区域即可，如下图所示：

   ![图像](/help/user-guide/assets/multi-zone/multizone-img3.png)

### 在一个或多个区域中使用序列内容 {#using-sequenced-content-in-one-or-more-zones}

如果您希望这些区域在不同区域中显示图像序列和视频，请按照以下步骤了解详细信息。

1. **创建渠道文件夹**

   1. 导航到 **区域** > **多区** > **渠道** 并选择 **创建** 从操作栏中。
   1. 选择 **渠道文件夹** 从 **创建** 向导并选择 **下一个**.
   1. 输入标题为 **嵌入式渠道** 并选择 **创建**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **将两个以上的渠道添加到渠道文件夹**

   1. 导航到 **区域** > **渠道** > **嵌入式渠道** 并选择 **创建** 从操作栏中。
   1. 选择 **序列渠道** 从 **创建** 创建标题为 **`Zone1`**.
   1. 选择 **`Zone1`** 并选择 **编辑** 从操作栏中。
   1. 将一些图像拖放到此渠道中。
   1. 同样，创建另一个标题为 **`Zone2`** 在 **嵌入式渠道** 文件夹。
   1. 将视频拖放到此渠道中。

   下图显示了通道 **`Zone1`** 和 **`Zone2`**：

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   添加到编辑器的图像 **`Zone1`** 序列渠道如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   视频已添加到的编辑器 **`Zone2`** 序列渠道如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **将嵌入式序列（组件）添加到主通道(MultiZone)**

   1. 导航到 **区域** > **渠道** > **多区**.
   1. 选择 **编辑** 从操作栏中。
   1. 拖放 **嵌入式序列** 组件添加到两个区域。
   1. 在其中一个区域中选择嵌入序列。
   1. 选择 **配置** 编辑器中的一个嵌入序列的（扳手）图标。
   1. 选择渠道路径为 **区域** > **渠道** > **嵌入式渠道** > **`Zone1`**，如下图所示。
   1. 同样，添加 **`Zone2`** 到编辑器中的另一个嵌入序列组件。

      ![图像](/help/user-guide/assets/multi-zone/multizone-3.png)

### 创建位置和显示 {#creating-location}

创建一个位置和显示，以便您可以在AEM Screens播放器中查看内容。

1. **创建位置**

   1. 导航到 **区域** > **位置** 文件夹。
   1. 选择 **位置** 文件夹并选择 **创建** 从操作栏中。
   1. 选择 **位置** 从 **创建** 向导并选择 **下一个**.
   1. 输入 **标题** 作为 **圣何塞** 并选择 **创建**.

1. **创建显示**

   1. 导航到 **区域** > **位置** 文件夹。
   1. 选择 **圣何塞** 位置和选择 **创建** 从操作栏中。
   1. 选择 **显示** 从 **创建** 向导并选择 **下一个**.
   1. 输入 **标题** 作为 **大厅** 并选择 **创建**.

### 将渠道分配给显示 {#channel-channel}

将渠道分配给显示内容以查看内容。 按照以下步骤将渠道分配给显示器。

1. **将渠道分配给显示**

   1. 导航到 **区域** > **位置** > **圣何塞**> **大厅**.
   1. 选择 **大厅** 显示并选择 **分配渠道** 从操作栏中。
   1. 输入路径 **多区** 中的频道 **渠道路径**.
   1. 设置 **受支持的事件** 作为 **初始加载**， **空闲屏幕**、和 **计时器**.
   1. 选择&#x200B;**保存**。

      ![图像](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. 同样，将其他两个嵌入渠道分配给(**`Zone1`** 和 **`Zone2`**)。
   1. 将三个渠道分配给 **大厅** ”时，您应该能够从“显示”功能板中查看分配的渠道。

      ![图像](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      >分配主渠道后(在本例中， **多区**)，必须分配其他两个嵌入渠道 **`Zone1`** 和 **`Zone2`** 也显示相同的内容。

### 注册设备 {#registering-device}

设置位置和显示后，请按照以下步骤注册设备并为设备分配显示。

1. **注册设备**

   1. 导航到 **区域** > **设备** 文件夹。
   1. 选择 **设备** 文件夹并选择 **设备管理器** 从操作栏中。
   1. 选择 **设备注册** 并从列表中选择待处理的设备。

      >[!NOTE]
      > 设备的标题必须与设备令牌匹配(**令牌** 字段)，显示在 **设备注册** 选项卡。

   1. 如果标题与设备令牌匹配，则选择设备并选择 **注册设备** 从操作栏中。
   1. 如果注册代码与Screens播放器中的代码匹配 **设备注册** 选项卡，选择 **验证** 从操作栏中。
      ![图像](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. 输入 **标题** 作为 **`Chrome-Device1`** 并选择 **注册**.
   1. 选择 **分配显示区** 并选择设备配置的路径。

   >[!NOTE]
   >如果您尝试在Screens播放器中查看内容，请确保选择 **更新离线内容** 从渠道功能板中，找到分配给显示的每个渠道。

### 查看结果 {#viewing-the-result}

使用上述步骤实施多区域布局时，将显示以下输出。

选中Screens播放器，以便查看在两个不同区域中显示内容的输出。 左侧和右侧区域（都使用嵌入式序列作为组件）。

左区域是序列通道，右区域包括视频。

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
