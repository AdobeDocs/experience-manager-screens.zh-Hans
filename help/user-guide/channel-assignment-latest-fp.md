---
title: 渠道分配——最新FP
seo-title: 渠道分配——最新FP
description: 可查看本页以了解渠道分配和分时段功能。
translation-type: tm+mt
source-git-commit: 1c6a7342288a5d78dbea91d29ff8e5d6c8fec486
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 28%

---


# 渠道分配 {#channel-assignment}

>[!IMPORTANT]
>本节重点介绍AEM 6.5.5 Screens功能包及更高版本的渠道分配和渠道安排。

设置显示屏后，必须为显示屏分配渠道，以视图内容。

本页显示了如何为显示屏分配渠道。

>[!NOTE]
>您可以为显示屏分配多个渠道。


## Assigning a Channel {#assign-a-channel-new-release}

请按照以下部分创建AEM Screens项目，并为显示屏分配渠道。

### 创建AEM Screens项目和渠道 {#creating-project}

请按照以下步骤设置项目和渠道:

1. 创建一个标题为DemoScreens的 **AEM Screens项目**。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >请参阅 [创建和管理项目](creating-a-screens-project.md) ，了解如何创建AEM Screens项目。

1. 在“渠道”文件夹中创 **建标题为** “自助 **餐** ”的序列渠道。

1. 选择渠道，然 **后单** 击操作栏中的编辑，向渠道添加内容。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   例如，Caferia渠道 **现在显** 示以下图像：

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. 创建标题为SanJose **的位置** ，以及标题为Lobby **的显示屏**。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### 将渠道分配给显示屏 {#assigning-channel-to-display}

项目设置完成后，必须将渠道分配给显示屏以视图内容。

1. 导航到所需的显示屏， **例如** DemoScreens **—>** 位置 **—** > SanJose **—**> Lobby Chrobby。

1. Tap/click **Assign Channel** from the action bar.

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   或者，

   点按／单击 **仪表板** ，然后单 **击“已指定** 的渠道和 **计划”面板中的“** 并分配渠道”。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. The **Channel Assignment** dialog box opens.

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. 从“设 **置** ”选项中，可以按路径或名称选择渠道，输入渠道角色、优先级、受支持事件和中断方法。 此外，您还可以从此对话框启用“有趣内容工具提示”选项。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >请参阅 [渠道属性](#channel-properties) 部分，进一步了解渠道属性。

1. 从计划 **选项** 中，选择引 **用时区**、激活 **窗口** 和重复计划 ****。

1. 配置 **首选项** 后，单击“保存”。

### 在Chrome Player中查看内容 {#viewing-content-output}

### 从渠道分配了解渠道属性 {#channel-properties}

### Reference Channel {#ref-channel}

引用渠道允许您按渠道名称或渠道路径提供对所需渠道的引用。

* **按路径**：您可以使用渠道的绝对路径提供显式引用。

* **按名称**:输入将按上下文解析为实际渠道的渠道的名称。 此功能允许您创建渠道的本地版本，以便动态解析特定于位置的内容。For example, a channel with name *deals of the day*, where the actual content would be different in two cities, but you still have the sane channel role on all the displays.

### 渠道角色 {#role-channel}

渠道角色定义了显示屏的上下文。该角色由各种操作来定位，并且与完成该角色的实际渠道无关。

### 优先级 {#priority-channel}

优先级用于在多个分配匹配播放条件时对分配进行排序。具有最高值的分配将始终优先于具有较低值的分配。例如，如果有两个渠道 A 和 B。A 的优先级为 1，B 的优先级为 2，则会显示渠道 B，因为它的优先级高于 A。

>[!NOTE]
>如上所述，渠道的优先级会在&#x200B;**渠道分配**&#x200B;对话框中设置为数字（最小值为 1）。此外，分配的渠道会按优先级以降序排列。

### 支持的事件 {#supported-events-channel}

* **初始加载**：播放器启动时加载渠道。可以将该事件与计划一起分配到多个渠道
* **空闲屏幕**：屏幕空闲时加载。可以将该事件与计划一起分配到多个渠道
* **计时器**：提供计划时需要对其进行设置
* **用户交互**：如果在空闲渠道中屏幕（触控）上存在用户交互，播放器将切换到指定的渠道，并将在触摸屏幕时加载该渠道

### 中断方法 {#interruption-method-channel}

>[!IMPORTANT]
>
> 此选项仅在AEM 6.4 Feature Pack 8或AEM 6.5 Feature Pack 4中可用。

作为内容作者，您应当能够指定渠道何时中断，以便选择切断非关键内容，但可以选择在由于日程安排而中断播放之前让重要内容完全播放。

从以下选项中进行选择，以从“渠道分配”对话框中设置 **中断方法** :

* **立即**:只要计划激活或收到更新，您就可以停止播放并立即刷新或播放新内容
* **在当前项目的末尾**:当激活新计划或收到更新时，您可以选择等待序列中的当前项目完成播放，并且仅在刷新或播放新内容之后
   >[!NOTE]
   >此选项默认处于选中状态。
* **在序列末尾**:当激活新计划或收到更新时，您可以选择等待整个序列到达其末尾，并且在所需序列之前，您循环回第1个元素，刷新或播放新内容

   >[!NOTE]
   >使用第二个或第三个选项可能导致在分配上定义的调度时间被稍微推迟，因为播放器在刷新之前将等待项目或序列的结束（在指定时间之后）。 延迟取决于项目的播放持续时间。