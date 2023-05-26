---
title: 文本覆盖
seo-title: Text Overlay
description: 文本叠加是AEM Screens中一项可用的功能，它允许您通过在图像上方提供标题或描述而在序列渠道中创建引人入胜的体验。 关注此页面以了解更多信息。
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
>此 **文本叠加** 功能仅在安装了AEM 6.3 Feature Pack 5或AEM 6.4 Feature Pack 3时才可用。

## 概述 {#overview}

文本叠加是AEM Screens中一项可用的功能，它允许您通过在图像上方提供标题或描述而在序列渠道中创建引人入胜的体验。

要了解如何创建自己的自定义组件，请参阅 **扩展AEM Screens组件**.

本节仅显示如何在AEM Screens项目中使用和应用海报组件，以及如何在其中一个序列渠道中将其用作文本叠加。

## 使用文本叠加 {#using-text-overlay}

以下部分介绍如何在AEM Screens项目中使用文本叠加。

**前提条件**

在开始实施此功能之前，请确保已将项目设置为开始实施文本叠加的先决条件。 例如，

* 创建一个AEM Screens项目(在本例中， **TextOverlayDemo**)

* 创建标题为 **文本示例** 下 **渠道** 文件夹

* 将内容添加到您的 **文本示例** 渠道

下图显示了 **TextOverlayDemo** 使用的项目 **文本示例** 中的频道 **渠道** 文件夹。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

请按照以下步骤在AEM Screens渠道中使用文本叠加：

1. 导航到 **TextOverlayDemo** —> **渠道** —> **文本示例** 并单击 **编辑** 以打开编辑器。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 选择图像并单击 **配置** （扳手图标）以打开“属性”对话框。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 选择 **文本叠加** 选项，如下图所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 了解文本叠加属性 {#understanding-text-overlay-properties}

使用文本叠加属性，您可以将文本添加到屏幕项目中的任何组件。 以下部分概述了文本叠加中可用的属性：

![文本](assets/text.gif)

您可以向文本框中添加文本并添加强调排版，例如粗体、斜体和下划线。

**颜色变量** 此选项允许文本为深色（黑色的文本）或浅色（白色的文本）。

**大小调整和定位** 此选项允许用户水平或垂直对齐文本，或使用细粒度工具对齐文本。

>[!NOTE]
>
>要正确使用细粒度工具，请确保使用(px)作为后缀（例如200像素）来标识正确的位置（以像素为单位）。 此表达式的结果是从起点算起200像素。

## 在文本叠加中使用ContextHub值 {#using-text-overlay-context-hub}

以下部分介绍了数据存储中的值的用法，例如，文本叠加组件中的google sheets 。

**前提条件**

为您的AEM Screens项目设置ContextHub配置。

要了解如何使用数据存储来设置和管理数据驱动的资产更改，请参阅 [在AEM Screens中配置ContextHub](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

为项目设置所需的配置后，请按照以下步骤使用Google Sheets中的值：

1. 导航到 **TextOverlayDemo** —> **渠道** —> **文本示例** 并单击 **属性** 操作栏中的。

1. 选择 **个性化** 选项卡以设置ContextHub配置。

   1. 选择 **ContextHub路径** 作为 **库** > **设置** > **云设置** > **默认** > **ContextHub配置** 并单击 **选择**.

   1. 选择 **区段路径** 作为 **会议** > **屏幕** > **设置** > **wcm** > **区段** 并单击 **选择**.

   1. 单击“**保存并关闭**”。

      >[!NOTE]
      >
      >使用ContextHub和区段路径，您最初是在其中保存了Context Hub配置和区段。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 导航到 **TextOverlayDemo** —> **渠道** —> **文本示例** 并单击 **编辑** 以打开编辑器。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 将图像和文本叠加组件添加到图像，如中所述 [使用文本叠加](/help/user-guide/text-overlay.md#using-text-overlay) 部分。

1. 单击 **配置** （扳手图标）以打开 **图像** 对话框。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 导航到 **ContextHub** 选项卡 **图像** 对话框。 单击 **添加**.

   >[!NOTE]
   >如果尚未设置ContextHub配置，则会为您的项目禁用此选项。

1. 输入 **值** 在 **占位符** 字段。 选择要从Google工作表中获取值的行 **ContextHub变量**. 在这种情况下，将从Google工作表中的行2和列1中检索值。 现在输入 **默认值** 作为 **20**，如下图所示。 完成后，单击复选标记。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >供您参考，下图显示了从Google Sheets中检索的值：

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 导航回到 **文本叠加** 选项卡，然后添加文本 *当前温度{Value}*，如下图所示。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 单击 **预览** 以查看所需的输出。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
