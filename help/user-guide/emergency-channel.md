---
title: 紧急渠道
description: 了解如何创建和管理紧急渠道，如果存在前提条件，内容作者可以从序列渠道切换紧急渠道。
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
TQID: https://experienceleague.adobe.com/v0I1gmu10jscAJFcZGWu3g7X27BUNXIuyTGfKpPwUvA
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 763
ht-degree: 1%

---

# 紧急渠道 {#emergency-channel}

## 用例说明 {#use-case-description}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

本节介绍一个用例示例。 它强调创建和管理紧急通道，内容作者可以在有前提条件的情况下从顺序通道切换紧急通道。

### 前提条件 {#preconditions}

在开始此用例之前，请确保您了解如何：

* **[创建和管理渠道](managing-channels.md)**
* **[创建和管理位置](managing-locations.md)**
* **[创建和管理计划](managing-schedules.md)**
* **[设备注册](device-registration.md)**

### 主要行为者 {#primary-actors}

内容作者

## 基本流程：设置项目 {#basic-flow-setting-up-the-project}

按照以下步骤设置紧急通道：

1. 创建一个名为&#x200B;**EmergencyChannel**&#x200B;的AEM Screens项目，如下所示。

   >[!NOTE]
   >要了解有关在AEM Screens中创建和管理项目的更多信息，请参阅创建项目。

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **创建序列频道**

   1. 单击&#x200B;**渠道**&#x200B;文件夹，然后单击&#x200B;**创建**。

   1. 单击向导中的&#x200B;**序列频道**，并创建标题为&#x200B;**MainAdChannel**&#x200B;的频道。

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **正在向序列频道添加内容**

   1. 单击频道(**MainAdChannel**)。
   1. 单击操作栏中的&#x200B;**编辑**。
   1. 将几个资产拖放到您的渠道中。

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **创建紧急频道**

   1. 单击&#x200B;**渠道**&#x200B;文件夹。
   1. 单击&#x200B;**创建**。
   1. 在向导中单击&#x200B;**顺序频道**，并创建标题为&#x200B;**紧急频道**&#x200B;的频道。

   >[!NOTE]
   >
   >通常，您的紧急渠道会添加到预先存在的生产项目中。

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **正在向紧急渠道添加内容**

   1. 单击频道（**紧急频道）**。
   1. 单击操作栏中的&#x200B;**编辑**。
   1. 将要在紧急情况下运行的资产拖放到渠道中。

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **创建位置**

   1. 导航到&#x200B;**位置**&#x200B;文件夹。
   1. 在操作栏中单击&#x200B;**创建**，然后从向导中创建标题为&#x200B;**存储**&#x200B;的位置。

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **在您的位置创建显示区**

   导航到您的位置（**商店**），然后单击操作栏中的&#x200B;**创建**。 按照该向导，创建两个标题为&#x200B;**StoreFront**&#x200B;和&#x200B;**StoreRear**&#x200B;的&#x200B;**显示区**。

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **创建计划**

   1. 导航到您的&#x200B;**计划**&#x200B;文件夹。
   1. 单击操作栏中的&#x200B;**创建**。
   1. 按照该向导，创建标题为&#x200B;**StoreSchedule**&#x200B;的计划。

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. 将两个显示区分配给您的计划和设置优先级

   1. 单击计划&#x200B;**(StoreSchedule)**，然后单击操作栏中的&#x200B;**仪表板**。

   1. 从&#x200B;**已分配渠道**&#x200B;面板中单击&#x200B;**+分配渠道**。

   1. 在&#x200B;**渠道分配**&#x200B;对话框中：

      1. 单击&#x200B;**MainAdChannel**&#x200B;的路径
      1. 将&#x200B;**优先级**&#x200B;设置为2
      1. 将支持的事件设置为&#x200B;**初始加载**&#x200B;和&#x200B;**空闲屏幕**。
      1. 单击&#x200B;**保存**

      同样，再次执行相同的步骤来分配&#x200B;**紧急通道**&#x200B;并设置其&#x200B;**优先级**。

   >[!NOTE]
   >
   >优先级用于对分配进行排序，以防多个分配符合播放标准。 值最高的总是优先于较低的值。

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. 从&#x200B;**已分配渠道**&#x200B;面板中单击&#x200B;**+分配渠道**。

1. 在&#x200B;**渠道分配**&#x200B;对话框中：

   1. 单击&#x200B;**紧急渠道**&#x200B;的路径
   1. 将&#x200B;**优先级**&#x200B;设置为1

   1. 将支持的事件设置为&#x200B;**初始加载**、**空闲屏幕**&#x200B;和&#x200B;**用户交互**

   1. 单击&#x200B;**保存**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   您可以从&#x200B;**StoreSchedule**&#x200B;仪表板查看分配的渠道。

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **为每个显示区分配计划**

   1. 导航到每个显示区，如&#x200B;**EmergencyChannel** > **位置** > **商店** >**商店前台**。

   1. 单击操作栏中的&#x200B;**仪表板**。
   1. 从&#x200B;**分配的渠道和计划**&#x200B;面板中单击&#x200B;**...**，然后单击&#x200B;**+分配计划**。

   1. 单击计划的路径（例如，此处，**EmergencyChannel** > **计划** >**存储计划**）。

   1. 单击&#x200B;**保存**。

   您可以从&#x200B;**StoreSchedule**&#x200B;仪表板查看分配给显示区的计划。
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **设备注册**

   完成设备注册过程。 注册后，您可以在AEM Screens Player上查看以下输出。

   ![new30](assets/new30.gif)

## 切换到紧急频道 {#switching-to-emergency-channel}

如果出现紧急情况，请执行以下步骤：

1. 导航到&#x200B;**EmergencyChannel** > **计划** > **存储计划**，然后单击操作栏中的&#x200B;**仪表板**。

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. 从&#x200B;**StoreSchedule**&#x200B;仪表板中单击&#x200B;**EmergencyChannel**，然后单击&#x200B;**编辑分配**。

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. 从&#x200B;**渠道分配**&#x200B;对话框将&#x200B;**EmergencyChannel**&#x200B;的&#x200B;**优先级**&#x200B;更新为&#x200B;**3**，然后单击&#x200B;**保存**。

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. 更新渠道优先级后，所有AEM Screens播放器都会显示&#x200B;**EmergencyChannel**&#x200B;内容。

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### 结论 {#conclusion}

**EmergencyChannel**&#x200B;继续显示其内容，直到内容作者将优先级值重置为1。

当内容作者收到紧急情况已清除的指示时，他们应更新&#x200B;**MainAdChannel**&#x200B;的优先级。 这样做会导致恢复正常播放。

