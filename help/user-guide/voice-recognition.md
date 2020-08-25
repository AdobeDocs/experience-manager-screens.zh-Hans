---
title: AEM Screens语音识别
description: 本页描述了AEM Screens的语音识别功能。
translation-type: tm+mt
source-git-commit: 0300af2ef44756dddbb27f3da15c52bc877b93ea
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 2%

---


# AEM Screens语音识别 {#voice-recognition}

## 概述 {#overview}

语音识别功能允许在由语音交互驱动的AEM Screens渠道中更改内容。

内容作者可以将显示器配置为启用语音。 此功能旨在允许客户利用语音作为与其显示器交互的方法。 一些类似用例包括在商店中查找产品推荐、在用餐者和餐馆订购菜单。 此功能增强了用户的可访问性，并可以极大增强客户体验。


>[!NOTE]
>播放器硬件必须支持语音输入，如麦克风。

>[!IMPORTANT]
> 语音识别功能仅在Chrome和电子播放器上可用。

## 实现语音识别 {#implementing}


要在您的AEM Screens项目中实现语音识别，您必须为显示屏启用语音识别，并将每个渠道与一个唯一标签相关联以触发渠道过渡。

下节介绍如何在AEM Screens项目中启用和使用语音识别功能。

### 设置项目 {#setting-up}

在使用语音识别功能之前，请确保您有一个项目和一个渠道，其中内容已为您的项目设置。

1. 以下示例展示了一个名为VoiceDemo的 **演示项目** ，以及三个序列 **渠道** Main **、** ColdDrinks和 **** HotDrinks饮料，如下图所示。

   ![图像](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >要了解如何创建渠道或向渠道添加内容，请参阅创 [建和管理渠道](/help/user-guide/managing-channels.md)

1. 导航到每个渠道并添加内容。 例如，导航到 **VoiceDemo** —> **渠道****—>** Main，然后选择渠道。 单击 **操作栏** 中的“编辑”以打开编辑器并根据您的要求添加内容（图像／视频）。 同样，为ColdDrinks和 **HotDrinks** 渠道 **添加内容** 。

   渠道现在包含资产（图像），如下图所示。

   **主要**:

   ![图像](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![图像](assets/voice-recognition/vr-3.png)

   **热饮**:

   ![图像](assets/voice-recognition/vr-2.png)

### 为渠道设置标记 {#setting-tags}

向渠道添加内容后，您需要导航到每个渠道并添加相应的标记，以触发语音识别。

请按照以下步骤向渠道添加标记：

1. 导航到每个渠道并添加内容。 例如，导航到 **VoiceDemo** —> **渠道****—>** Main，然后选择渠道。

1. Click **Properties** from the action bar.

   ![图像](assets/voice-recognition/vr-5.png)

1. 导航到 **基础** (Basics)选项卡，从“标记”(Tags)字段中选 **择已有** 的标记，或创建新标记。

   您可以通过为标记键入新名称来创建新标记，如下图所示：

   ![图像](assets/voice-recognition/vr-6.png)

   或者，

   您可以预先从AEM实例为项目创建标记，也可以选择这些标记。

   请按照以下步骤创建标记：

   1. 导航到AEM实例。
   1. 单击工具—> **标记**。
      ![图像](assets/voice-recognition/vr-7.png)

1. 完成 **后，单击** “保存并关闭”。

同样，在HotDrinks **渠道** 中添加标题为 **“热”的** 标签 **，在ColdDrinks** 渠道中添 **加“冷”的** 标签。

### 将渠道分配给显示屏 {#channel-assignment}

1. 在“位置”文 **件夹** 中创建显示屏，如下图所示。

   >[!NOTE]
   >
   >要了解如何将渠道分配给显示屏，请参阅创 [建和管理显示屏](/help/user-guide/managing-displays.md)。

1. 将渠道 **Main**、 **ColdDrinks**&#x200B;和HotDrinks分 **配给您的** LobbyDisplay **** Adobly。


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







