---
title: 渠道分配 — 最新FP
description: 了解渠道分配和日期划分。
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
TQID: https://experienceleague.adobe.com/-hIHgs66ksW-qvVaUp4euiJlPfbn0OGk88ASNIc4QZI
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: ba4275ba-c29a-4197-90dc-5a633402ca3c
  - id: d4878390-3838-4e80-8cb3-33bc1a01ea16
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 1464
ht-degree: 2%

---

# 渠道分配 {#channel-assignment}

>[!IMPORTANT]
>
>本节重点介绍AEM 6.5.5 Screens Feature Pack及更高版本的渠道分配和计划。

设置显示后，将渠道分配给显示以查看您的内容。

本页显示将渠道分配给显示器、了解渠道属性以及日期分隔。

此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

>[!NOTE]
>
>您可以为显示分配多个渠道。


## 分配渠道 {#assign-a-channel-new-release}

请按照以下部分创建AEM Screens项目并将渠道分配给显示。

### 创建AEM Screens项目和渠道 {#creating-project}

请按照以下步骤设置项目和渠道：

1. 创建标题为&#x200B;**DemoScreens**&#x200B;的AEM Screens项目。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >要了解如何创建AEM Screens项目，请参阅[创建和管理项目](creating-a-screens-project.md)。

1. 在&#x200B;**Channels**&#x200B;文件夹中创建标题为&#x200B;**Cafeteria**&#x200B;的序列频道。

1. 单击频道，然后单击操作栏中的&#x200B;**编辑**。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   例如，**食堂**&#x200B;频道现在显示以下图像：

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. 创建标题为&#x200B;**SanJose**&#x200B;的位置和显示为&#x200B;**大厅**&#x200B;的位置。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### 将渠道分配给显示 {#assigning-channel-to-display}

项目设置完成后，将渠道分配给显示区，以查看内容。

1. 导航到所需的显示，例如&#x200B;**DemoScreens** > **位置** > **SanJose** > **大厅**。

