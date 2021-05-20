---
title: 渠道分配 — 最新FP
seo-title: 渠道分配 — 最新FP
description: 请阅读本页，了解渠道分配和分时段。
feature: 创作屏幕，渠道分配
role: Administrator, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '1475'
ht-degree: 23%

---

# 渠道分配 {#channel-assignment}

>[!IMPORTANT]
>
>本部分重点介绍AEM 6.5.5 Screens功能包及更高版本的渠道分配和计划。

设置显示屏后，必须为显示屏分配渠道才能查看内容。

本页将介绍如何为显示屏分配渠道、了解渠道属性和分时段。

>[!NOTE]
>
>您可以为显示屏分配多个渠道。


## 分配渠道{#assign-a-channel-new-release}

请按照以下部分创建AEM Screens项目并将渠道分配给显示屏。

### 创建AEM Screens项目和渠道{#creating-project}

按照以下步骤设置项目和渠道：

1. 创建标题为&#x200B;**DemoScreens**&#x200B;的AEM Screens项目。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >请参阅[创建和管理项目](creating-a-screens-project.md)以了解如何创建AEM Screens项目。

1. 在&#x200B;**Channels**&#x200B;文件夹中创建名为&#x200B;**Caferiate**&#x200B;的序列渠道。

1. 选择渠道，然后单击操作栏中的&#x200B;**编辑**&#x200B;以向渠道添加内容。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   例如，**Caferia**&#x200B;渠道现在显示以下图像：

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. 创建标题为&#x200B;**SanJose**&#x200B;的位置和标题为&#x200B;**Lobby**&#x200B;的显示屏。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### 将渠道分配给显示器{#assigning-channel-to-display}

项目设置完成后，必须将渠道分配给显示屏来查看内容。

1. 导航到所需的显示屏，例如&#x200B;**DemoScreens** —> **位置** —> **SanJose** —> **Lobby**。

1. 点按/单击操作栏中的&#x200B;**分配渠道** 。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   或者，

   点按/单击操作栏中的&#x200B;**功能板** ，然后单击&#x200B;**已分配的渠道和计划**&#x200B;面板中的&#x200B;**+分配渠道**。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. 将打开&#x200B;**渠道分配**&#x200B;对话框。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. 从&#x200B;**Settings**&#x200B;选项中，可以按路径&#x200B;**或按名称**&#x200B;选择渠道&#x200B;**或**，输入&#x200B;**渠道角色**、**优先级**、**受支持事件**&#x200B;和&#x200B;**中断方法**。 此外，您还可以从此对话框中启用有趣内容工具提示。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >请参阅[渠道属性](#channel-properties)一节，了解有关渠道分配属性的更多信息。

