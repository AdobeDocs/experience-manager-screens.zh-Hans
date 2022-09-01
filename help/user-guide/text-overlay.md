---
title: 文本覆盖
seo-title: Text Overlay
description: 文本叠加是AEM Screens中提供的一项功能，通过提供覆盖在图像顶部的标题或描述，该功能允许您在序列渠道中创建引人入胜的体验。 请阅读本页以了解更多信息。
seo-description: Text Overlay is a feature available in AEM Screens that allows you to create a compelling experience in a Sequence Channel by providing a title or a description overlaid on top of an image. Follow this page to learn more.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 2%

---

# 文本覆盖 {#text-overlay}

本节涵盖以下主题：

* **概述**
* **使用文本叠加**
* **了解文本叠加属性**
* **在文本叠加中使用ContextHub值**

>[!CAUTION]
>
>的 **文本叠加** 功能仅当您安装了AEM 6.3功能包5或AEM 6.4功能包3时才可用。

## 概述 {#overview}

文本叠加是AEM Screens中提供的一项功能，通过提供覆盖在图像顶部的标题或描述，该功能允许您在序列渠道中创建引人入胜的体验。

要了解如何创建您自己的自定义组件，请参阅 **扩展AEM Screens组件**.

此部分仅展示如何在AEM Screens项目中使用和应用海报组件，并将其用作序列渠道之一中的文本叠加。

## 使用文本叠加 {#using-text-overlay}

以下部分介绍如何在AEM Screens项目中使用文本叠加。

**前提条件**

在开始实施此功能之前，请确保已将项目设置为开始实施文本叠加的先决条件。 例如，

* 创建AEM Screens项目(在此示例中， **TextOverlayDemo**)

* 创建名为的序列渠道 **TextSample** 在 **渠道** 文件夹

* 向 **TextSample** 渠道

下图显示了 **TextOverlayDemo** 项目 **TextSample** 渠道 **渠道** 文件夹。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

请按照以下步骤在AEM Screens渠道中使用文本叠加：

1. 导航到 **TextOverlayDemo** —> **渠道** —> **TextSample** 单击 **编辑** 从操作栏中打开编辑器。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 选择图像并单击 **配置** （扳手图标）打开“属性”对话框。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 选择 **文本叠加** 选项，如下图所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 了解文本叠加属性 {#understanding-text-overlay-properties}

使用文本叠加属性，您可以向Screens项目中的任何组件添加文本。 以下部分概述了文本叠加中可用的属性：

![text](assets/text.gif)

您可以在文本框中添加文本，并添加排版重点，如粗体、斜体和下划线。

**颜色变体** 此选项允许文本为“深色”（黑色文本）或“浅色”（白色文本）。

**大小调整和定位** 此选项允许用户水平或垂直对齐文本，或者也使用细粒度工具进行文本对齐。

>[!NOTE]
>
>要正确使用细粒度工具，请务必以像素(px)作为后缀来识别正确的位置，例如200像素。 此表达式的结果为距起始点200像素。

## 在文本叠加中使用ContextHub值 {#using-text-overlay-context-hub}

以下部分介绍数据存储中值的用法，例如，文本叠加组件中的google工作表。

**前提条件**

为AEM Screens项目设置ContextHub配置。

要了解如何使用数据存储来设置和管理数据驱动的资产更改，请参阅 [在AEM Screens中配置ContextHub](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

为项目设置所需配置后，请按照以下步骤使用google工作表中的值：

1. 导航到 **TextOverlayDemo** —> **渠道** —> **TextSample** 单击 **属性** 中。

1. 选择 **个性化** 选项卡来设置ContextHub配置。

   1. 选择 **ContextHub路径** as **libs** > **设置** > **云设置** > **默认** > **ContextHub配置** 单击 **选择**.

   1. 选择 **区段路径** as **conf** > **屏幕** > **设置** > **wcm** > **区段** 单击 **选择**.

   1. 单击“**保存并关闭**”。

      >[!NOTE]
      >
      >使用ContextHub和区段路径，您最初在其中保存了ContextHub配置和区段。

      ![图像1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 导航到 **TextOverlayDemo** —> **渠道** —> **TextSample** 单击 **编辑** 从操作栏中打开编辑器。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 向图像中添加图像和文本叠加组件，如 [使用文本叠加](/help/user-guide/text-overlay.md#using-text-overlay) 部分。

1. 单击 **配置** （扳手图标）以打开 **图像** 对话框。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 导航到 **ContextHub** 选项卡 **图像** 对话框。 单击&#x200B;**添加**。

   >[!NOTE]
   >如果尚未设置ContextHub配置，则对于您的项目，此选项将处于禁用状态。

1. 输入 **值** 在 **占位符** 字段。 选择要从Google工作表(位于 **ContextHub变量**. 在这种情况下，该值会从Google工作表的第2行和第1列中检索。 现在，输入 **默认值** as **20**，如下图所示。 完成后，单击复选标记。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >以下图像显示了从google工作表中检索的值，供您参考：

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 导航回 **文本叠加** 选项卡，然后添加文本 *当前温度{Value}*，如下图所示。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 单击 **预览** ，以查看所需的输出。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay10.png)
