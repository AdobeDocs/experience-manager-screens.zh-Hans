---
title: 创建和管理Live Copy
seo-title: 管理 Live Copy
description: 本页介绍了如何创建和管理渠道的 Live Copy。
seo-description: 可查看本页以创建渠道的 Live Copy、查看属性、检查状态，以及将渠道中的更改传播到其 Live Copy。
uuid: 78ec7219-95ab-44d1-9514-1b97aded5bf4
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 84085a03-1798-4f1d-858c-6014a3f6aff6
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 创建和管理Live Copy {#creating-and-managing-a-live-copy}

本页介绍了如何创建和管理渠道的 Live Copy。

A ***Live Copy*** is a copy of specific site content for which a live relationship with the original source is maintained. 此Live关系允许Live copy从源继承内容和页面属性。

本页介绍了如何创建渠道的 Live Copy、查看属性、检查状态，以及将渠道中的更改传播到其 Live Copy。


## 创建 Live Copy {#creating-a-live-copy}

请按照以下步骤在项目文件夹中创建渠道的 Live Copy。

1. 选择 Adobe Experience Manager 链接（左上方），然后选择&#x200B;**屏幕**。Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.

1. Navigate to Screens project and click **Channels**.
1. Click **Create** and select **Live Copy** to create a live copy of the channel.

1. 选择目标，然后单击&#x200B;**下一步**。
1. 选择将存放 Live Copy 的位置。
1. 在&#x200B;**创建 Live Copy** 页面中输入&#x200B;**标题**&#x200B;和&#x200B;**名称**。

1. 单击&#x200B;**打开**&#x200B;以查看新 Live Copy 的内容，或单击&#x200B;**完成**&#x200B;以返回主页。

或者，请查看下面以可视化形式显示的有关创建渠道的新 Live Copy 的步骤。

The following example shows the creation of a live copy (***IdleLiveCopy***) for ***Idle Channel*** with destination folder as ***Channels***.

![chlimage_1-2](assets/chlimage_1-2.gif)

## 查看 Live Copy 渠道的内容 {#viewing-content-of-the-live-copy-channel}

Live Copy 是已存在的渠道的副本。

要查看您的 Live Copy 内容，请执行以下步骤：

1. 导航到 Screens 项目，然后单击您最初创建 Live Copy 的位置，如上面的部分所示。(Here, the location was chosen as **Channels** folder)

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. 单击操作栏中的&#x200B;**编辑**&#x200B;以查看渠道中的内容。

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >查看 Live Copy 渠道的内容时，您将在菜单中看到一个额外的项目 **Live Copy 状态**。有关更多详细信息，请参阅以下部分。

### 查看 Live Copy 的属性 {#viewing-properties-of-a-live-copy}

您还可以查看 Live Copy 渠道的属性。

1. 导航到您的 Live Copy 渠道，然后单击操作栏中的&#x200B;**属性**。

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. 选择 **Live Copy** 选项卡以查看渠道的详细信息。

   ![chlimage_1-21](assets/chlimage_1-21.png)

### Live Copy 状态 {#live-copy-status}

通过模式** Live copy状态**（如下图所示），可以查看渠道中所有资产的关系状态。

1. Click **Edit** to choose the **Live Copy Status** and view the association of your channel content to the original channel (from which the live copy is generated).

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. 选择 **Live Copy 状态**&#x200B;以显示预览页面。

   所有具有绿色边框的资源均表示内容是从原始渠道继承的。

   ![chlimage_1-23](assets/chlimage_1-23.png)

### 中断继承 {#breaking-the-inheritance}

您也可以从 Live Copy 中取消继承，以使内容变得与原始分支无关。

如以下示例所示，您可以在编辑模式下选择图像，然后单击右上方的取消继承符号。

![chlimage_1-24](assets/chlimage_1-24.png)

### 将更改传播到 Live Copy 渠道 {#propagating-changes-to-the-live-copy-channel}

如果您在原始渠道中进行了更改/更新，您需要也将这些更改传播到 Live Copy 渠道。

请按照以下步骤确保您的更改会从原始渠道传播到 Live Copy 渠道：

1. 选择原始渠道 (***Idle Channel***)，然后单击操作栏中的&#x200B;**编辑**。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 对此渠道内容进行编辑。例如，从此渠道中删除一个图像。

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. 选择此渠道的 Live Copy (***IdleLiveCopy***)，然后单击操作栏中的&#x200B;**编辑**。此时您将注意到已删除的图像仍显示在 Live Copy 中。

   为了传播更改，您需要同步渠道。

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. 要将更改传播到 Live Copy 渠道，请导航到 AEM 功能板并选择 Live Copy 渠道，然后单击操作栏中的&#x200B;**属性**。

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. 选择 **Live Copy** 选项卡，然后单击操作栏中的&#x200B;**同步**。

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. 单击&#x200B;**同步**&#x200B;以确认所做的更改。Click **Save &amp; Close** to navigate back to the AEM dashboard..

   ![chlimage_1-30](assets/chlimage_1-30.png)

   此时您将注意到图像现在也已从 Live Copy 渠道中删除。
