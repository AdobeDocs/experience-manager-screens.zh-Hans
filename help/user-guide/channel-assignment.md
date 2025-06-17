---
title: 渠道分配
description: 了解渠道分配和时段分割。
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 2%

---

# 渠道分配 {#channel-assignment}

>[!IMPORTANT]
>此部分重点介绍低于AEM 6.5.5 Screens版本的Feature Pack的渠道分配和计划。

设置显示后，将渠道分配给显示以查看您的内容。

本页显示分配渠道给显示区。

>[!NOTE]
>您可以为显示分配多个渠道。

## 分配渠道 {#assign-a-channel}

请按照以下步骤将渠道分配给显示：

1. 导航到所需的显示，例如&#x200B;**DemoProject** > **位置** > **SanJose** > **StoreDisplay**。

   ![图像](assets/screen_shot_2018-08-23at25359pm.png)

1. 在操作栏中单击&#x200B;**分配渠道**。

   或，

   单击“**仪表板**”并单击“**已分配渠道**”面板中的“**+分配渠道**”，以便打开“**渠道分配**”对话框。

   ![图像](/help/user-guide/assets/channel-assign1.png)

   您可以从以下部分的&#x200B;**渠道分配**&#x200B;对话框中配置属性。 有关渠道属性的更多信息，请参阅[渠道属性](#channel-properties)部分。

## 通过渠道分配了解渠道属性 {#channel-properties}

### 引用渠道 {#ref-channel}

引用渠道允许您按渠道名称或渠道路径提供对所需渠道的引用。

* **路径** — 您使用该渠道的绝对路径提供了显式引用。

* **按名称** — 您输入按上下文解析为实际渠道的渠道名称。 通过此功能，可创建渠道的本地版本，以便动态解析特定于位置的内容。 例如，名称为&#x200B;*每日交易数*&#x200B;的渠道，其中实际内容在两个城市可能不同，但您在所有显示区中仍具有正常的渠道角色。

### 渠道角色 {#role-channel}

渠道角色定义显示的上下文。 该角色可定向各种操作，且独立于履行该角色的实际渠道。

### 优先级 {#priority-channel}

优先级用于对分配进行排序，以防多个分配符合播放标准。 值最高的总是优先于较低的值。 例如，如果存在两个渠道A和B。A的优先级为1，B的优先级为2，然后显示信道B，因为它优先级高于A。

>[!NOTE]
>如上所述，在&#x200B;**渠道分配**&#x200B;对话框中，渠道的优先级设置为数字（最小值为1）。 此外，分配的渠道根据降序优先级排序。

### 支持的事件 {#supported-events-channel}

* **初始加载** — 在播放器启动时加载频道。 可按计划将其分配给多个渠道。
* **空闲屏幕** — 在屏幕空闲时加载。 可按计划将其分配给多个渠道。
* **计时器** — 在提供计划时必须设置。
* **用户交互** — 如果屏幕上有空闲渠道中的用户交互（触控），则播放器切换到指定的渠道，并在触摸屏幕时加载。

### 中断方法 {#interruption-method-channel}

>[!IMPORTANT]
>
> 此选项仅在<!--AEM 6.4 Feature Pack 8 or -->AEM 6.5 Feature Pack 4中可用。

作为内容作者，请指定渠道中断的时间。 这样做可让您根据需要剪切非关键内容，但可以选择在由于计划而剪切其播放之前播放重要内容。

单击以下选项之一，这些选项可用于从&#x200B;**渠道分配**&#x200B;对话框设置中断方法：

* **立即** — 每当计划激活或收到更新时，您都可以中断播放并立即刷新或播放新内容。
* **在当前项目结束时** — 激活新计划或收到更新时，您可以选择等待序列中的当前项目完成播放。 只有在这之后，您才能刷新或播放新内容。

  >[!NOTE]
  >默认情况下，该选项处于选中状态。
