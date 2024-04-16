---
title: 渠道分配 — 最新FP
description: 了解渠道分配和日期划分。
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '1448'
ht-degree: 2%

---

# 渠道分配 {#channel-assignment}

>[!IMPORTANT]
>
>此部分重点介绍AEM 6.5.5 Screens功能包及更高版本的渠道分配和计划。

设置显示后，将渠道分配给显示以查看您的内容。

本页显示将渠道分配给显示器、了解渠道属性以及日期分隔。

>[!NOTE]
>
>您可以为显示分配多个渠道。


## 分配渠道 {#assign-a-channel-new-release}

请按照以下部分创建AEM Screens项目并将渠道分配给显示。

### 创建AEM Screens项目和渠道 {#creating-project}

请按照以下步骤设置项目和渠道：

1. AEM Screens创建标题为 **DemoScreens**.

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >要了解如何创建AEM Screens项目，请参阅 [创建和管理项目](creating-a-screens-project.md).

1. 创建标题为 **自助餐厅** 在 **渠道** 文件夹。

1. 单击渠道，然后单击 **编辑** 从操作栏中。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   例如， **自助餐厅** 渠道现在显示以下图像：

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. 创建标题为 **圣何塞** 和显示为 **大厅**.

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### 将渠道分配给显示 {#assigning-channel-to-display}

项目设置完成后，将渠道分配给显示区，以查看内容。

1. 导航到所需的显示，例如， **DemoScreens** > **位置** > **圣何塞** > **大厅**.

