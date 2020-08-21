---
title: AEM Screens语音识别
description: 本页描述了AEM Screens的语音识别功能。
translation-type: tm+mt
source-git-commit: c46cd26f5067468aadf80a822fffce1d5f0b5d9a
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---


# AEM Screens语音识别 {#voice-recognition}

## 概述 {#overview}

语音识别功能允许在由语音交互驱动的AEM Screens渠道中更改内容。

内容作者可以将显示器配置为启用语音。 这允许根据显示器注册的所有玩家理解语音。 您必须为显示屏启用语音识别，并将每个渠道与唯一标签相关联以触发渠道过渡。

>[!NOTE]
>播放器硬件必须支持语音输入，如麦克风。

>[!IMPORTANT]
> 语音识别功能仅在Chrome和电子播放器上可用。

## 实现语音识别 {#implementing}

下节介绍如何在AEM Screens项目中启用和使用语音识别功能。

### 设置项目 {#setting-up}

在使用语音识别功能之前，请确保您有一个项目和一个渠道，其中内容已为您的项目设置。

1. 以下示例展示了一个名为VoiceDemo的 **演示项目** ，以及三个序列 **渠道** Main **、** ColdDrinks和 **** HotDrinks饮料，如下图所示。

   >[!NOTE]
   >
   >要了解如何创建渠道或向渠道添加内容，请参阅创 [建和管理渠道](/help/user-guide/managing-channels.md)

1. 导航到每个渠道并添加内容。 例如，导航到 **VoiceDemo** —> **渠道****—>** Main，然后选择渠道。 单击 **操作栏** 中的“编辑”以打开编辑器并根据您的要求添加内容（图像／视频）。 同样，向ColdDrinks和 **HotDrinks** 渠道 **添加内容** 。

   渠道现在包含以下内容，如下图所示。

   **主要**:

   **ColdDrinks**:

   **热饮**:

### 为渠道设置标记 {#setting-tags}

向渠道添加内容后，您需要导航到每个渠道并添加相应的标记，以触发语音识别。

请按照以下步骤向渠道添加标记：

1. 导航到每个渠道并添加内容。 例如，导航到 **VoiceDemo** —> **渠道****—>** Main，然后选择渠道。

1. Click **Properties** from the action bar.

1. 导航到 **基础** (Basics)选项卡，从“标记”(Tags)字段中选 **择已有** 的标记，或创建新标记。

1. 完成 **后，单击** “保存并关闭”。


### 将渠道分配给显示屏 {#channel-assignment}

1. 在“位置”文 **件夹** 中创建显示屏，如下图所示。

   >[!NOTE]
   >
   >要了解如何将渠道分配给显示屏，请参阅创 [建和管理显示屏](/help/user-guide/managing-displays.md)。

1. 将渠道 **Main**、 **ColdDrinks**&#x200B;和HotDrinks分 **配给您的** LobbyDisplay **** Adobe。


1. 为每个渠道设置以下属性。

   >[!NOTE]
   >
   >要了解如何将渠道分配给显示屏，请参阅创 [建和管理显示屏](/help/user-guide/managing-displays.md)。

1. 将渠道分配给显示屏后，导航到 **LobbyDisplay** ，然后选择显示屏。 从操 **作栏** 中选择属性。

1. 导航到“显 **示** ”选项卡，并在“内 **容”下启用** “启用 **语音”选项**。

   >[!NOTE]
   >必须从显示器启用语音识别功能。

## 在Chrome播放器中查看内容 {#viewing-content}

完成上述步骤后，您可以注册Chrome设备并视图输出。

应遵循以下步骤：

1. 导航到 **设备** 文件夹，并单 **击操作栏** 中的“设备管理器”以注册设备。