1. 单击操作栏中的&#x200B;**分配渠道**。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   或者，

   在操作栏中单击&#x200B;**仪表板**，然后在&#x200B;**“已分配的渠道和计划”**&#x200B;面板中单击&#x200B;**+分配渠道**。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. **渠道分配**&#x200B;对话框打开。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. 从&#x200B;**设置**&#x200B;选项中，您可以选择渠道&#x200B;**按路径**&#x200B;或&#x200B;**按名称**，输入&#x200B;**渠道角色**、**优先级**、**支持的事件**&#x200B;和&#x200B;**中断方法**。 此外，您还可以从此对话框启用有趣内容工具提示。

   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >要了解有关渠道分配属性的更多信息，请参阅[渠道属性](#channel-properties)部分。

1. 从&#x200B;**计划**&#x200B;选项中，单击&#x200B;**激活窗口**&#x200B;和&#x200B;**周期性计划**。
   ![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >要了解有关渠道分配属性的更多信息，请参阅[渠道属性](#channel-properties)部分。

1. 配置首选项后，单击&#x200B;**保存**。

### 在Chrome播放器中查看内容 {#viewing-content-output}

此示例显示了Chrome Player上的输出。 将渠道分配给显示区后，请将设备注册到播放器。

要了解如何在AEM Screens Player上注册设备，请参阅[设备注册](device-registration.md)。

您可以在选择的播放器上查看以下输出：

![新建1](assets/channel-assignment/channel-assign-output.gif)

## 时间线视图 {#timeline-view}

将渠道分配给显示区并设置周期性时间表后，您可以从&#x200B;**已分配的渠道和时间表**&#x200B;面板查看时间线。

按照以下步骤导航到时间线视图：

1. 导航到所需的显示，例如&#x200B;**DemoScreens** > **位置** > **SanJose** > **大厅**。

1. 单击操作栏中的&#x200B;**分配渠道**。

   或者，

   单击&#x200B;**仪表板**，然后单击&#x200B;**已分配的渠道和计划**&#x200B;面板中的&#x200B;**时间线**。

   ![图像](/help/user-guide/assets/channel-assignment/timeline-1.png)

## “通过渠道分配了解渠道属性”对话框 {#channel-properties}

以下属性是通过&#x200B;**渠道分配**&#x200B;对话框中的&#x200B;**设置**&#x200B;选项设置的。

![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### 选择一个渠道 {#select-channel}

通过选择渠道，您可以按渠道名称或渠道路径提供对所需渠道的引用。

* **按路径** — 您使用该渠道的绝对路径提供了显式引用。
* **按名称** — 您输入按上下文解析为实际渠道的渠道名称。 通过此功能，可创建渠道的本地版本，以便动态解析特定于位置的内容。 例如，名称为&#x200B;*每日交易数*&#x200B;的渠道，其中实际内容在两个城市可能不同，但您在所有显示区中仍具有正常的渠道角色。

### 渠道角色 {#role-channel}

渠道角色定义显示的上下文。 各种操作针对角色。 它与履行职责的实际渠道无关。

### 优先级 {#priority-channel}

优先级用于对分配进行排序，以防多个分配符合播放标准。 值最高的总是优先于较低的值。 例如，如果存在两个渠道A和B。 A的优先级为1，B的优先级为2，然后显示信道B，因为它优先级高于A。

>[!NOTE]
>
>如上所述，在&#x200B;**渠道分配**&#x200B;对话框中，渠道的优先级设置为数字（最小值为1）。 此外，分配的渠道根据降序优先级排序。

### 支持的事件 {#supported-events-channel}

* **初始加载** — 在播放器启动时加载频道。 可按计划将其分配给多个渠道。
* **空闲屏幕** — 在屏幕空闲时加载。 可按计划将其分配给多个渠道。
* **计时器** — 在提供计划时必须设置。
* **用户交互** — 如果屏幕上有空闲渠道中的用户交互（触控），则播放器切换到指定的渠道，并在触摸屏幕时加载。

### 中断方法 {#interruption-method-channel}

>[!IMPORTANT]
> 此选项仅在<!--AEM 6.4 Feature Pack 8 or-->AEM 6.5 Feature Pack 4中可用。

作为内容作者，您可以指定渠道中断的时间。 这样做可让您选择切断非关键内容。 但是，您还可以选择让重要内容在因日程安排而缩短内容之前完整播放。

从&#x200B;**渠道分配**&#x200B;对话框中选择以下选项之一，这些选项可用于设置中断方法：

* **立即** — 每当计划激活或收到更新时，您都可以中断播放，并立即刷新或播放新内容
* **当前项目结束** — 激活新计划或收到更新时，您可以选择等待序列中的当前项目完成播放。 之后，您才能刷新或播放新内容。

  >[!NOTE]
  >默认情况下，该选项处于选中状态。

* **序列结束** — 激活新计划或收到更新时，您可以选择等待整个序列结束。 然后，就在所需的序列之前，您可以循环播放回第一个元素、刷新或播放新内容。

  >[!NOTE]
  >使用第二个或第三个选项可能会导致对分配定义的调度时间稍微延迟。 原因是播放器在刷新之前等待项目或序列的结束（在指定的时间之后）。 延迟取决于项目的播放持续时间。

以下属性是通过&#x200B;**渠道分配**&#x200B;对话框中的&#x200B;**计划**&#x200B;选项设置的。

![图像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### 激活窗口 {#activation-window}

激活窗口允许您选择&#x200B;**开始日期**&#x200B;和&#x200B;**结束日期**&#x200B;来显示您的内容。

### 循环计划 {#recurrence-schedule}

周期性时间表允许您为内容设置周期性时间表。 单击&#x200B;**+添加计划**&#x200B;以将周期性计划添加到您的频道。

>[!NOTE]
>您可以向渠道添加多个周期性计划。
>周期性计划引入&#x200B;*DayParting*。您可以设置一个全局计划，让多个渠道在一天中的特定时间运行，然后一次性重新使用为所有的显示设置好的计划。

您可以设置以下选项：

* **名称** — 周期性计划的标题。
* **重复** — 选择计划是运行&#x200B;**每日**、**每周**、**每月**&#x200B;还是&#x200B;**每年**。
* **开始** — 计划的开始时间。
* **结束** — 计划的结束时间。 您可以按时间或持续时间进行设置。
   * **时间** — 计划将在指定的时间结束。
   * **持续时间** — 计划运行特定持续时间（小时或分钟）。

### DayParting {#dayparting}

日期划分是指将一天划分为多个时间段，并指定在所需时间播放哪些内容。 通过AEM Screens，您可以根据需要按照日期划分在一天、一周或一个月内安排渠道。

以下示例在三种不同的情景中解释了渠道中的DayParting：

#### 在划分为多个时隙的某天播放内容 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此示例说明一家餐厅如何使用DayParting每天展示其早餐、午餐和晚餐菜单。

在此，每天都会被划分为不同的时段，以便渠道内容可以在一天中的指定时间播放。 为渠道设置周期性计划的以下属性，以根据此用例播放内容。

| **名称** | **重复** | **启动** | **结束** |
|---|---|---|---|
| 早餐 | 每日 | 上午6:00 | 上午11:00 |
| 午餐 | 每日 | 上午11:00 | 下午3:00 |
| 晚餐 | 每日 | 下午3:00 | 晚上8:00 |

#### 在一周中的特定日期播放内容 {#playing-content-on-a-particular-day-of-the-week}

此示例显示了在赌场中实施的DayParting，该赌场中每个周末从晚上8:00到晚上10:00进行现场活动，并且晚上10:00到凌晨1:00的晚餐菜单上有特别优惠。

| **名称** | **重复** | **启动** | **结束** |
|---|---|---|---|
| 周末 | 每周：星期六和星期日 | 晚上8:00 | 下午10:00 |
| 特别计划 | 每日：星期一到星期五 | 下午10:00 | 上午1:00 |

>[!NOTE]
>
>此外，您还可以为每个渠道定义&#x200B;***优先级***。 例如，如果为同一天和时间或同一月份设置两个渠道，则首先播放具有较高优先级的渠道。 优先级的最小值可以设置为0。
