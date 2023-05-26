---
title: 永久接管渠道
seo-title: Perpetual TakeOver Channel
description: 遵循此用例创建永久接管渠道。
seo-description: Follow this Use Case on setting up a project that creates a Perpetual TakeOver channel that plays for a specific time day and time continuously.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 5d112f33-a7cf-415e-9ea7-dc18a0356a8d
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 1%

---

# 永久接管渠道 {#perpetual-takeover-channel}

以下页面展示了一个用例，重点介绍如何设置项目，了解如何创建在特定时间（天和时间）连续播放的永久接管渠道。

## 用例描述 {#use-case-description}

此用例说明了如何创建具有以下特征的渠道 *接管* 来自一个显示器或一组显示器的正常播放频道。 收购将在特定的日期和时间持续进行。
例如，有一个永久接管频道，从星期五上午9点到上午10点播放该频道。 在此期间，不应播放其他渠道。 以下示例展示了如何创建永久接管渠道，该渠道允许内容从每周三的2:00 pm到下午4:00，并且每周三的2小时播放。

### 前提条件 {#preconditions}

在开始此用例之前，请确保您了解如何：

* **[创建和管理渠道](managing-channels.md)**
* **[创建和管理位置](managing-locations.md)**
* **[创建和管理时间表](managing-schedules.md)**
* **[设备注册](device-registration.md)**

### 主要行为者 {#primary-actors}

内容作者

## 设置项目 {#setting-up-the-project}

按照以下步骤设置项目：

**设置渠道和显示**

1. AEM Screens创建标题为 **永久接管**，如下所示。

   ![资产](assets/p_usecase1.png)

1. 创建 **MainAdChannel** 在 **渠道** 文件夹。

   ![资产](assets/p_usecase2.png)

1. 选择 **MainAdChannel** 并单击 **编辑** 操作栏中的。 将一些资产（图像、视频、嵌入式序列）拖放到您的渠道中。

   ![资产](assets/p_usecase3.png)


   >[!NOTE]
   >此 **MainAdChannel** 在此示例中，演示了一个连续播放内容的序列渠道。

1. 创建 **接管** 接收中内容的渠道 **MainAdChannel** 每周三下午2:00到4:00之间播放。

1. 选择 **接管** 并单击 **编辑** 操作栏中的。 将一些资产拖放到您的渠道中。 以下示例展示了添加到此渠道的单个区域图像。

   ![资产](assets/p_usecase4.png)

1. 设置渠道的位置和显示。 例如，以下位置 **MainLobby** 和显示 **MainLobbyDisplay** 已为此项目设置。

   ![资产](assets/p_usecase5.png)

**将渠道分配给显示**

1. 选择显示区 **MainLobbyDisplay** 从 **位置** 文件夹。 单击 **分配渠道** 从操作栏中打开 **渠道分配** 对话框。

   >[!NOTE]
   >要了解如何将渠道分配给显示，请参阅 **[渠道分配](channel-assignment.md)**.

1. 填充字段(**渠道路径**， **优先级**、和 **受支持的事件**)中的 **渠道分配** 对话框，然后单击 **保存** 以分配 **MainAdChannel** 到您的显示区。

   * **渠道路径**：选择路径 **MainAdChannel** 渠道
   * **优先级**：将此渠道的优先级设置为1。
   * **受支持的事件**：选择 **初始加载** 和 **空闲屏幕**.

   ![资产](assets/p_usecase6.png)

1. 选择显示区 **接管** 从 **位置** 文件夹。 单击 **分配渠道** 以分配接管渠道。

1. 要分配 **接管** 在计划时间显示，并填充以下字段 **渠道分配** 对话框，然后单击 **保存**：

   * **渠道路径**：选择路径 **接管** 渠道
   * **优先级**：将此渠道的优先级设置为大于 **MainAdChannel**. 例如，本示例中设置的优先级为8。
   * **受支持的事件**：选择 **空闲屏幕** 和 **计时器**.
   * **计划**：输入您希望此渠道运行显示的计划文本。 此文本位于 **计划** 本示例中提到的 *星期三14点后到16点前*.

      >[!NOTE]
      >要了解有关可以添加到中的表达式的更多信息，请 **计划**，请参阅 [示例表达式](#example-expressions) 部分。
   * **激活自**：开始日期和时间。
   * **保持活动状态结束日期**：结束日期和时间。

      例如，文本位于 **计划** 和 **激活自** 和 **保持活动状态结束日期** 此处的日期和时间允许内容从每周三下午2:00到下午4:00播放。


      ![资产](assets/p_usecase7.png)

      导航到显示区，从 **接管** —> **位置** —> **MainLobby** —> **MainLobbyDisplay** 并单击 **仪表板** ，查看已分配渠道及其优先级，如下所示。

      >[!NOTE]
      >必须将接管渠道的优先级设置为最高。

      ![资产](assets/p_usecase8.png)
现在， **接管** 渠道将接管 **MainAdChannel** 每周三下午2:00播放2小时，直到下午4:00，并从2020年1月9日到2020年1月31日播放其内容。

## 示例表达式 {#example-expressions}

下表总结了将渠道分配给显示内容时可以添加到计划的几个示例表达式。

| **表达式** | **解释** |
|---|---|
| 上午8点之前 | 该频道每天上午8:00之前播放 |
| 下午2:00 | 该频道每天下午2:00后播放 |
| 12:15后和12:45前 | 该频道每天12:15后播放30分钟 |
| 12:15之前还有12:45之后 | 该频道在每天中午12:15之前播放，然后在中午12:45之后播放 |
| 1月1日下午2:00之后也是1月2日也是1月3日凌晨3:00之前 | 该频道在1月1日下午2:00之后开始播放，并在1月2日继续播放一整天，一直到1月3日凌晨3:00 |
| 1月1-2日下午2:00之后以及1月2-3日凌晨3:00之前 | 该频道在1月1日下午2:00之后开始播放该节目，一直播放到1月2日凌晨3:00，然后在1月2日下午2:00再次开始播放并继续播放到1月3日凌晨3:00 |

>[!NOTE]
>
>您还可以使用 _军事时间_ 表示法（即14:00），而不是 *上午/下午* 表示法（即下午2:00）。
