---
title: 使用体验片段
description: 了解如何在AEM Screens中使用体验片段。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Experience Fragments
role: Admin, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 1%

---

# 使用体验片段 {#using-experience-fragments}

本页涵盖以下主题：

* **概述**
* **在AEM Screens中使用体验片段**
* **将更改传播到页面**

## 概述 {#overview}

An ***体验片段*** 是一个或多个组件的组，这些组件包括可在页面中引用的内容和布局。 体验片段可以包含任何组件，例如一个或多个组件，这些组件可以包含段落系统中被引用到完整体验或由第三个端点请求的任何内容。


## 在AEM Screens中使用体验片段 {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>以下示例使用 **`We.Retail`** 作为演示项目，从中应用体验片段 **站点** 页面到AEM Screens项目。

例如，以下工作流演示了如何使用中的体验片段 `We.Retail` 在Sites中。 您可以选择网页，并在某个项目的AEM Screens渠道中使用该内容。

### 先决条件 {#pre-requisites}

**使用渠道创建演示项目**

***创建项目***

1. 要创建项目，请单击 **创建屏幕项目**.
1. 输入标题为 **演示项目**.
1. 单击&#x200B;**保存**。

A **演示项目** 会添加到您的AEM Screens。

***创建渠道***

1. 导航至 **演示项目** 您已创建，然后单击 **渠道** 文件夹。

1. 单击 **创建** 以打开向导。
1. 选择 **序列渠道** 模板并单击 **下一个**.

1. 输入 **标题** 作为 **TestChannel** 并单击 **创建**.

A **TestChannel** 已添加到您的 **演示项目**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### 创建体验片段 {#creating-an-experience-fragment}

请按照以下步骤应用中的内容 **`We.Retail`** 敬您的 **TestChannel** 在 **演示项目**.

1. **导航到We.Retail中的“站点”页面**

   1. 导航到站点并单击 **`We.Retail`** > **美国** > **英语** > **设备** 并点击此页面，以便将其用作Screens渠道的体验片段。

   1. 单击 **编辑** 从操作栏中，以打开要用作屏幕渠道体验片段的页面。

1. **重用内容**

   1. 单击要包含在渠道中的片段。
   1. 单击右侧的最后一个图标，以打开 **转换为体验片段** 对话框。

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **创建体验片段**

   1. 选择 **操作** 作为 **创建新的体验片段**.

   1. 单击 **父级路径**.
   1. 单击 **模板**. 选择 **体验片段 — 屏幕变量** 此处为模板（字段中的值） `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`)。

   1. 输入 **片段标题** 作为 **Screensfragment**.

   1. 要完成新体验片段的创建，请单击复选标记。

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   注意：要单击更简单的选项，请单击字段右侧的复选标记，以便打开选择对话框。

1. **创建体验片段的活动副本**

   1. 导航到AEM主页。
   1. 单击 **体验片段** 并突出显示 **Screensfragment** 并单击 **live-copy形式的变量**，如下图所示：

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c.单击 **Screensfragment** 从 **创建Live Copy** 向导并单击 **下一个**.

   d.输入 **标题** 和 **名称** 作为 **Screens**.

   e.单击 **创建** 以便创建Live Copy。

   f.单击 **完成** 这样你就可以移回 **Screensfragment** 页面。

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >创建AEM Screens片段后，可以编辑片段的属性。 单击片段，然后单击 **属性** 从操作栏中。

   **编辑屏幕片段的属性**

   1. 导航至 **Screensfragment** （在前面的步骤中创建）并单击 **属性** 从操作栏中。

   1. 单击 **脱机配置** 选项卡，如下图所示。

   您可以添加 **客户端库** (Java™和css)和 **静态文件** 到您的体验片段。

   以下示例显示了作为静态文件的一部分向体验片段添加的客户端库和字体。  ![片段](assets/fragment.gif)

1. **在屏幕渠道中使用体验片段作为组件**

   1. 导航到要在其中使用 **Screens** 片段。
   1. 单击 **TestChannel** 并单击 **编辑** 从操作栏中。

   1. 单击侧选项卡中的组件图标。
   1. 拖放 **体验片段** 到您的频道。

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e.单击 **体验片段** 组件并单击左上角（扳手）图标，以打开 **体验片段** 对话框。

   f.单击 **Screens** 您在中创建的片段的实时副本 *步骤3* 在 **路径**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f.单击 **Screens** 您在中创建的片段的实时副本 *步骤3* 在 **体验片段**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h.输入毫秒，单位： **持续时间**.

   i.单击 **脱机配置** 从 **体验片段** 对话框，以便您可以定义客户端库和静态文件。

   >[!NOTE]
   >
   >要添加客户端库或静态文件，以及您在步骤(4)中配置的内容，您可以从 **脱机配置** 选项卡 **体验片段** 对话框。

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j.单击复选标记，以便完成该流程。

### 验证结果 {#validating-the-result}

完成上述步骤后，可以在中验证您的体验片段 **ChannelOne** 通过：

1. 导航到 **TestChannel**.
1. 选择 **预览** 从操作栏中。

从查看内容 **站点** 页面（体验片段的实时副本）的数量，如下图所示：\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## 将更改传播到页面 {#propagating-changes-from-the-master-page}

***Live Copy*** 指由转出配置定义的同步操作维护的（源的）副本。

因为您创建的体验片段是来自的 **站点** 页面中，如果从主页面更改该特定片段，则可以在渠道中查看更改。 或者，查看您使用体验片段的目标。

>[!NOTE]
>
>有关Live Copy的更多信息，请参阅重用内容：多站点管理器和Live Copy 。

请按照以下步骤将更改从主渠道传播到您的目标渠道：

1. 单击中的体验片段 **站点** （主要）页面上，然后单击铅笔图标，以便您可以编辑体验片段中的项目。

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. 单击体验片段，然后单击扳手图标，以打开对话框来编辑图像。

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. 此 **产品网格** 对话框打开。

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. 您可以编辑任何图像。 例如，此处替换了此片段中的第一个图像。

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. 单击体验片段，然后单击转出图标，以使您可将更改传播到渠道中使用的片段。

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. 单击“转出”。

   请注意，这些更改已转出。

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### 验证更改 {#validating-the-changes}

请按照以下步骤确认对渠道所做的更改：

1. 导航至 **Screens** > **渠道** > **TestChannel**.

1. 单击 **预览** 从操作栏中。

下图说明了 **TestChannel**：\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)
