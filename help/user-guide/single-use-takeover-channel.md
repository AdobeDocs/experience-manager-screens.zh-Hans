---
title: 一次性使用接管渠道
seo-title: 一次性使用接管渠道
description: 按照此用例创建单次使用接管渠道。
seo-description: 按照此用例创建单次使用接管渠道。
contentOwner: jsyal
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 2%

---


# 单次使用接管渠道{#single-use-takeover-channel}

下面的页面展示了一个用例，其中强调了如何设置一个项目，以便创建在特定时间仅播放一次的“一次取出”渠道。


## 用例描述 {#use-case-description}

此用例说明如何为显示屏或显示屏组创建从正常播放渠道&#x200B;*接管*的渠道。 收购将仅发生一次，并且只在特定时间进行。
例如，有一个“单次接管”渠道在星期五从上午9点到上午10点播放。 在此期间，不应播放其他渠道。 在此之前和之后，将不会播放单次使用接管渠道。 以下示例展示了如何创建一个播放的接管渠道，允许内容在12月31日上午12:00至凌晨12:01之前播放2分钟。

### 先决条件{#preconditions}

在开始此用例之前，请确保您了解如何：

* **[创建和管理渠道](managing-channels.md)**
* **[创建和管理位置](managing-locations.md)**
* **[创建和管理计划](managing-schedules.md)**
* **[设备注册](device-registration.md)**

### 主要操作者{#primary-actors}

内容作者

## 设置项目{#setting-up-the-project}

请按照以下步骤设置项目：

**设置渠道和显示**

1. 创建标题为&#x200B;**SingleUseTakeOver**&#x200B;的AEM Screens项目，如下所示。

   ![资产](assets/single-takeover1.png)

1. 在&#x200B;**渠道**&#x200B;文件夹中创建&#x200B;**MainAdChannel**。

   ![资产](assets/single-takeover2.png)

1. 选择&#x200B;**MainAdChannel**&#x200B;并单击操作栏中的&#x200B;**编辑**。 将某些资产（图像、视频、嵌入式序列）拖放到您的渠道。

   ![资产](assets/single-takeover2.png)


   >[!NOTE]
   >此示例中的&#x200B;**MainAdChannel**&#x200B;演示了连续播放内容的序列渠道。

   ![资产](assets/single-takeover3.png)

1. 创建一个&#x200B;**TakeOver**&#x200B;渠道，它接管&#x200B;**MainAdChannel**&#x200B;中的内容，并且仅在特定日期和时间播放。

1. 选择&#x200B;**TakeOver**&#x200B;并单击操作栏中的&#x200B;**编辑**。 将一些资产拖放到您的渠道。 下面的示例展示添加到此渠道的单个区域图像。

   ![资产](assets/single-takeover4.png)

1. 为渠道设置位置和显示。 例如，为此项目设置了以下位置&#x200B;**Lobby**&#x200B;和display **MainLobbyDisplay**。

   ![资产](assets/single-takeover5.png)

**将渠道分配给显示屏**

1. 从&#x200B;**Locations**&#x200B;文件夹中选择显示&#x200B;**MainLobbyDisplay**。 单击操作栏中的&#x200B;**指定渠道**。

   ![资产](assets/single-takeover6.png)

   >[!NOTE]
   >要了解如何将渠道分配给显示屏，请参阅&#x200B;**[渠道分配](channel-assignment.md)**。

1. 从“渠道分配”(**A7/>)对话框填充字段(**&#x200B;渠道路径&#x200B;**、** Priority **和**&#x200B;支持的事件&#x200B;**)，然后单击“保存”(** Save **)。**&#x200B;您现在已将&#x200B;**MainAdChannel**&#x200B;分配给您的显示屏。

   ![资产](assets/single-takeover7.png)

1. 从&#x200B;**位置**&#x200B;文件夹中选择显示屏&#x200B;**TakeOver**。 单击操作栏中的&#x200B;**指定渠道**&#x200B;以指定单次使用接管通道。

1. 要在计划时间将&#x200B;**TakeOver**&#x200B;渠道分配给您的显示屏，并在&#x200B;**渠道分配**&#x200B;对话框中填充以下字段，然后单击&#x200B;**保存**:

   * **渠道路径**:选择“接管”渠道的路径
   * **优先级**:将此渠道的优先级设置为大于 **MainAdChannel**。例如，本例中设置的优先级为8。

      >[!NOTE]
      >优先级可以是高于正常播放渠道的优先级值的任何值。
   * **支持的事件**:选择“ **空闲** 屏幕和 **计时器**”。
   * **计划**:输入希望此计划运行显示的渠道的文本。例如，此处的文本允许内容在12月31日半夜12:00之前播放2分钟，直到凌晨12:01。
本例中提到的**计划**&#x200B;中的文本为&#x200B;*，是12月23日之后的31天，也是00.01*&#x200B;之前的1月1日。

      ![资产](assets/single-takeover8.png)

      从&#x200B;**SingleUseTakeOver** —> **位置** —> **Lobby** —> **MainLobbyDisplay**&#x200B;导航到显示屏，然后单击操作栏中的&#x200B;**仪表板**&#x200B;以视图分配的渠道优先事项，如下所示。

      >[!NOTE]
      >必须将收购渠道的优先级设置为最高。

      ![资产](assets/single-takeover9.png)

>[!NOTE]
>
>播放“一次性使用接管”渠道后，最好删除它。