1. 从&#x200B;**计划**&#x200B;选项中，选择&#x200B;**激活窗口**&#x200B;和&#x200B;**重复计划**。
   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >请参阅[渠道属性](#channel-properties)一节，了解有关渠道分配属性的更多信息。

1. 配置首选项后，单击&#x200B;**Save**。

### 在Chrome播放器{#viewing-content-output}中查看内容

此示例在Chrome播放器中显示输出。 将渠道分配给显示屏后，必须向播放器注册设备。

请参阅[设备注册](device-registration.md)以了解如何在AEM Screens播放器上注册设备。

您将在选择的播放器中查看以下输出：

![new1](assets/channel-assignment/channel-assign-output.gif)

## 时间轴视图{#timeline-view}

将渠道分配给显示屏并设置重复计划后，您便可以从&#x200B;**已分配的渠道和计划**&#x200B;面板中查看时间轴。

按照以下步骤导航到时间轴视图：

1. 导航到所需的显示屏，例如&#x200B;**DemoScreens** —> **位置** —> **SanJose** —> **Lobby**。

1. 点按/单击操作栏中的&#x200B;**分配渠道** 。

   或者，

   点按/单击&#x200B;**功能板**，然后单击&#x200B;**已分配的渠道和计划**&#x200B;面板中的&#x200B;**时间轴**。

   ![图像](/help/user-guide/assets/channel-assignment/timeline-1.png)

## 了解渠道分配对话框{#channel-properties}中的渠道属性

以下属性是从&#x200B;**渠道分配**&#x200B;对话框的&#x200B;**Settings**&#x200B;选项中设置的。

![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### 选择一个渠道 {#select-channel}

通过选择渠道，您可以按渠道名称或渠道路径提供对所需渠道的引用。

* **按路径**：您可以使用渠道的绝对路径提供显式引用。

* **按名称**:您输入将按上下文解析为实际渠道的渠道名称。此功能允许您创建渠道的本地版本，以便动态解析特定于位置的内容。例如，名称为&#x200B;*每日交易*&#x200B;的渠道，其中两个城市的实际内容会有所不同，但您在所有显示屏上仍具有正常渠道角色。

### 渠道角色 {#role-channel}

渠道角色定义了显示屏的上下文。角色是多种操作的目标，且不依赖于履行角色的实际渠道。

### 优先级 {#priority-channel}

优先级用于在多个分配匹配播放条件时对分配进行排序。具有最高值的分配将始终优先于具有较低值的分配。例如，如果有两个渠道 A 和 B。A 的优先级为 1，B 的优先级为 2，则会显示渠道 B，因为它的优先级高于 A。

>[!NOTE]
>
>如上所述，渠道的优先级会在&#x200B;**渠道分配**&#x200B;对话框中设置为数字（最小值为 1）。此外，分配的渠道会按优先级以降序排列。

### 支持的事件 {#supported-events-channel}

* **初始加载**：播放器启动时加载渠道。可以将该事件与计划一起分配到多个渠道
* **空闲屏幕**：屏幕空闲时加载。可以将该事件与计划一起分配到多个渠道
* **计时器**：提供计划时需要对其进行设置
* **用户交互**：如果在空闲渠道中屏幕（触控）上存在用户交互，播放器将切换到指定的渠道，并将在触摸屏幕时加载该渠道

### 中断方法 {#interruption-method-channel}

>[!IMPORTANT]
> 此选项仅在AEM 6.4功能包8或AEM 6.5功能包4中提供。

作为内容作者，您应该能够指定渠道何时中断，以便选择切断非关键内容，但可以选择在因计划而切断播放之前，让重要内容充分播放。

从以下选项中进行选择，这些选项可用于从&#x200B;**渠道分配**&#x200B;对话框中设置中断方法：

* **立即**:每当计划被激活或收到更新时，您都可以停止播放并立即刷新或播放新内容
* **在当前项目的末尾**:当激活新计划或收到更新时，您可以选择等待序列中的当前项目完成播放，并且仅在刷新或播放新内容之后

   >[!NOTE]
   >默认情况下，此选项处于选中状态。

* **在序列末尾**:当激活新计划或收到更新时，您可以选择等待整个序列到达其结尾，而在所需序列之前，您将循环回第1个元素，刷新或播放新内容

   >[!NOTE]
   >使用第二个或第三个选项可能会导致在分配上定义的计划时间被稍微推迟，因为播放器在刷新之前将等待项目或序列的结束（在指定的时间之后）。 延迟取决于项目的播放持续时间。

以下属性是从&#x200B;**渠道分配**&#x200B;对话框的&#x200B;**Schedule**&#x200B;选项中设置的。

![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### 激活窗口 {#activation-window}

激活窗口允许您选择&#x200B;**开始日期**&#x200B;和&#x200B;**结束日期**&#x200B;来显示您的内容。

### 循环计划 {#recurrence-schedule}

循环计划允许您为内容设置循环计划。 单击&#x200B;**+添加计划**&#x200B;以向渠道添加重复计划。

>[!NOTE]
>您可以向渠道中添加多个循环计划。
>循环计划引入了&#x200B;*DayParting*，它允许您设置全局计划，其中多个渠道在一天中的特定时间运行，并同时为所有显示屏重复使用该设置。

您可以设置以下选项：

* **名称**:定期计划的标题。
* **重复**:选择计划是 **每日**、 **每周**、 **每月**&#x200B;还 **是每年**。
* **开始**:计划的开始时间。
* **结束**:计划的结束时间。您可以按时间或持续时间设置此参数。
   * **时间**:计划将在指定时间结束。
   * **持续时间**:计划以小时或分钟为单位在特定时间段内运行。

### 分时段 {#dayparting}

日期划分是指将一天划分为多个时段，并指定在所需时间播放的内容。 AEM Screens允许您根据需要在一天、一周或一个月内按照分时段方式计划渠道。

以下示例说明了在三种不同情况下渠道中使用日期划分的方法：

#### 在一天内分多个时段播放内容 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此示例展示了餐厅如何使用DayParting展示其每日早餐、午餐和晚餐菜单。

在本例中，我们将每天分为不同的时段，以便渠道内容在一天中的指定时间播放。 根据此用例，为渠道设置循环计划的以下属性以播放内容。

| **名称** | **重复** | **开始** | **结束** |
|---|---|---|---|
| 早餐 | 每日 | 6:00 AM | 上午11:00 |
| 午餐 | 每日 | 上午11:00 | 下午3:00 |
| 晚餐 | 每日 | 下午3:00 | 晚8:00 |

#### 在一周中的特定一天播放内容 {#playing-content-on-a-particular-day-of-the-week}

此示例显示了在赌场中实施的分时段功能，该赌场在每周末的晚上8:00至晚上10:00举办现场活动，晚上10:00至凌晨1:00提供晚餐菜单。

| **名称** | **重复** | **开始** | **结束** |
|---|---|---|---|
| 周末 | 每周：星期六，星期日 | 晚8:00 | 晚上10:00 |
| 特价 | 每日：星期一至星期五 | 晚上10:00 | 凌晨1:00 |

>[!NOTE]
>
>此外，您可以为每个渠道定义&#x200B;***优先级***。例如，如果将两个渠道设置为同一天同一时间或同一个月播放，则将先播放具有较高优先级的渠道。优先级的最小值可以设置为 0。