* **序列结束** — 激活新计划或收到更新时，您可以选择等待整个序列结束。 然后，就在所需的序列之前，您可以循环播放回第一个元素、刷新或播放新内容。

  >[!NOTE]
  >使用第二个或第三个选项可能会导致对分配定义的调度时间稍微延迟。 原因是播放器在刷新之前等待项目或序列的结束（在指定的时间之后）。 延迟取决于项目的播放持续时间。

### 计划 {#schedule-channel}

通过计划，可在渠道出现时以文本形式提供描述。 它还允许您为要显示的渠道定义开始日期（**从**&#x200B;开始处于活动状态）和结束日期（**到**&#x200B;为止）。

**显示有趣内容工具提示**

“显示有趣内容”工具提示定义在渠道运行时是否必须显示有趣内容工具提示（“*从任何位置触碰开始*”）。

### DayParting {#dayparting}

与&#x200B;**DayParting**&#x200B;结合使用的计划允许您设置全局计划，其中多个渠道在一天中的特定时间运行，并且允许您同时重用为所有显示设置的全局计划。

DayParting是指将一天划分为多个时段，并指定在所需时间播放哪些内容。 通过AEM Screens，您可以根据需要按照在一天、一周或一个月内进行日期划分来计划渠道。

以下示例在三种不同的情景中解释了渠道中的日期划分：

#### 在划分为多个时隙的某天播放内容 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此示例显示餐厅如何使用DayParting来展示其早餐、午餐和晚餐菜单。

在这里，您将每天划分为三个不同的时隙，以便在一天中的指定时间播放渠道内容：

| **频道** | **角色** | **优先级** | **计划** |
|---|---|---|---|
| Menu_A | 早餐 |  | 6:00之后和11:00之前 |
| 菜单B | 午餐 |  | 11:00之后和15:00之前 |
| Menu_C | 晚餐 |  | 15:00至20:00期间 |

#### 在一周中的特定日期播放内容 {#playing-content-on-a-particular-day-of-the-week}

此示例显示了在赌场中实现的分日活动，该赌场的直播活动在每周末的下午8:00到下午10:00之间进行，并且在10:00到凌晨1:00之间可提供晚餐菜单上的特殊优惠。

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
   <td>2017年10月21日至2017年10月22日20:00之后22:00之前<br /></td>
  </tr>
  <tr>
   <td>特别餐晚餐</td>
   <td>周末</td>
   <td> </td>
   <td>2017年10月21日至2017年10月22日22:00之后1:00之前<br /></td>
  </tr>
 </tbody>
</table>

#### 播放特定月/月的内容 {#playing-content-for-a-particular-month-months}

此示例显示了一个商店的DayParting，该商店显示其从6月到8月的夏季系列以及从9月到10月的秋季系列。

在这里，您按照每月创建DayParting，以便渠道内容按照一年中的指定月份播放。

| **频道** | **角色** | **优先级** | **计划** |
|---|---|---|---|
| SummerCollection | Summer |  | 2017年6月1日至2017年8月31日 |
| FallCollection | 跌落 |  | 2017年9月1日至2017年10月30日 |

>[!NOTE]
>
>此外，您还可以为每个渠道定义&#x200B;***优先级***。 例如，如果为同一天和时间或同一月份设置两个渠道，则首先播放具有较高优先级的渠道。 优先级的最小值可以设置为0。

#### 为具有相同优先级的渠道播放内容 {#playing-content-for-channels-with-same-priority}

此示例显示了使用相同计划在12月份显示其冬季收藏集的商店的DayParting。 但由于频道B的优先级设置为2，因此在该周内，频道B播放其内容而不是频道A。

| **频道** | **角色** | **优先级** | **计划** |
|---|---|---|---|
| A | Winter | 1 | 2017年12月01日至2017年12月31日 |
| B | 圣诞节 | 2 | 2017年12月24日至2017年12月31日 |


>[!NOTE]
>
> 要了解有关DayParting的更多信息，请参阅以下部分：
>
>* [在Assets中处理循环](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling)
>* [在渠道中处理Assets的循环](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation)
