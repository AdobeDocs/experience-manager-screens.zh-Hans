---
title: AEM Screens语音识别
description: 本页描述了AEM Screens的语音识别功能。
translation-type: tm+mt
source-git-commit: e355d648846034c4762ef8fdcb3e218d868044b6
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 3%

---


# AEM Screens语音识别{#voice-recognition}

>[!IMPORTANT]
>
>**重要隐私信息**
>
>使用语音识别功能时，请遵循您所在区域的所有适用法律和道德准则（包括但不限于向最终用户显示播放器正在使用语音识别）。 Adobe Inc，不接收、存储或处理任何语音相关信息。 AEM Screens玩家使用内置在浏览引擎中的标准Web语音API。 在后台，此API会向Google的服务器发送从语音到文本的波形语音，并且此文本由播放器根据配置的关键字进行匹配。
>
>有关更多详细信息，请参阅Web语音API的[Google隐私白皮书](https://www.google.com/chrome/privacy/whitepaper.html#speech)。


语音识别功能允许在由语音交互驱动的AEM Screens渠道中的内容更改。

内容作者可以将显示器配置为启用语音。 此功能旨在允许客户利用语音作为与其显示器交互的方法。 一些类似用例包括在商店中查找产品推荐、在用餐者和餐馆订购菜单。 此功能增强了用户的可访问性，并可以极大增强客户体验。

>[!NOTE]
>播放器硬件必须支持语音输入，如麦克风。

## 实现语音识别{#implementing}

>[!IMPORTANT]
> 语音识别功能仅在Chrome OS和Windows播放器上可用。

要在您的AEM Screens项目中实现语音识别，您必须为显示屏启用语音识别，并将每个渠道与一个唯一标签相关联以触发渠道过渡。

下节介绍如何在AEM Screens项目中启用和使用语音识别功能。

## 在全屏或分屏渠道开关{#sequence-channel}中查看内容

在使用语音识别功能之前，请确保您有一个项目和一个渠道，其中的内容已为您的项目设置。

1. 以下示例展示名为&#x200B;**VoiceDemo**&#x200B;的演示项目和三个序列渠道&#x200B;**Main**、**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**，如下图所示。

   ![图像](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >要了解如何创建渠道或向渠道添加内容，请参阅[创建和管理渠道](/help/user-guide/managing-channels.md)

   或者，

   您可以创建三个序列渠道&#x200B;**Main**、**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**，以及一个额外的1x2分屏渠道&#x200B;**SplitScreen**，如下图所示。

   ![图像](assets/voice-recognition/vr-emb-1.png)

1. 导航到每个渠道并添加内容。 例如，导航到&#x200B;**VoiceDemo** —> **渠道** —> **主**&#x200B;并选择渠道。 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器并根据需要添加内容（图像／视频）。 同样，向&#x200B;**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**&#x200B;渠道添加内容。

   渠道现在包含资产（图像），如下图所示。

   **主要**:

   ![图像](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![图像](assets/voice-recognition/vr-3.png)

   **热饮**:

   ![图像](assets/voice-recognition/vr-2.png)

   如果已将“分屏”渠道添加到项目，请导航至&#x200B;**SplitScreen**&#x200B;并拖放两个嵌入式序列，并添加指向&#x200B;**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**渠道的路径，如下图所示。
   ![图像](assets/voice-recognition/vr-emb-6.png)


### 设置渠道{#setting-tags}的标记

向渠道添加内容后，您需要导航到每个渠道并添加相应的标记，以触发语音识别。

请按照以下步骤向渠道添加标记：

1. 导航到每个渠道并添加内容。 例如，导航到&#x200B;**VoiceDemo** —> **渠道** —> **主**&#x200B;并选择渠道。

1. 单击操作栏中的&#x200B;**属性**。

   ![图像](assets/voice-recognition/vr-5.png)

1. 导航到&#x200B;**Basics**&#x200B;选项卡，从&#x200B;**Tags**&#x200B;字段中选择已存在的标记，或创建新标记。

   您可以为标记键入新名称并点击`return`键来创建新标记，如下图所示：

   ![图像](assets/voice-recognition/vr-6.png)

   或者，

   您还可以提前从AEM实例为项目创建标记并选择这些标记。 按照[创建标记](#creating-tags)中所述的步骤操作后，您可以从位置选择标记并将其添加到渠道，如下图所示：

   ![图像](assets/voice-recognition/vr-tag1.png)

1. 同样，在&#x200B;**热饮**&#x200B;渠道中添加标题为&#x200B;**hot**&#x200B;的标签。

1. 如果您使用“分屏”渠道，请将标记（**hot**&#x200B;和&#x200B;**cold**）添加到&#x200B;**SplitScreen**&#x200B;渠道属性，如下图所示。

   ![图像](assets/voice-recognition/vr-emb-7.png)

1. 完成后，单击&#x200B;**保存并关闭**。


### 创建标记{#creating-tags}

请按照以下步骤创建标记：

1. 导航到AEM实例。

1. 单击工具图标—> **标记**。
   ![图像](assets/voice-recognition/vr-7.png)

1. 单击&#x200B;**创建** —> **创建命名空间**。
   ![图像](assets/voice-recognition/vr-tag3.png)

1. 输入项目名称，例如&#x200B;**VoiceDemo**，然后单击&#x200B;**创建**。

1. 选择&#x200B;**VoiceDemo**&#x200B;项目，然后单击操作栏中的&#x200B;**创建标记**。
   ![图像](assets/voice-recognition/vr-tag4.png)

1. 输入标记的名称，然后单击&#x200B;**提交**。
   ![图像](assets/voice-recognition/vr-tag5.png)

现在，您可以在AEM Screens项目中使用这些标签。

### 将渠道分配给显示屏并启用语音识别{#channel-assignment}

1. 在&#x200B;**Locations**&#x200B;文件夹中创建显示屏，如下图所示。

   ![图像](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >要了解如何将渠道分配给显示屏，请参阅[创建和管理显示屏](/help/user-guide/managing-displays.md)。

1. 将渠道&#x200B;**Main**、**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**&#x200B;分配给您的&#x200B;**LobbyDisplay**。 此外，如果您正在为项目使用&#x200B;**SplitScreen**&#x200B;渠道，请确保也将此分配给显示屏。

   >[!NOTE]
   >如果已创建分屏渠道，请将&#x200B;**SplitScreen**&#x200B;渠道分配给显示屏。

1. 在分配渠道时，为每个渠道设置以下属性。

   | **渠道名称** | **优先级** | **支持的事件** |
   |---|---|---|
   | 主要 | 2 | 初始加载、空闲屏幕、计时器 |
   | 热饮 | 1 | 用户交互 |
   | ColdDrinks | 3 | 用户交互 |
   | SplitScreen | 3 | 用户交互 |

   >[!NOTE]
   >
   >要了解如何将渠道分配给显示屏，请参阅[创建和管理显示屏](/help/user-guide/managing-displays.md)。

1. 将渠道分配给显示屏后，请导航到&#x200B;**LobbyDisplay**&#x200B;并选择显示屏。 从操作栏中选择&#x200B;**属性**。

1. 导航到&#x200B;**Display**&#x200B;选项卡，并在&#x200B;**Content**&#x200B;下启用&#x200B;**启用语音**&#x200B;选项。

   ![图像](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >必须从显示器启用语音识别功能。

### 在Chrome播放器中查看内容{#viewing-content}

完成上述步骤后，您可以注册Chrome设备以视图输出。

>[!NOTE]
>请参阅[设备注册](device-registration.md)，了解如何在AEM Screens播放器上注册设备。

**序列渠道所需输出**

**Main**&#x200B;渠道正在播放其内容，但是当您使用关键字&#x200B;**hot**&#x200B;如&#x200B;*我想要热饮*&#x200B;时，渠道开始正在播放&#x200B;**HotDrinks**&#x200B;渠道的内容。

同样，如果您使用关键字&#x200B;**cold**（如&#x200B;*）的单词，我希望有冷的*，则渠道开始播放&#x200B;**ColdDrinks**&#x200B;渠道的内容。

**拆分屏幕所需的输出渠道**

**Main**&#x200B;渠道正在播放其内容，但当您结合使用关键字&#x200B;**hot**&#x200B;和&#x200B;**cold**&#x200B;时，我想看到热饮和冷饮的菜单&#x200B;*,渠道开始正在播放&#x200B;**SplitScreen&lt;a**渠道。*&#x200B;如果您说&#x200B;*返回主菜单*，它将切换回主渠道。





