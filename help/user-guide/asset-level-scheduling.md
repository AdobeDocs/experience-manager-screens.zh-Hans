---
title: 资产级别激活
description: 了解如何在播放器的本地时区的计划时间范围内在渠道中激活特定资产。
feature: Authoring Screens, Asset Level Activation
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '1460'
ht-degree: 1%

---

# 资产级别激活 {#asset-level-scheduling}

本页介绍渠道中使用的资产的资产级激活。

本节涵盖以下主题：

* 概述
* 激活窗口
* 单个事件播放
* 处理资源中的重复项
   * DayParting
   * WeekParting
   * MonthParting
   * 部件的组合
* 多资产激活
* 通用开始时间的全局覆盖

<!-- REFERS TO ARCHIVED VERSIONS THAT ADOBE NO LONGER SUPPORTS>
>[!CAUTION]
>
>This AEM Screens functionality is only available if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permission, you can download it from Package Share. -->

## 概述 {#overview}

***资产级别激活*** 可让您在播放器的本地时区的计划时间范围内，在渠道中激活特定资产。 这适用于图像、视频、过渡、页面和嵌入式渠道（动态或静态）。

*例如*，则您希望在星期一和星期三的快乐时间（下午2点至下午5点）内仅显示特殊促销活动。

使用此功能，您不仅可以指定开始和结束日期及时间，还可以指定循环模式。

## 激活窗口 {#single-event-playback}

资源级激活可通过配置 **激活** 选项卡。

请按照以下步骤执行资产层计划：

1. 单击任意渠道，然后单击 **编辑** 从操作栏中。

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >详细了解如何
   >
   >* 创建项目，请参见 [创建新项目](creating-a-screens-project.md).
   >* 创建内容并将其添加到渠道，请参阅 [管理渠道](managing-channels.md).

1. 单击 **编辑** 因此，您可以打开渠道编辑器，然后单击要应用计划的资产。

   ![图像](/help/user-guide/assets/asset-activation/asset-level2.png)

1. 单击资产，然后单击左上方 **配置** （扳手图标）。

   单击 **激活** 选项卡。

   ![图像](/help/user-guide/assets/asset-activation/asset-level3.png)

1. 您可以使用以下方式指定日期选取器的日期 **保持活动状态起始日期** 和 **保持活动状态结束日期** 字段。

   如果您单击 **保持活动状态起始日期** 和 **保持活动状态结束日期** 日期和时间，则资产将只显示开始日期/时间和结束日期/时间之间并循环。

   ![图像](/help/user-guide/assets/asset-activation/asset-level3.png)

## 处理资源中的重复项 {#handling-recurrence-in-assets}

您也可以根据自己的要求，安排资产以特定的时间间隔每日、每周或每月重复使用。

假设您只想在星期五下午1:00到晚上10:00显示图像。 您可以使用 **激活** 选项卡，为资源设置所需的重复间隔。

### 日划分 {#day-parting}

1. 单击资产，然后单击 **配置** （扳手图标）以打开“属性”对话框。

1. 输入开始日期/时间和结束/日期时间后，可以使用表达式或自然文本版本指定循环计划。

   >[!NOTE]
   >您可以跳过或包含 **保持活动状态起始日期** 和 **保持活动状态结束日期** 字段并根据您的要求将表达式添加到Schedules字段。

1. 将表达式输入到 **计划** 并且您的资产会在特定的日期和时间间隔内显示。

#### Day划分的示例表达式 {#example-one}

下表汇总了在为显示分配渠道时可以添加到计划的几个示例表达式。

| **表达式** | **解释** |
|---|---|
| 上午8点之前。 | 渠道中的资产在每天上午8:00之前播放 |
| 下午2点以后。 | 渠道中的资产在每日下午2:00之后播放 |
| 12:15 至 12:45 期间 | 渠道中的资产在每日下午12:15之后播放30分钟 |
| 12:15之前以及12:45之后 | 渠道中的资产在每天中午12:15之前播放，然后在中午12:45之后播放。 |

>[!NOTE]
>
>您还可以使用 _军事时间_ 表示法(14:00)，而不是 *上午./P.M。* （下午2:00）

### WeekParting {#week-parting}

1. 单击资产，然后单击 **配置** （扳手图标）。

1. 输入开始日期/时间和结束/日期时间后，可以使用表达式或自然文本版本指定循环计划。

   >[!NOTE]
   >您可以跳过或包含 **保持活动状态起始日期** 和 **保持活动状态结束日期** 字段并根据您的要求将表达式添加到Schedules字段。

1. 将表达式输入到 **计划** 并且您的资产会在特定的日期和时间间隔内显示。

#### WeekParting的示例表达式 {#example-two}

下表汇总了在为显示分配渠道时可以添加到计划的几个示例表达式。

| **表达式** | **解释** |
|---|---|
| `Mon,Wed,Fri` | 资产从星期一、星期三和星期五开始在渠道中播放 |
| `Mon-Thu` | 资产从星期一到星期四在渠道中播放 |

>[!NOTE]
>
>您还可以使用 _完整_ 表示法(`Monday,Wednesday,Friday`)，而不是 _短手_ (`Mon,Wed,Fri`)。


