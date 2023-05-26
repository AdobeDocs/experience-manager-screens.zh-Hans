---
title: 单次使用接管渠道
seo-title: Single Use TakeOver Channel
description: 按照此用例创建单次使用接管渠道。
seo-description: Follow this Use Case for creating a Single Use TakeOver Channel.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3317f07a-784f-4c4a-93ea-c84f4e42e9f2
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 2%

---

# 单次使用接管渠道 {#single-use-takeover-channel}

以下页面展示了一个用例，重点介绍如何设置一个项目，介绍如何创建一个在特定时间内只播放一次的Single TakeOver渠道。


## 用例描述 {#use-case-description}

此用例说明了如何创建具有以下特征的渠道 *接管* 来自一个显示器或一组显示器的正常播放频道。 接管操作将只进行一次，并且只进行一个特定时间。
例如，有一个“单次接管”频道，在星期五上午9点至上午10点播放。 在此期间，不应播放其他渠道。 在此时间之前和之后，单次使用接管渠道将不播放。 以下示例展示了如何创建一个播放的单一接管渠道，该渠道允许在12月31日凌晨12:00到凌晨12:01之间播放内容2分钟。

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

1. AEM Screens创建标题为 **SingleUseTakeOver**，如下所示。

   ![资产](assets/single-takeover1.png)

1. 创建 **MainAdChannel** 在 **渠道** 文件夹。

   ![资产](assets/single-takeover2.png)

1. 选择 **MainAdChannel** 并单击 **编辑** 操作栏中的。 将一些资产（图像、视频、嵌入式序列）拖放到您的渠道中。

   ![资产](assets/single-takeover2.png)


   >[!NOTE]
   >此 **MainAdChannel** 在此示例中，演示了一个连续播放内容的序列渠道。

   ![资产](assets/single-takeover3.png)

1. 创建 **接管** 接收中内容的渠道 **MainAdChannel** 和将只在特定的日期和时间播放。

1. 选择 **接管** 并单击 **编辑** 操作栏中的。 将一些资产拖放到您的渠道中。 以下示例展示了添加到此渠道的单个区域图像。

   ![资产](assets/single-takeover4.png)

1. 设置渠道的位置和显示。 例如，以下位置 **大厅** 和显示 **MainLobbyDisplay** 已为此项目设置。

   ![资产](assets/single-takeover5.png)

**将渠道分配给显示**

1. 选择显示区 **MainLobbyDisplay** 从 **位置** 文件夹。 单击 **分配渠道** 操作栏中的。

   ![资产](assets/single-takeover6.png)

   >[!NOTE]
   >要了解如何将渠道分配给显示，请参阅 **[渠道分配](channel-assignment.md)**.

1. 填充字段(**渠道路径**， **优先级**、和 **受支持的事件**)中的 **渠道分配** 对话框，然后单击 **保存**. 您现在已分配 **MainAdChannel** 到您的显示区。

   ![资产](assets/single-takeover7.png)

1. 选择显示区 **接管** 从 **位置** 文件夹。 单击 **分配渠道** 从操作栏中分配一次性接管渠道。

1. 要分配 **接管** 在计划时间显示，并填充以下字段 **渠道分配** 对话框，然后单击 **保存**：

   * **渠道路径**：选择接管渠道的路径
   * **优先级**：将此渠道的优先级设置为大于 **MainAdChannel**. 例如，本示例中设置的优先级为8。

      >[!NOTE]
      >优先级可以是高于正常播放渠道的优先级值的任何值。
   * **受支持的事件**：选择 **空闲屏幕** 和 **计时器**.
   * **计划**：输入您希望此渠道运行显示的计划文本。 例如，此处的文本允许在12月31日凌晨12:00到凌晨12:01之间播放内容2分钟。
此文本位于 **计划** 本示例中提到的 *12月31日23:58后及1月1日00:01前*.

      ![资产](assets/single-takeover8.png)

      导航到显示区，从 **SingleUseTakeOver** —> **位置** —> **大厅** —> **MainLobbyDisplay** 并单击 **仪表板** ，查看已分配渠道及其优先级，如下所示。

      >[!NOTE]
      >必须将接管渠道的优先级设置为最高。

      ![资产](assets/single-takeover9.png)

>[!NOTE]
>
>最佳实践是在播放后删除一次性TakeOver渠道。
