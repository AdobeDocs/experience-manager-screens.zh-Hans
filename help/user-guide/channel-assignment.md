---
title: 渠道分配
seo-title: Channel Assignment
description: 关注此页面，了解“渠道分配”和“时段分割”。
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 3%

---

# 渠道分配 {#channel-assignment}

>[!IMPORTANT]
>此部分重点介绍低于AEM 6.5.5 Screens版本的功能包的渠道分配和渠道计划。

设置显示后，必须为显示分配渠道以查看您的内容。

此页显示将渠道分配给您的显示区。

>[!NOTE]
>您可以为显示分配多个渠道。

## 分配渠道 {#assign-a-channel}

按照以下步骤为显示分配渠道：

1. 导航到所需的显示，例如， **演示项目** —> **位置** —> **圣何塞** —> **StoreDisplay**.

   ![图像](assets/screen_shot_2018-08-23at25359pm.png)

1. 点按/单击 **分配渠道** 操作栏中的

   或者,

   点按/单击 **仪表板** 并单击 **+指定渠道** 从 **已分配渠道** 用于打开 **渠道分配** 对话框。

   ![图像](/help/user-guide/assets/channel-assign1.png)

   您可以从以下位置配置属性 **渠道分配** 对话框。 请参阅 [渠道属性](#channel-properties) 部分，了解有关渠道属性的更多信息。


## 通过渠道分配了解渠道属性 {#channel-properties}

### 引用渠道 {#ref-channel}

引用渠道允许您按渠道名称或渠道路径提供对所需渠道的引用。

* **按路径**：使用渠道的绝对路径提供显式引用。

* **按名称**：输入将按上下文解析为实际渠道的渠道名称。 此功能允许您创建渠道的本地版本，以便动态解析特定于位置的内容。 例如，名为的渠道 *每日交易*，虽然实际内容在两个城市中可能有所不同，但您在所有显示屏上仍然具有正常的渠道角色。

### 渠道角色 {#role-channel}

渠道角色定义显示的上下文。 该角色由各种操作定向，并且独立于履行该角色的实际渠道。

### 优先级 {#priority-channel}

优先级用于对分配进行排序，以防多个分配符合播放标准。 值最高的总是优先于较低的值。 例如，如果存在两个渠道A和B。A的优先级为1，B的优先级为2，然后显示信道B，因为它的优先级高于A。

>[!NOTE]
>渠道的优先级在中设置为一个数字（最小值为1） **渠道分配** 对话框（如上所述）。 此外，分配的渠道根据递减优先级排序。

### 支持的事件 {#supported-events-channel}

* **初始加载**：在播放器启动时加载渠道。 可与计划一起将其分配给多个渠道
* **空闲屏幕**：在屏幕空闲时加载。 可与计划一起将其分配给多个渠道
* **计时器**：在提供计划时需要设置
* **用户交互**：如果在空闲渠道的屏幕上有用户交互（触摸），则播放器将切换到指定的渠道，并在触摸屏幕时加载

### 中断方法 {#interruption-method-channel}

>[!IMPORTANT]
>
> 此选项仅在AEM 6.4 Feature Pack 8或AEM 6.5 Feature Pack 4中可用。

作为内容作者，您应该能够指定渠道何时中断，以便能够选择切断非关键内容，但可以选择让重要内容完全播放，然后再因计划而切断播放。

从以下选项中选择一个选项，这些选项可用于设置中断方法 **渠道分配** 对话框：

* **立即**：每当激活计划或收到更新时，您可以中断播放并立即刷新或播放新内容
* **在当前项目结束时**：在激活新计划或收到更新时，您可以选择等待序列中的当前项目完成播放，并且仅在完成之后刷新或播放新内容
   >[!NOTE]
   >默认情况下，该选项处于选中状态。
* **在序列末尾**：当激活新计划或收到更新时，您可以选择等待整个序列到达其结尾，就在所需的序列之前，您循环返回到第一个元素，然后刷新或播放新内容

   >[!NOTE]
   >使用第二个或第三个选项可能会导致对分配定义的计划时间稍微延迟，因为播放器将在刷新之前等待项目或序列的结束（在指定的时间之后）。 延迟将取决于项目的播放持续时间。

### 计划 {#schedule-channel}

通过计划，您可以在应显示渠道时以文本形式提供描述。 它还允许您定义开始日期(**激活自**)和结束日期(**保持活动状态结束日期**)才能显示渠道。

**显示有趣内容工具提示**:

显示有趣内容工具提示定义有趣内容工具提示(&quot;*随处触碰以开始*“)是否显示。

### 日期分段 {#dayparting}

与合并时的计划 **日期分段**，允许您设置一个全局计划，在一天中的特定时间运行多个渠道，并一次为所有显示重复使用该设置。

DayParting是指将一天划分为多个时段，并指定在所需时间播放哪些内容。 AEM Screens允许您根据需要按照在一天、一周或一个月内的时段划分来安排渠道。

以下示例在三种不同的场景中解释了渠道中的日期划分：

#### 在划分为多个时隙的一天中播放内容 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此示例说明餐厅如何使用时段划分来展示其早餐、午餐和晚餐菜单。

在本例中，我们将每天划分为三个不同的时间段，以便渠道内容可以在一天中的指定时间播放：

| **渠道** | **角色** | **优先级** | **计划** |
|---|---|---|---|
| Menu_A | 早餐 |  | 6:00 至 11:00 期间 |
| Menu_B | 午餐 |  | 11:00 至 15:00 期间 |
| Menu_C | 晚餐 |  | 15:00 至 20:00 期间 |

#### 在一周中的某一天播放内容 {#playing-content-on-a-particular-day-of-the-week}

此示例显示了在赌场中实现的分日活动，其中现场活动在每周末的8:00 pm到10:00 pm之间进行，并且在10:00 pm后到1:00 am之间为晚餐菜单提供特别优惠。

<table>
 <tbody>
  <tr>
   <td><strong>渠道</strong></td>
   <td><strong>角色</strong></td>
   <td><strong>优先级</strong></td>
   <td><strong>计划</strong></td>
  </tr>
  <tr>
   <td>LiveConcent</td>
   <td>周末</td>
   <td> </td>
   <td>2017年10月21日至2017年10月22日 <br /> 20:00至22:00</td>
  </tr>
  <tr>
   <td>特别餐晚餐</td>
   <td>周末</td>
   <td> </td>
   <td>2017年10月21日至2017年10月22日 <br /> 22:00至1:00</td>
  </tr>
 </tbody>
</table>

#### 播放特定月/月的内容 {#playing-content-for-a-particular-month-months}

此示例显示了一个商店的DayParting，该商店显示其从6月到8月的夏季系列以及从9月到10月底的秋季系列。

在这里，您将创建按月划分时段，以便渠道内容按指定的月份播放。

| **渠道** | **角色** | **优先级** | **计划** |
|---|---|---|---|
| Summercollection | Summer |  | 2017年6月01日至2017年8月31日 |
| FallCollection | 跌落 |  | 2017年9月01日至2017年10月30日 |

>[!NOTE]
>
>此外，您还可以定义 ***优先级*** 用于每个渠道。 例如，如果为同一天和时间或同一月份设置两个渠道，则首先播放具有较高优先级的渠道。 优先级的最小值可以设置为0。

#### 为具有相同优先级的渠道播放内容 {#playing-content-for-channels-with-same-priority}

此示例显示了一个商店的DayParting，该商店在12月份使用相同的计划显示其冬季收藏集。 但由于频道B的优先级设置为2，因此在该周内，频道B播放其内容而不是频道A。

| **渠道** | **角色** | **优先级** | **计划** |
|---|---|---|---|
| A | Winter | 1 | 2017年12月01日至2017年12月31日 |
| B | 圣诞节 | 2 | 2017年12月24日至2017年12月31日 |


>[!NOTE]
>
> 要了解有关DayParting的更多信息，请参阅以下部分：
>
>* [处理资源中的重复项](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [处理渠道中的资产重复项](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)