### MonthParting {#month-parting}

1. 单击资产，然后单击 **配置** （扳手图标）。

1. 输入开始日期/时间和结束/日期时间后，可以使用表达式或自然文本版本指定循环计划。

   >[!NOTE]
   >您可以跳过或包含 **保持活动状态起始日期** 和 **保持活动状态结束日期** 字段并根据您的要求将表达式添加到Schedules字段。

1. 将表达式输入到 **计划** 并且您的资产会在特定的日期和时间间隔内显示。

#### MonthParting的示例表达式 {#example-three}

下表汇总了在为显示分配渠道时可以添加到计划的几个示例表达式。

| **表达式** | **解释** |
|---|---|
| `on February,May,August,November` | 该资产将于2月、5月、8月和11月在渠道中播放 |
| `on February-July` | 该资产从2月播放到7月底 |

>[!NOTE]
>在定义星期和月份时，您可以使用短写符号和全名符号，例如，周一/星期一和一月/一月。

### 部件的组合 {#combined-parting}

1. 单击资产，然后单击 **配置** （扳手图标）。

1. 输入开始日期/时间和结束/日期时间后，可以使用表达式或自然文本版本指定循环计划。

   >[!NOTE]
   >您可以跳过或包含 **保持活动状态起始日期** 和 **保持活动状态结束日期** 字段并根据您的要求将表达式添加到Schedules字段。

1. 将表达式输入到 **计划** 并且您的资产会在特定的日期和时间间隔内显示。

#### 分块组合的示例表达式 {#example-four}

下表汇总了在为显示分配渠道时可以添加到计划的几个示例表达式。

| **表达式** | **解释** |
|---|---|
| `after 6:00 and before 18:00 on Mon,Wed of Jan-Mar` | 从1月到3月底，周一和周三上午6点到下午6点之间，该资产会在渠道中播放 |
| `on the 1st day of January after 2:00 P.M. also on the 2nd day of January also on the 3rd day of January before 3:00 A.M.` | 渠道中的资产在1月1日下午2点后开始播放，并在1月2日继续播放一整天，一直到1月3日凌晨3点 |
| `on the 1-2 days of January after 2:00 P.M. also on the 2-3 days of January before 3:00 A.M.` | 渠道中的资产在1月1日下午2:00之后开始播放，继续播放直到1月2日凌晨3:00，然后在1月2日下午2:00重新开始播放，并继续播放直到1月3日凌晨3:00 |

>[!NOTE]
>在定义星期和月份时，您可以使用短写符号和全名符号，例如，周一/星期一和一月/一月。 此外，您还可以使用 _军事时间_ 表示法(14:00)，而不是 *上午./P.M。*（下午2:00）


## 多资产激活 {#multi-asset-scheduling}

<!--
>[!CAUTION]
>
>The **Multi-asset Activation** feature is only available if you have installed AEM 6.3 Feature Pack 5 or AEM 6.4 Feature Pack 3. -->

***多资产激活*** 允许用户单击多个资源并将播放计划应用于所有选定资源。

### 先决条件 {#prerequisites}

要为资源使用多资源级激活，请创建一个具有序列渠道的AEM Screens项目。 例如，以下用例展示了功能的实施：

* AEM Screens创建标题为 **MultiAssetDemo**.
* 创建标题为 **MultiAssetChannel** 并将内容添加到渠道中，如下图所示。

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

请按照以下步骤单击多个资源并计划将它们显示在AEM Screens项目中：

1. 单击 **MultiAssetChannel**，然后单击 **编辑** 从操作栏中。

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. 单击编辑器中的多个资源，然后单击 **编辑激活** （左上角图标）。

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. 单击中的日期和时间 **保持活动状态起始日期** 和 **保持活动状态结束日期** 从 **组件激活** 对话框。 选择完计划后，单击复选标记图标。

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. 单击刷新可检查将应用多资源计划的资源。

   >[!NOTE]
   >
   >计划图标位于具有多资产激活的资产右上角。

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

## 通用开始时间的全局覆盖 {#global-override-scheduling}

***通用开始时间的全局覆盖***，是一种设置，它允许内容作者根据特定时间定义图像或视频资源的播放。 不使用任何单个播放器的时间/时区设置。

通常，播放由任何给定播放器的本地时间确定，但通过全局覆盖，可以使用特定的通用开始时间来启动资源的播放。

这允许内容作者将特定资源的播放指定为在特定日期/时间发生，而不管具有所分配内容的任何播放器上的本地时钟为何。

通用开始时间的全局覆盖是通过配置 **激活** 选项卡。 请按照以下步骤执行资产计划的全局覆盖：

1. 单击任意渠道，然后单击 **编辑** 以添加或编辑渠道中的内容。

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

1. 单击 **编辑**.
1. 在渠道编辑器中，单击要对其应用计划的资产。

   ![screen_shot_2018-12-21at70550am](/help/user-guide/assets/asset-activation/Asset-level4.png)

1. 对于全局覆盖，请在 **时区覆盖** 资源部分。 如果您没有在此区域输入任何内容，则应用的时区是播放器的时区。


