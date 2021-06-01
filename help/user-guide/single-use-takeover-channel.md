---
title: 单次使用TakeOver渠道
seo-title: 单次使用TakeOver渠道
description: 请按照此用例创建单次使用转接渠道。
seo-description: 请按照此用例创建单次使用转接渠道。
contentOwner: jsyal
feature: 创作屏幕
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 2%

---


# 单次使用TakeOver通道{#single-use-takeover-channel}

以下页面展示了一个用例，其中着重介绍了如何设置一个关于如何创建在特定时间只播放一次的“单次转接”渠道的项目。


## 用例描述 {#use-case-description}

此用例说明如何为显示屏或显示屏组创建从正常播放的渠道中&#x200B;*接管*的渠道。 收购将只发生一次，并在特定时间进行。
例如，有一个“单次接管”渠道在周五的上午9点到10点播放。 在此期间，不应播放其他频道。 在此之前和之后，单次使用接管渠道将不会播放。 以下示例显示如何创建单个接管渠道，以便播放该渠道，以便内容在12月31日凌晨12:00至凌晨12:01之前播放2分钟。

### 先决条件 {#preconditions}

在开始使用此用例之前，请确保您了解如何：

* **[创建和管理渠道](managing-channels.md)**
* **[创建和管理位置](managing-locations.md)**
* **[创建和管理计划](managing-schedules.md)**
* **[设备注册](device-registration.md)**

### 主要行为者{#primary-actors}

内容作者

## 设置项目{#setting-up-the-project}

请按照以下步骤设置项目：

**设置渠道和显示**

1. 创建标题为&#x200B;**SingleUseTakeOver**&#x200B;的AEM Screens项目，如下所示。

   ![资产](assets/single-takeover1.png)

1. 在&#x200B;**Channels**&#x200B;文件夹中创建&#x200B;**MainAdChannel**。

   ![资产](assets/single-takeover2.png)

1. 选择&#x200B;**MainAdChannel**，然后单击操作栏中的&#x200B;**编辑**。 将某些资产（图像、视频、嵌入式序列）拖放到您的渠道中。

   ![资产](assets/single-takeover2.png)


   >[!NOTE]
   >此示例中的&#x200B;**MainAdChannel**&#x200B;演示连续播放内容的序列渠道。

   ![资产](assets/single-takeover3.png)

1. 创建一个&#x200B;**TakeOver**&#x200B;渠道，该渠道接管&#x200B;**MainAdChannel**&#x200B;中的内容，并且仅在特定的日期和时间播放。

1. 选择&#x200B;**TakeOver** ，然后单击操作栏中的&#x200B;**编辑**。 将一些资产拖放到您的渠道中。 以下示例显示了添加到此渠道的单个区域图像。

   ![资产](assets/single-takeover4.png)

1. 为渠道设置位置和显示屏。 例如，为此项目设置了以下位置&#x200B;**Lobby**&#x200B;和显示&#x200B;**MainLobbyDisplay**。

   ![资产](assets/single-takeover5.png)

**将渠道分配给显示器**

1. 从&#x200B;**Locations**&#x200B;文件夹中选择显示&#x200B;**MainLobbyDisplay**。 单击操作栏中的&#x200B;**分配渠道** 。

   ![资产](assets/single-takeover6.png)

   >[!NOTE]
   >要了解如何将渠道分配给显示屏，请参阅&#x200B;**[渠道分配](channel-assignment.md)**。

1. 从“渠道分配”对话框中填充字段（**渠道路径**、**优先级**&#x200B;和&#x200B;**支持的事件**），然后单击“保存”**。******&#x200B;您现在已将&#x200B;**MainAdChannel**&#x200B;分配给显示屏。

   ![资产](assets/single-takeover7.png)

1. 从&#x200B;**Locations**&#x200B;文件夹中选择显示的&#x200B;**TakeOver**。 单击操作栏中的&#x200B;**分配渠道**&#x200B;以分配单次使用接管渠道。

1. 要在计划时间将&#x200B;**TakeOver**&#x200B;渠道分配给您的显示屏，并在&#x200B;**渠道分配**&#x200B;对话框中填充以下字段，然后单击&#x200B;**Save**:

   * **渠道路径**:选择TakeOver渠道的路径
   * **优先级**:将此渠道的优先级设置为大于 **MainAdChannel**。例如，本示例中设置的优先级为8。

      >[!NOTE]
      >优先级可以是高于正常播放渠道的优先级值的任何值。
   * **支持的事件**:选择“ **空闲** 屏幕和 **计时器**”。
   * **计划**:输入您希望此渠道运行显示的计划文本。例如，此处的文本允许内容在12月31日凌晨12:00到凌晨12:01之前播放2分钟。
本示例中提及的**Schedule**&#x200B;中的文本是&#x200B;*在12月23:58之后的31天，也在1月1日00.01*&#x200B;之前。

      ![资产](assets/single-takeover8.png)

      从&#x200B;**SingleUseTakeOver** —> **位置** —> **大堂** —> **MainLobbyDisplay**&#x200B;导航到显示屏，然后单击操作栏中的&#x200B;**功能板**&#x200B;查看分配的渠道及其优先级，如下所示。

      >[!NOTE]
      >必须将收购渠道的优先级设置为最高。

      ![资产](assets/single-takeover9.png)

>[!NOTE]
>
>播放单次使用接管渠道后，最好删除该渠道。