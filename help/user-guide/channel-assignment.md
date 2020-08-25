---
title: 渠道分配
seo-title: 渠道分配
description: 可查看本页以了解渠道分配和分时段功能。
translation-type: tm+mt
source-git-commit: 39da8293fb64321fdb28acaa67be579483ba4f0d
workflow-type: tm+mt
source-wordcount: '1215'
ht-degree: 37%

---


# 渠道分配 {#channel-assignment}

>[!IMPORTANT]
>本节重点介绍渠道分配和安排AEM 6.5.5 Screens版本之前的功能包渠道的安排。

设置显示屏后，必须为显示屏分配渠道，以视图内容。

本页显示了如何为显示屏分配渠道。

>[!NOTE]
>您可以为显示屏分配多个渠道。

## Assigning a Channel {#assign-a-channel}

请按照以下步骤为显示屏分配渠道：

1. 导航到所需的显示屏， **例如** DemoProject **—>位** 置 **** —> **SanJose**—> StoreDisplayDisplay。

   ![图像](assets/screen_shot_2018-08-23at25359pm.png)

1. Tap/click **Assign Channel** in the action bar

   或者，

   Tap/click **Dashboard** and click **+Assign Channel** from the **ASSIGNED CHANNNELS** panel to open the **Channel Assignment** dialog box.

   ![图像](/help/user-guide/assets/channel-assign1.png)

   您可以从以下部分的“ **渠道分配** ”对话框配置属性。 请参阅 [渠道属性](#channel-properties) 部分，进一步了解渠道属性。


## 从渠道分配了解渠道属性 {#channel-properties}

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

### 计划 {#schedule-channel}

通过计划，您可以在应当显示渠道时提供文本形式的说明。It also let&#39;s you define a start date (**active from**) and an end date (**active until**) for the channel to be shown.

**显示有趣内容工具提示**：

“显示有趣内容工具提示”定义了在渠道运行时是否必须显示有趣内容工具提示（“触摸任何位置可开始&#x200B;**”）。

### DayParting {#dayparting}

Schedules when combined with **DayParting**, allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

分时段功能是指将一天分成多个时段并指定在所需时间播放的内容。AEM Screens允许您根据要求在一天、一周或月内分时段计划渠道。

以下示例说明了三种不同情况下渠道的分时段功能：

#### 在一天内分多个时段播放内容 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此示例说明餐厅如何使用分时段功能展示其早餐、午餐和晚餐菜单。

在此，我们将每天分为三个不同的时段，以便渠道内容按一天中的指定时间播放：

| **渠道** | **角色** | **优先级** | **计划** |
|---|---|---|---|
| 菜单_A | 早餐 |  | 6:00 至 11:00 期间 |
| 菜单_B | 午餐 |  | 11:00 至 15:00 期间 |
| Menu_C | 晚餐 |  | 15:00 至 20:00 期间 |

#### 在一周中的特定一天播放内容 {#playing-content-on-a-particular-day-of-the-week}

此示例显示了在赌场中实现的dayParting，该赌场每周末从晚8:00至晚10:00进行实时事件，晚10:00至凌晨1:00提供特价晚餐菜单。

<table>
 <tbody>
  <tr>
   <td><strong>渠道</strong></td>
   <td><strong>角色</strong></td>
   <td><strong>优先级</strong></td>
   <td><strong>计划</strong></td>
  </tr>
  <tr>
   <td>LiveConcert</td>
   <td>周末</td>
   <td> </td>
   <td>2017年10月21日- 2017年10月22 <br /> 日20:00至22:00</td>
  </tr>
  <tr>
   <td>特价晚餐</td>
   <td>周末</td>
   <td> </td>
   <td>2017年10月21日- 2017年10月22 <br /> 日1点前22分</td>
  </tr>
 </tbody>
</table>

#### 在特定月份播放内容 {#playing-content-for-a-particular-month-months}

此示例显示了商店的DayParting，该商店在6月到8月显示其夏季收藏品，在9月到10月底显示秋季收藏品。

在此，您将按月创建分时段功能，以便渠道内容按年度的指定月份播放。

| **渠道** | **角色** | **优先级** | **计划** |
|---|---|---|---|
| SummerCollection | 夏天 |  | 2017年6月1日至2017年8月31日 |
| FallCollection | 秋 |  | 2017年9月1日至2017年10月30日 |

>[!NOTE]
>
>此外，您可以为每个渠道定义&#x200B;***优先级***。例如，如果将两个渠道设置为同一天同一时间或同一个月播放，则将先播放具有较高优先级的渠道。优先级的最小值可以设置为 0。

#### 播放具有相同优先级的渠道内容 {#playing-content-for-channels-with-same-priority}

此示例显示了商店的DayParting，该商店在12月的月份以相同计划显示其冬季收藏集。 但是，由于在最后一周渠道 B 的优先级设置为 2，因此，渠道 B 会播放其内容，而渠道 A 则不会播放内容。

| **渠道** | **角色** | **优先级** | **计划** |
|---|---|---|---|
| A | 冬季 | 1 | 2017年12月1日至2017年12月31日 |
| B | 圣诞节 | 2 | 2017年12月24日至2017年12月31日 |


>[!NOTE]
>
> 要进一步了解分时段功能，请参阅以下各节：
>
>* [处理资产中的重复](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [处理渠道中资产的重复](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)