1. 单击 **分配渠道** 从操作栏中。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   或者，

   单击 **仪表板** 操作栏中，然后单击 **+指定渠道** 从 **已分配的渠道和计划** 面板。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. 此 **渠道分配** 对话框打开。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. 从 **设置** 选项，您可以选择渠道 **按路径** 或 **按名称**，输入 **渠道角色**， **优先级**， **受支持的事件**、和 **中断方法**. 此外，您还可以从此对话框启用有趣内容工具提示。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >要了解有关渠道分配属性的更多信息，请参阅 [渠道属性](#channel-properties) 部分。

1. 从 **计划** 选项，单击 **激活窗口** 和 **周期性计划**.
   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >要了解有关渠道分配属性的更多信息，请参阅 [渠道属性](#channel-properties) 部分。

1. 单击 **保存** 配置您的首选项后。

### 在Chrome播放器中查看内容 {#viewing-content-output}

此示例在Chrome播放器上展示了输出。 将渠道分配给显示区后，请将设备注册到播放器。

要了解如何在AEM Screens播放器上注册设备，请参阅 [设备注册](device-registration.md).

您可以在选择的播放器上查看以下输出：

![new1](assets/channel-assignment/channel-assign-output.gif)

## 时间线视图 {#timeline-view}

当您将渠道分配给显示并设置循环计划时，您可以从以下位置查看时间线： **已分配的渠道和计划** 面板。

按照以下步骤导航到时间线视图：

1. 导航到所需的显示，例如， **DemoScreens** > **位置** > **圣何塞** > **大厅**.

1. 单击 **分配渠道** 从操作栏中。

   或者，

   单击 **仪表板** 并单击 **时间线** 从 **已分配的渠道和计划** 面板。

   ![图像](/help/user-guide/assets/channel-assignment/timeline-1.png)

## “通过渠道分配了解渠道属性”对话框 {#channel-properties}

以下属性是从 **设置** 中的选项 **渠道分配** 对话框。

![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### 选择一个渠道 {#select-channel}

通过选择渠道，您可以按渠道名称或渠道路径提供对所需渠道的引用。

* **按路径**  — 使用渠道的绝对路径提供显式引用。
* **按名称**  — 输入按上下文解析为实际渠道的渠道名称。 通过此功能，可创建渠道的本地版本，以便动态解析特定于位置的内容。 例如，名为的渠道 *每日交易*，虽然实际内容在两个城市中可能有所不同，但您在所有显示屏上仍然可以发挥正常的渠道作用。

### 渠道角色 {#role-channel}

渠道角色定义显示的上下文。 该角色由各种操作定向，独立于履行该角色的实际渠道。

### 优先级 {#priority-channel}

优先级用于对分配进行排序，以防多个分配符合播放标准。 值最高的总是优先于较低的值。 例如，如果存在两个渠道A和B。A的优先级为1，B的优先级为2，然后显示信道B，因为它优先级高于A。

>[!NOTE]
>
>渠道的优先级在中设置为一个数字（最小值为1） **渠道分配** 对话框（如上所述）。 此外，分配的渠道根据降序优先级排序。

### 支持的事件 {#supported-events-channel}

* **初始加载**  — 在播放器启动时加载渠道。 可按计划将其分配给多个渠道。
* **空闲屏幕**  — 在屏幕空闲时加载。 可按计划将其分配给多个渠道。
* **计时器**  — 在提供计划时必须设置。
* **用户交互**  — 如果屏幕上的用户交互（触摸）位于空闲渠道中，则播放器切换到指定的渠道，并在触摸屏幕时加载。

### 中断方法 {#interruption-method-channel}

>[!IMPORTANT]
> 此选项仅适用于 <!--AEM 6.4 Feature Pack 8 or-->AEM 6.5 Feature Pack 4.

作为内容作者，您可以指定渠道中断的时间。 这样做可让您选择切断非关键内容。 但是，您还可以选择让重要内容在因日程安排而缩短内容之前完整播放。

从以下选项中选择一个选项，这些选项可用于设置中断方法 **渠道分配** 对话框：

* **立即**  — 每当激活计划或收到更新时，您都可以中断播放并立即刷新或播放新内容
* **当前项目的结尾**  — 激活新计划或收到更新时，您可以选择等待序列中的当前项目完成播放。 之后，您才能刷新或播放新内容。

  >[!NOTE]
  >默认情况下，该选项处于选中状态。

* **在序列末尾**  — 在激活新计划或收到更新时，您可以选择等待整个序列到达终点。 然后，就在所需的序列之前，您可以循环播放回第一个元素、刷新或播放新内容。

  >[!NOTE]
  >使用第二个或第三个选项可能会导致对分配定义的调度时间稍微延迟。 原因是播放器在刷新之前等待项目或序列的结束（在指定的时间之后）。 延迟取决于项目的播放持续时间。

以下属性是从 **计划** 中的选项 **渠道分配** 对话框。

![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### 激活窗口 {#activation-window}

激活窗口允许您选择 **开始日期** 和 **结束日期** 以显示您的内容。

### 循环计划 {#recurrence-schedule}

周期性时间表允许您为内容设置周期性时间表。 单击 **+添加计划** 以向渠道中添加周期性计划。

>[!NOTE]
>您可以向渠道添加多个周期性计划。
>周期性时间表引入 *DayParting* 此设置允许您设置一个全局计划，在一天中的特定时间运行多个渠道，并重复使用为全部显示设置的全局计划。

您可以设置以下选项：

* **名称**  — 周期性计划的标题。
* **重复**  — 选择计划是否运行 **每日**， **每周**， **每月**，或 **每年**.
* **开始**  — 计划的开始时间。
* **结束**  — 计划的结束时间。 您可以按时间或持续时间进行设置。
   * **时间**  — 计划将在指定的时间结束。
   * **持续时间**  — 时间表在特定时间段内运行，以小时或分钟为单位。

### DayParting {#dayparting}

日期划分是指将一天划分为多个时间段，并指定在所需时间播放哪些内容。 通过AEM Screens，您可以根据需要按照日期划分在一天、一周或一个月内安排渠道。

以下示例在三种不同的情景中解释了渠道中的DayParting：

#### 在划分为多个时隙的某天播放内容 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此示例说明一家餐厅如何使用DayParting每天展示其早餐、午餐和晚餐菜单。

在此，每天都会被划分为不同的时段，以便渠道内容可以在一天中的指定时间播放。 为渠道设置周期性计划的以下属性，以根据此用例播放内容。

| **名称** | **重复** | **启动** | **结束** |
|---|---|---|---|
| 早餐 | 每日 | 清晨6点 | 上午11:00 |
| 午餐 | 每日 | 上午11:00 | 下午3:00 |
| 晚餐 | 每日 | 下午3:00 | 晚上8点 |

#### 在一周中的特定日期播放内容 {#playing-content-on-a-particular-day-of-the-week}

此示例显示了在赌场中实施的DayParting，其中实时活动在每周末的下午8:00到下午10:00之间进行，并且在10:00到凌晨1:00之间可在晚餐菜单中找到特别优惠。

| **名称** | **重复** | **启动** | **结束** |
|---|---|---|---|
| 周末 | 每周：星期六和星期日 | 晚上8点 | 晚上10点 |
| 特别计划 | 每日：星期一到星期五 | 晚上10点 | 凌晨1点 |

>[!NOTE]
>
>此外，您还可以定义 ***优先级*** 用于每个渠道。 例如，如果为同一天和时间或同一月份设置两个渠道，则首先播放具有较高优先级的渠道。 优先级的最小值可以设置为0。
