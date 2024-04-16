---
title: 文本覆盖
description: 了解AEM Screens中的文本叠加，它通过在图像上方提供标题或描述，让您在序列渠道中创建引人入胜的体验。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 1%

---

# 文本覆盖 {#text-overlay}

本节涵盖以下主题：

* **概述**
* **使用文本叠加**
* **了解文本叠加属性**
* **在文本覆盖中使用ContextHub值**

>[!CAUTION]
>
>此 **文本叠加** 功能仅在安装了AEM 6.3 Feature Pack 5或AEM 6.4 Feature Pack 3时才可用。

## 概述 {#overview}

文本叠加是AEM Screens中提供的功能，它通过在图像上方提供标题或描述而在序列渠道中创建引人入胜的体验。

要了解如何创建自己的自定义组件，请参阅 **扩展AEM Screens组件**.

本节仅显示如何在AEM Screens项目中使用和应用海报组件，并将其用作某个序列渠道中的文本叠加。

## 使用文本叠加 {#using-text-overlay}

下节介绍如何在AEM Screens项目中使用文本叠加。

**前提条件**

在实施此功能之前，请确保已设置项目作为开始实施文本叠加的先决条件。 例如，

* 创建一个AEM Screens项目(在此示例中， **TextOverlayDemo**)

* 创建标题为 **文本示例** 下 **渠道** 文件夹

* 将内容添加到您的 **文本示例** 渠道

下图显示了 **TextOverlayDemo** 使用的项目 **文本示例** 中的频道 **渠道** 文件夹。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

请按照以下步骤在AEM Screens渠道中使用文本叠加：

1. 导航到 **TextOverlayDemo** > **渠道** > **文本示例** 并选择 **编辑** 从操作栏中。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 选择图像并选择 **配置** （扳手图标）以打开“属性”对话框。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 选择 **文本叠加** 对话框导航栏中的选项，如下图所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 了解文本叠加属性 {#understanding-text-overlay-properties}

使用文本叠加属性，您可以将文本添加到屏幕项目中的任何组件。 以下部分概述了文本叠加中可用的属性：

![文本](assets/text.gif)

您可以向文本框中添加文本并添加印刷强调字符，例如粗体、斜体和下划线。

**颜色变量** 此选项允许文本为深色（黑色的文本）或浅色（白色的文本）。

**大小调整和定位** 此选项允许用户水平或垂直对齐文本，或者使用细粒度工具对齐文本。

>[!NOTE]
>
>要正确使用细粒度工具，请确保使用(px)作为后缀来识别正确的像素位置，例如200像素。 此表达式的结果是从起点算起的200像素。

## 在文本覆盖中使用ContextHub值 {#using-text-overlay-context-hub}

以下部分介绍数据存储中的值的用法，例如，文本覆盖组件中的google sheets 。

**前提条件**

为您的AEM Screens项目设置ContextHub配置。

要了解如何使用数据存储来设置和管理数据驱动的资源更改，请参阅 [在AEM Screens中配置ContextHub](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/configuring-context-hub).

在为项目设置所需的配置后，请按照以下步骤使用Google工作表中的值：

1. 导航到 **TextOverlayDemo** > **渠道** > **文本示例** 并选择 **属性** 从操作栏中。

1. 选择 **个性化** 选项卡，以便设置ContextHub配置。

   1. 选择 **ContextHub路径** 作为 **库** > **设置** > **云设置** > **默认** > **ContextHub配置** 并选择 **选择**.

   1. 选择 **区段路径** 作为 **会议** > **屏幕** > **设置** > **wcm** > **区段** 并选择 **选择**.

   1. 选择&#x200B;**保存并关闭**。

      >[!NOTE]
      >
      >使用ContextHub和区段路径，您最初是在其中保存了Context Hub配置和区段。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 导航到 **TextOverlayDemo** > **渠道** > **文本示例** 并选择 **编辑** 从操作栏中。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 将图像和文本叠加组件添加到图像，如中所述 [使用文本叠加](/help/user-guide/text-overlay.md#using-text-overlay) 部分。

1. 选择于 **配置** （扳手图标）以打开 **图像** 对话框。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 导航至 **ContextHub** 选项卡 **图像** 对话框。 选择&#x200B;**添加**。

   >[!NOTE]
   >如果尚未设置ContextHub配置，则会为您的项目禁用此选项。

1. 输入 **值** 在 **占位符** 字段。 选择要从Google工作表中获取值的行 **ContextHub变量**. 在这种情况下，将从Google工作表中的行2和列1检索值。 现在，输入 **默认值** 作为 **20**，如下图所示。 完成后，选中复选标记。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >供您参考，下图显示了从Google工作表中检索的值：

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 导航回 **文本叠加** 选项卡，然后添加文本 *当前温度 {Value}*，如下图所示。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 选择 **预览**.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
