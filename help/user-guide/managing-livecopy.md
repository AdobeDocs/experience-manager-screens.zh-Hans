---
title: 创建和管理Live Copy
seo-title: Managing LiveCopy
description: 本页介绍如何创建和管理渠道的实时副本。
seo-description: Follow this page to create live copy of a channel, view properties, check status, and propagate changes from a channel to its live copy.
uuid: 78ec7219-95ab-44d1-9514-1b97aded5bf4
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 84085a03-1798-4f1d-858c-6014a3f6aff6
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 4a4b3a83-2b02-42a0-86a7-fce6bbf47c7d
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 1%

---

# 创建和管理Live Copy {#creating-and-managing-a-live-copy}

本页介绍如何创建和管理渠道的实时副本。

A ***Live Copy*** 是特定站点内容的副本，其中与原始源保持实时关系。 此Live关系允许Live Copy从源继承内容和页面属性。

本页介绍如何创建渠道的Live Copy、查看属性、检查状态以及将更改从渠道传播到其Live Copy。


## 创建 Live Copy {#creating-a-live-copy}

执行以下步骤，在您的项目文件夹中创建渠道的Live Copy。

1. 选择Adobe Experience Manager链接（左上方），然后 **Screens**. 或者，您可以直接转到： `http://localhost:4502/screens.html/content/screens`.

1. 导航到屏幕项目并单击 **渠道**.
1. 单击 **创建** 并选择 **Live Copy** 以创建渠道的Live Copy。

1. 选择目标并单击 **下一个**.
1. 选择Live Copy将驻留的位置。
1. 输入 **标题** 和 **名称** 在 **创建Live Copy** 页面。

1. 单击 **打开** 查看新Live Copy的内容或 **完成** 以返回到主页。

或者，请参阅以下步骤以了解用于创建渠道的新Live Copy的可视化表示法。

以下示例显示了Live Copy的创建(***IdleliveCopy***)表示 ***空闲频道*** 目标文件夹为 ***渠道***.

![chlimage_1-2](assets/chlimage_1-2.gif)

## 查看Live Copy渠道的内容 {#viewing-content-of-the-live-copy-channel}

Live Copy是已存在渠道的副本。

要查看Live Copy的内容，请参阅以下步骤：

1. 导航到屏幕项目，然后单击最初创建Live Copy的位置，如上面的部分所示。 (在本例中，选择位置为 **渠道** 文件夹)

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. 单击 **编辑** 操作栏中的内容，以查看渠道中的内容。

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >在查看Live Copy渠道的内容时，您将在菜单中以 **Live Copy状态**. 有关更多详细信息，请参阅以下部分。

### 查看Live Copy的属性 {#viewing-properties-of-a-live-copy}

此外，您还可以查看Live Copy渠道的属性。

1. 导航到您的Live Copy渠道并单击 **属性** 操作栏中的。

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. 选择 **Live Copy** 选项卡以查看渠道的详细信息。

   ![chlimage_1-21](assets/chlimage_1-21.png)

### Live Copy 状态 {#live-copy-status}

模式 **Live Copy状态**&#x200B;如下图所示，允许您查看渠道中所有资产的关系状态。

1. 单击 **编辑** 以选择 **Live Copy状态** 和查看渠道内容与原始渠道（生成Live Copy的渠道）的关联。

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. 选择 **Live Copy状态** 以显示预览页面。

   所有带绿色边框的资源均显示内容继承自原始渠道。

   ![chlimage_1-23](assets/chlimage_1-23.png)

### 中断继承 {#breaking-the-inheritance}

您还可以取消来自LiveCopy的继承，以便内容独立于原始分支。

以下示例显示您在编辑模式下选择图像，然后单击右上角的取消继承符号。

![chlimage_1-24](assets/chlimage_1-24.png)

### 将更改传播到Live Copy渠道 {#propagating-changes-to-the-live-copy-channel}

如果您在原始渠道中进行更改/更新，则还需要将这些更改传播到Live Copy渠道。

请按照以下步骤操作，以确保将更改从原始渠道传播到Live Copy渠道：

1. 选择原始渠道(***空闲频道***)，然后单击 **编辑** 操作栏中的。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 对此渠道内容进行编辑。 例如，从此渠道中删除图像。

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. 选择渠道的Live Copy (***IdleliveCopy***)，然后单击 **编辑** 操作栏中的。 您会注意到删除的图像在Live Copy中仍然可见。

   为了传播更改，您需要同步渠道。

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. 要将更改传播到Live Copy渠道，请导航到AEM功能板，选择Live Copy渠道并单击 **属性** 操作栏中的。

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. 选择 **Live Copy** 选项卡，然后单击 **同步** 操作栏中的。

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. 单击 **同步** 以确认更改。 单击 **保存并关闭** 导航回AEM功能板。

   ![chlimage_1-30](assets/chlimage_1-30.png)

   您会注意到图像现在也从Live Copy渠道中删除。
