---
title: 嵌入式序列
seo-title: 嵌入式序列
description: 可查看本页以了解渠道的嵌入式序列，通过这些嵌入式序列，用户可以在父渠道中添加组件，还可以重复使用不同渠道中的内容并将此内容嵌入到父渠道中。
seo-description: 可查看本页以了解渠道的嵌入式序列，通过这些嵌入式序列，用户可以在父渠道中添加组件，还可以重复使用不同渠道中的内容并将此内容嵌入到父渠道中。
uuid: 72a8d4e6-e5ce-4069-bf3b-864d03f61585
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: fc13d713-af30-4a54-8408-920f78fd2b2f
docset: aem65
translation-type: tm+mt
source-git-commit: 23ecaf3533c2298d98c37f2bbcb6cbe50aed17fc

---


# 嵌入式序列 {#embedded-sequences}

Using ***Embedded Sequences***, for channels, allows the user to add components in the parent channel and also to re-use the content from a different channel and embed it into the parent channel.

## 添加嵌入式序列 {#adding-embedded-sequences}

您可以选择向序列渠道中添加以下组件：

* 嵌入式序列
* 动态嵌入式序列

>[!NOTE]
>
>要了解如何在 Screens 项目中使用其他组件，请参阅[向渠道添加组件](adding-components-to-a-channel.md)。

### 添加嵌入式序列 {#adding-an-embedded-sequence}

您可以将嵌入式序列添加到渠道中。嵌入式序列是包含图像或视频等资产的另一个渠道。 添加嵌入式序列时，用户可以按“渠道路径”******&#x200B;将序列添加到渠道。

>[!NOTE]
>
>***渠道路径*** 定义对渠道的显式引用。
>
>要了解“渠道路径”**&#x200B;的更多信息，请参阅“创作屏幕”中的[渠道分配](channel-assignment.md)。

请按照以下步骤向您的渠道中添加嵌入式序列：

1. 选择要嵌入页面的渠道。For example, **We.Retail In-Store** --> **Channels** --> **Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. 单击左侧栏中的组件图标以添加嵌入式页面。Drag and drop the **Embedded Sequence** to the editor.
1. Double-click the **Embedded Sequence** component to add the channel to your original sequence channel.
1. Select the **Channel Path** of the channel.
1. Select the **Duration (ms)** for your embedded channel in the **Sequence** tab. By default, the duration is set to **-1**, that means embedded channel is fully run. 如果用户指定持续时间，那么子序列将在指定的时间中断（即截断）。

1. 将“按量 **收费播放策略** ”设 **置为正常**。

By default, it is set to **normal**. Setting the value to **normal** (Play all items) means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item** (Play a single item) and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

>[!I重要]
>必须将渠道（在嵌入式序列中使用）分配到同一显示屏。
>
>在之前的步骤中将嵌入式序列添加到渠道后，请按照以下步骤操作：
>
>1. 导航到显示屏，然后从“位置”文件夹中选 **择显示屏** 。
>1. 单击操 **作栏中的** “功能板”以导航到显示功能板。
>1. 从“已 **分配的渠道** ”和“已计划”面板中 **选择+分配渠道** ，以打开“渠道 **分配”对话框**。
   >
   >
1. 在渠道路径中选择您（在嵌入式序列中使用）的渠 **道路径**。
>1. 确保优先级 **低于** 主渠道。
   >
   >
1. 您不得选择任何受支 **持的活动**。
>1. 完成 **后，单击** “保存”。
>



以下示例显示了如何向现有渠道 (**Idle Channel**) 中添加嵌入式序列 (**Idle Channel - Night**)。

![new2](assets/new2.gif)

### 添加动态嵌入式序列 {#adding-a-dynamic-embedded-sequence}

您可以将动态嵌入式序列添加到渠道中。动态嵌入式序列与嵌入式序列类似，但动态嵌入式序列允许用户遵循一种层次结构，在该层次结构中，对一个渠道所做的更改/更新将会传播到相关的另一个渠道。它遵循父子层次结构，还包括图像或视频等资产。 添加动态序列时，用户可以按渠道角色添加渠道。

>[!NOTE]
>
>“渠道角色”******&#x200B;定义了显示屏的上下文。
>
>要了解“渠道角色”**&#x200B;的更多信息，请参阅“创作屏幕”中的[渠道分配](channel-assignment.md)。

请按照以下步骤向您的渠道中添加嵌入式序列：

1. 选择要嵌入动态序列的渠道。For example, **We.Retail In-Store** --> **Channels** --> **Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. 单击左侧栏中的组件图标以添加动态嵌入式序列。将动&#x200B;**态** **嵌入式序列**拖放到编辑器中。

1. Double-click the **Dynamic** **Embedded Sequence** component to add the page to your sequence channel.

1. Enter the **Channel Assignment Role**.
1. 将“按量 **收费播放策略** ”设 **置为正常**。 By default, it is set to **normal**. Setting the value to **normal** (Play all items) means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item** (Play a single item) and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

1. Select the **Duration (ms)** in **Sequence** tab for your embedded channel in the sequence.

![最新](assets/latest.gif)

