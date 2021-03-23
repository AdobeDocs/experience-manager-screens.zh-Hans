---
title: 紧急渠道
seo-title: 紧急渠道
description: 请按照此用例示例了解如何创建和管理紧急渠道，内容作者可以在先决条件情况下从序列渠道切换该紧急。
seo-description: 请按照此用例示例了解如何创建和管理紧急渠道，内容作者可以在先决条件情况下从序列渠道切换该紧急。
uuid: 612917c9-a832-453b-970c-f4365f7b105d
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: dbb4fae6-f3fb-496a-9bd6-1151e2862b5b
docset: aem65
feature: 创作屏幕
role: 管理员、开发人员
level: 中间
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 8%

---


# 紧急渠道{#emergency-channel}

## 用例描述 {#use-case-description}

本节介绍一个用例示例，该示例强调了如何创建和管理紧急渠道，内容作者可以在先决条件情况下从序列渠道切换该紧急。

### 先决条件{#preconditions}

在开始此用例之前，请确保您了解如何：

* **[创建和管理渠道](managing-channels.md)**
* **[创建和管理位置](managing-locations.md)**
* **[创建和管理计划](managing-schedules.md)**
* **[设备注册](device-registration.md)**

### 主要操作者{#primary-actors}

内容作者

## 基本流程：设置项目{#basic-flow-setting-up-the-project}

请按照以下步骤设置紧急渠道:

1. 创建名为&#x200B;**EmergencyChannel**&#x200B;的AEM Screens项目，如下所示。

   >[!NOTE]
   >要了解有关在AEM Screens中创建和管理项目的更多信息，请参阅创建项目。

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **创建序列渠道**

   1. 选择&#x200B;**渠道**&#x200B;文件夹，然后单击&#x200B;**创建**&#x200B;以打开向导以创建渠道。

   1. 从向导中选择&#x200B;**序列渠道**&#x200B;并创建标题为&#x200B;**MainAdChannel**&#x200B;的渠道。

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **将内容添加到序列渠道**

   1. 选择渠道(**MainAdChannel**)。
   1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。将少量资源拖放到您的渠道。

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **创建紧急渠道**

   1. 选择&#x200B;**渠道**&#x200B;文件夹。
   1. 单击&#x200B;**创建**&#x200B;以打开向导以创建渠道。
   1. 从向导中选择&#x200B;**序列渠道**&#x200B;并创建标题为&#x200B;**EmergentChannel**&#x200B;的渠道。

   >[!NOTE]
   >
   >通常，您的紧急渠道会添加到您预先存在的生产项目中。

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **将内容添加到紧急渠道**

   1. 选择渠道(**紧急渠道)**。
   1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。将您要在紧急情况下运行的资产拖放到您的渠道。

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **创建位置**

   1. 导航到&#x200B;**位置**&#x200B;文件夹。
   1. 单击操作栏中的&#x200B;**创建**，然后从向导中创建标题为&#x200B;**存储**&#x200B;的位置。

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **在您的位置创建显示屏**

   导航到您的位置(**Store**)，然后单击操作栏中的&#x200B;**创建**。 按照向导创建两个标题为&#x200B;**StoreFront**&#x200B;和&#x200B;**StoreRear**&#x200B;的&#x200B;**Displays**。

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **创建计划**

   1. 导航到&#x200B;**计划**&#x200B;文件夹。
   1. 单击操作栏中的&#x200B;**创建**。按照向导创建标题为&#x200B;**StoreSchedule**&#x200B;的计划。

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. 将显示内容分配给计划并设置优先级

   1. 选择计划&#x200B;**(StoreSchedule)**，然后单击操作栏中的&#x200B;**仪表板**。

   1. 单击&#x200B;**ASSIGNED渠道**&#x200B;面板中的&#x200B;**+分配渠道**。

   1. 在&#x200B;**渠道分配**&#x200B;对话框中：

      1. 选择&#x200B;**MainAdChannel**&#x200B;的路径
      1. 将&#x200B;**优先级**&#x200B;设置为2
      1. 将支持的事件设置为&#x200B;**初始负载**&#x200B;和&#x200B;**空闲屏幕**。
      1. 单击&#x200B;**保存**

      同样，您也必须再次执行相同的步骤，以分配&#x200B;**EmergencyChannel**&#x200B;并设置其&#x200B;**Priority**。
   >[!NOTE]
   >
   >优先级用于在多个分配匹配播放条件时对分配进行排序。具有最高值的分配将始终优先于具有较低值的分配。

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. 单击&#x200B;**ASSIGNED渠道**&#x200B;面板中的&#x200B;**+分配渠道**。

1. 在&#x200B;**渠道分配**&#x200B;对话框中：

   1. 选择&#x200B;**EmergentChannel**&#x200B;的路径
   1. 将&#x200B;**优先级**&#x200B;设置为1

   1. 将支持的事件设置为&#x200B;**初始加载**、**空闲屏幕**&#x200B;和&#x200B;**用户交互**

   1. 单击&#x200B;**保存**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   您可以从&#x200B;**StoreSchedule**&#x200B;视图中仪表板分配的渠道。

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **将计划分配给每个显示屏**

   1. 导航到每个显示屏，如&#x200B;**EmergencyChannel** —> **位置** —> **存储** —>**StoreFront**。

   1. 单击操作中的&#x200B;**仪表板**&#x200B;以打开显示仪表板。
   1. 单击&#x200B;**...**&#x200B;从&#x200B;**“已指定渠道和计划”**&#x200B;面板中，进一步单击&#x200B;**+“已指定计划”**。

   1. 选择计划的路径(例如，此处&#x200B;**EmergencyChannel** —> **计划** —>**StoreSchedule**)。

   1. 单击&#x200B;**保存**。

   您可以从&#x200B;**StoreSchedule**视图将分配的计划仪表板到显示屏。
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **设备注册**

   完成设备注册过程，注册后，您将在AEM Screens播放器上视图以下输出。

   ![new30](assets/new30.gif)

## 切换到紧急渠道{#switching-to-emergency-channel}

在紧急事件中，执行以下步骤：

1. 导航到&#x200B;**EmergencyChannel** —> **计划** —> **StoreSchedule**&#x200B;并从操作栏中选择&#x200B;**仪表板**。

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. 从&#x200B;**StoreSchedule**&#x200B;仪表板中选择&#x200B;**EmergencyChannel**，然后单击&#x200B;**编辑分配**。

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. 将&#x200B;**EmergencyChannel**&#x200B;的&#x200B;**Priority**&#x200B;从&#x200B;**渠道分配**&#x200B;对话框更新为&#x200B;**3**，然后单击&#x200B;**保存**。

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. 更新渠道的优先级后，所有AEM Screens播放器都将显示&#x200B;**EmergentChannel**&#x200B;内容，如下所示。

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### 结论{#conclusion}

**EmergentChannel**&#x200B;将继续显示其内容，直到内容作者将优先级值重置为1。

内容作者收到已清除紧急情况的指示后，应更新&#x200B;**MainAdChannel**&#x200B;的优先级，这会导致正常播放恢复。
