---
title: 频道级别激活——单个事件播放
seo-title: 频道级别激活——单个事件播放
description: 按照本指南，了解使用单个事件回放的频道级别激活。
seo-description: 按照本指南，了解使用单个事件回放的频道级别激活。
uuid: 87230344-5f9a-42a4-a7a8-ae4203303612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: c28fd669-f23e-4d53-bec1-a2911274567d
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 频道级别激活——单个事件播放 {#channel-level-activation-single-event-playback}

使用渠道级别激活涵盖以下主题：

* 概述
* 将频道级别激活用作单个事件回放

## 概述 {#overview}

***“渠道级别激活*** ”允许渠道在特定设置的计划后进行切换。 单个事件渠道在设置的计划后替换主渠道并在特定时间内播放，直到主渠道再次播放其内容。

以下示例重点介绍以下关键术语，从而提供解决方案：

* 全 ***局序列的主序列*** -通道
* 一 ***个事件渠道*** ，在设定时间只运行一次
* 在 ***主序列频道内发生的单个播放事件的设置计划和优先级***

## 使用渠道级别激活 {#using-channel-level-activation}

以下部分介绍如何为AEM Screens项目在渠道内创建单个事件回放。

### 前提条件 {#prerequisites}

在开始实施此功能之前，请确保您已准备好以下入门项目以开始实施渠道级别激活：

* 创建AEM Screens项目，在此示例中为渠道级 **别激活**

* 在“渠道”文件夹下 **创建渠道** ，作 **为MainAdChannel**

* 在“渠道”文件夹下 **创建另一个渠道** ，作 **为TargetedSinglePlay**

* 将相关资产添加到两个渠道

下图显示了MainAdChannel **和** TargetedSinglePlay渠道中包含MainAdChannel和TargetedSinglePlay **Channels文件夹的********** 渠道级别激活项目。

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>有关如何创建项目以及如何创建序列渠道的其他信息，请参阅以下资源：
>
>* [创建和管理项目](creating-a-screens-project.md)
   >
   >
* [管理渠道](managing-channels.md)
>



### 实施 {#implementation}

在AEM Screens项目中实施渠道级别激活涉及三项主要任务：

1. **设置项目分类，包括渠道、位置和显示**
1. **将渠道分配到显示**
1. **设置计划和优先级**

请按照以下步骤实现该功能：

1. **创建位置**

   导航到AEM Screens项 **目中的** Locations文件夹，然后创建一个位置作为 **Region**。

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >要了解如何创建位置，请参阅创 **[建和管理位置](managing-locations.md)**。

1. **在位置下创建显示**

   1. 导航到渠 **道级别激活** &gt;位 **置** &gt;区 **域**。
   1. 选择 **区域** ，然后单击操 **作栏中的** +创建。
   1. 从向 **导中选择** “显示”，然后创建标题为RegionDisplay的 **显示。**
   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **分配要显示的渠道**

   对于 **MainAdChannel:**

   1. 导航到渠道 **级别激活** &gt; &gt; **位置** &gt; **区域** &gt;区域单击 ******** 操作中的显示和分配渠道分配。
   1. **“渠道分配** ”对话框打开。
   1. Select **Reference Channel**.. by path.
   1. 选择渠道 **路径** “渠道 **级别激活”** —&gt;“渠道 ***”—*********&gt;MainChannelAdChannel。
   1. 渠 **道角色将填充** ，作为 **主渠道**。
   1. 选择优 **先级** , **为1**。
   1. Select the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. 单击&#x200B;**保存**。
   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >您还可以通过以下方式从显示控制板中分配 **渠道** ：渠道级别激活 **—&gt;位置** —&gt;位置 **—&gt;区域—********** &gt;显示区域显示从操作中导航到操作栏的单击和DisplayDashboardDashboard。 从“已 **分配的渠道和计划** ”面板 **中单击+分配渠道** 。

   同样，为显示屏 **分配渠道TargetedSinglePlay** **:

   1. 导航到渠 **道级别激活** —&gt;位 **置** —&gt;位置 **—&gt;** 区域 ******** — Region Display bar单击操作中的Channel Assign Assign From the action。
   1. **“渠道分配** ”对话框打开。
   1. Select **Reference Channel**.. by path.
   1. 选择渠 **道路径** ，作 **为渠道级别激活*** —&gt;渠道 ***—*********&gt;目标SinglePlay Reactive。
   1. 渠道 **角色将填充** ，作为目 **标单独播放**。
   1. 将“优 **先级** ”设置为 **2**。
   1. 选择“支 **持的事件** ”, **如**“初始加载”、“空闲屏幕 **”和“******&#x200B;计时器”*，如下图所示。
   1. 选择有效日期， **从** 2018年11月27日晚11:59开始， **到2018年11月** 28日上午12:05结束。
   1. 单击&#x200B;**保存**。
   >[!CAUTION]
   您必须将 **TargetedSinglePlay渠道的优先级设置为高于** MainAdSegment渠道 **** 。

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   要选择同一天，您必须选择第二天，然后手动编辑日期至同一天，但以后再编辑。 这会限制用户选择过去的日期。 请参阅以下示例：

   ![new1](assets/new1.gif)

## 查看结果 {#viewing-the-results}

为渠道和显示完成设置后，请启动AEM Screens播放器以查看内容。

播放器显示 **MainAdChannel的内容，并且正好在晚上11:59（如计划中所设定）,** TargetedSinglePlay **频道将显示其内容，直至凌晨12:05，然后****** MainAdChannel将再次恢复播放其内容。

>[!NOTE]
要了解AEM Screen Player，请参阅以下资源：
* [AEM Screens播放器下载](https://download.macromedia.com/screens/)
* [使用AEM Screens播放器](working-with-screens-player.md)
