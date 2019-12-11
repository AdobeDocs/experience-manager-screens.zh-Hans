---
title: 紧急通道
seo-title: 紧急通道
description: 按照此用例示例，了解如何创建和管理紧急渠道，内容作者可以在先决条件的情况下从序列渠道进行切换。
seo-description: 按照此用例示例，了解如何创建和管理紧急渠道，内容作者可以在先决条件的情况下从序列渠道进行切换。
uuid: 612917c9-a832-453b-970c-f4365f7b105d
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: dbb4fae6-f3fb-496a-9bd6-1151e2862b5b
docset: aem65
translation-type: tm+mt
source-git-commit: 2708464222321fd138c986f19d8572c71f1dae75

---


# 紧急通道 {#emergency-channel}

## 用例描述 {#use-case-description}

本节描述了一个用例示例，该示例强调了如何创建和管理紧急渠道，内容作者可以在先决条件的情况下从序列渠道进行切换。

### 先决条件 {#preconditions}

在开始此使用案例之前，请确保您了解如何：

* **[创建和管理渠道](managing-channels.md)**
* **[创建和管理位置](managing-locations.md)**
* **[创建和管理计划](managing-schedules.md)**
* **[设备注册](device-registration.md)**

### 主要演员 {#primary-actors}

内容作者

## 基本流程：设置项目 {#basic-flow-setting-up-the-project}

请按照以下步骤设置紧急渠道：

1. 创建一个名为 **EmergencyChannel的AEM Screens项目**，如下所示。

   >[!NOTE]
   >
   >要了解有关在AEM Screens中创建和管理项目的更多信息，请参阅创建项目。

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **创建序列渠道**

   1. 选择渠 **道文件夹** ，然后单 **击创建** ，打开向导以创建渠道。

   1. 从向 **导中选择序列渠道** ，然后创建标题为MainAdChannel **的渠道**。
   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **将内容添加到序列渠道**

   1. 选择渠道(**MainAdChannel**)。
   1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。将少量资源拖放到您的渠道。
   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **创建紧急渠道**

   1. 选择渠 **道文** 件夹。
   1. 单击创 **建** ，打开向导以创建渠道。
   1. 从向 **导中选择序列渠道** ，然后创建标题为ExerencyChannel的 **渠道**。
   >[!NOTE]
   >
   >通常情况下，您的紧急渠道会添加到您的预先存在的生产项目中。

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **将内容添加到紧急渠道**

   1. 选择渠道(紧&#x200B;**急渠道)**。
   1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。将要在紧急情况下运行的资产拖放到渠道中。
   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **创建位置**

   1. 导航到位 **置文** 件夹。
   1. 单击 **操作栏中的** “创建”，然后从向导中创建标题为“ **Store** ”的位置。
   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **在您的位置创建显示屏**

   导航到您的位置(**商店**)，然后单 **击操作栏中的** “创建”。 按照向导的说明创建两个标 **题为** StoreFront **和** StoreRear的显示屏 ****。

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **创建计划**

   1. 导航到您的“计 **划** ”文件夹。
   1. 单击操作栏中的&#x200B;**创建**。按照向导创建标题为StoreSchedule的 **计划**。
   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. 将显示分配给您的计划并设置优先级

   1. 选择计划( **StoreSchedule)** ，然后单 **击操作栏中的Dashboard** 。

   1. 从“已 **分配的渠道** ”面板中单 **击+分配渠道** 。

   1. 从“渠道 **分配** ”对话框中：

      1. 选择MainAdChannel的路 **径**
      1. 将优先级 **设置为** 2
      1. Set the Supported Events as **Initial Load** and **Idle Screen**.
      1. Click **Save**
      同样，您也必须再次执行相同的步骤来分配 **ExercyChannel** 并设置其 **优先级**。
   >[!NOTE]
   >
   >优先级用于在多个分配匹配播放条件时对分配进行排序。具有最高值的分配将始终优先于具有较低值的分配。

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. 从“已 **分配的渠道** ”面板中单 **击+分配渠道** 。

1. 从“渠道 **分配** ”对话框中：

   1. 选择ExercyChannel的路 **径**
   1. 将优 **先级** 设置为1

   1. 将支持的事件设置为 **初始加载**、 **空闲屏幕**&#x200B;和用 **户交互**

   1. Click **Save**
   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   您可以从StoreSchedule功能板查看分配 **的渠道** 。

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **将计划分配给每个显示屏**

   1. 导航到每个显示屏，如 **Channel** —&gt;位置 **—&gt;** Store **—&gt;** StoreFront紧急调&#x200B;****&#x200B;用。

   1. Click **Dashboard** from the action to open the display dashboard.
   1. **单击**...从“已分 **配的渠道和计划** ”面板，然后单击 **+分配计划**。

   1. 选择计划的路径(例如，此处， **EmergencyChannel** —&gt;计划 **—&gt;** StoreSchedule ****)。

   1. 单击&#x200B;**保存**。
   您可以从StoreSchedule功能板查看分配到显示屏的 **计划** 。
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **设备注册**

   完成设备注册过程，注册后，您将在AEM Screens播放器上查看以下输出。

   ![new30](assets/new30.gif)

## 切换到紧急通道 {#switching-to-emergency-channel}

在发生紧急情况时，请执行以下步骤：

1. 导航到 **EmergencyChannel** —&gt;计划 **—&gt;** StoreSchedule **，然后从操作栏****** 中选择控制板。

   ![screen_shot_2019-02-25at10112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. 从StoreSchedule功能 **板中选择ExercyChannel** ，然后单 **击“编** 辑分配” ****。

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. 将EmergencyChannel的 **Priority** (优先级 **)从“Assignment Channel Assignment”(渠道分配** )对话框 **和Click channel的Saved（单击）中更新** 为 **3******。

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. 一旦更新了渠道的优先级，所有AEM Screens播放器都将显示 **EmergencyChannel** ，如下所示。

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### 结论 {#conclusion}

在内 **容作者将优先级值重置为1之前** ,EmergencyChannel将继续显示其内容。

内容作者收到紧急情况已清除的说明后，应更新 **MainAdChannel的优先级** ，这会导致正常播放恢复。
