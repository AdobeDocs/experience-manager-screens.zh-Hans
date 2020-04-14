---
title: 文本覆盖
seo-title: 文本覆盖
description: 文本叠加是AEM Screens中提供的一项功能，通过提供覆盖在图像顶部的标题或描述，您可以在序列渠道中创建引人入胜的体验。 可查看本页以了解更多信息。
seo-description: 文本叠加是AEM Screens中提供的一项功能，通过提供覆盖在图像顶部的标题或描述，您可以在序列渠道中创建引人入胜的体验。 可查看本页以了解更多信息。
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: 651627223e1b9bd0f650b010d2b92f004b9e2ea2

---


# 文本覆盖 {#text-overlay}

本节涵盖以下主题：

* **概述**
* **使用文本叠加**
* **了解文本叠加属性**
* **在文本叠加中使用ContextHub值**

>[!CAUTION]
>
>仅 **** 当您安装了AEM 6.3功能包5或AEM 6.4功能包3时，“文本叠加”功能才可用。

## 概述 {#overview}

文本叠加是AEM Screens中提供的一项功能，通过提供覆盖在图像顶部的标题或描述，您可以在序列渠道中创建引人入胜的体验。

要了解如何创建您自己的自定义组件，请参 **阅扩展AEM Screens组件**。

此部分仅展示如何在AEM Screens项目中使用和利用海报组件，并将其用作序列渠道中的文本叠加。

## 使用文本叠加 {#using-text-overlay}

下节介绍了在AEM Screens项目中使用文本叠加的方法。

**前提条件**

在开始实现此功能之前，请确保已将项目设置为开始实现文本叠加的先决条件。 例如，

* 创建AEM Screens项目(在此示例中， **TextOverlayDemo**)

* 在“渠道”文件夹下创建标题为 **TextSample** 的序 **列渠道** 。

* 将内容添加到 **TextSample** 渠道

下图显示了 **TextOverlayDemo项目，该项目在****渠道文件夹中具有TextSample****渠道** 。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

请按照以下步骤在AEM Screens渠道中使用文本叠加：

1. 导航到 **TextOverlayDemo** —> **渠道** —> **TextSample** —并单击操作 **** 栏中的EditFrom以打开该编辑器。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 选择图像，然后单击 **配置** （扳手图标）以打开属性对话框。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 从对话框 **的导航栏中选择** “文本叠加”选项，如下图所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 了解文本叠加属性 {#understanding-text-overlay-properties}

使用“文本叠加”属性，可以向Screens项目中的任何组件添加文本。 以下部分概述了文本叠加中可用的属性：

![text](assets/text.gif)

您可以向文本框中添加文本并添加排版重点，如粗体、斜体、下划线等。

**颜色变体** “此选项”允许文本为深色（黑色文本）或浅色（白色文本）。

**调整大小和位置** “此选项”允许用户水平或垂直对齐文本，或者另外使用细致的工具进行文本对齐。

>[!NOTE]
>
>要正确使用细粒度工具，请务必使用(px)作为后缀（例如200px）以像素为单位确定正确的位置。 此表达式的结果将是距开始点200像素。

## 在文本叠加中使用ContextHub值 {#using-text-overlay-context-hub}

下节介绍数据存储中的值的用法，例如，文本叠加组件中的google表单。

**前提条件**

必须为AEM Screens项目设置ContextHub配置。

要了解如何使用数据存储设置和管理数据驱动的资产更改，请参阅在AEM Screens中 [配置ContextHub](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/developing/configuring-context-hub.html)。

为项目设置所需配置后，请按照以下步骤使用Google工作表中的值：

1. 导航到 **TextOverlayDemo** —> **渠道** —> **TextSample** ，然后单击操 **** 作栏中的Properties。

1. 选择“个 **性化** ”选项卡以设置ContextHub配置。

   1. 选择“ **Hub Path** ”作 **为** Libs **>** > Settings > DefaultHub **>DefaultHob Context Configurations(Libs**************> Settings > DefaultHub Context And Click SelectCloveCt”。

   1. 选择段路径 **Path Path** Conf **> screens** > **Settings > Wcm Screens** > Wcm Select Select Select中的Click As ****************> Select Select的线段。

   1. 单击 **保存并关闭**。

      >[!NOTE]
      >
      >使用ContextHub和“区段”路径，您最初在该路径中保存了Context Hub配置和区段。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 导航到 **TextOverlayDemo** —> **渠道** —> **TextSample** —并单击操作 **** 栏中的EditFrom以打开该编辑器。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 如本页的“使用文本叠加”部分中所述，向图像 [添加图像和文本叠加组件](/help/user-guide/text-overlay.md#using-text-overlay) 。

1. 单击“ **配置** （扳手图标）”以打开“图 **像** ”对话框。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 从“图像 **”对话框中** ，导航到 **ContextHub选项卡** 。 单击&#x200B;**添加**。

   >[!NOTE]
   >如果尚未设置ContextHub配置，则将为项目禁用此选项。

1. 在 **Value****字段中，选择要从** ContextVariable ************（本例中，从行2和google表的列1检索值）中获取值的行，并将“默认值”(Default Value)输入为分析占位符（如下图所示）:“分析表”(Hub)。 完成后，单击复选标记。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >以下图像显示从google工作表检索到的值以供参考：

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 从“图像”对 **话框导航回“文本叠加** ”选项卡，并添加文本“当前温度”{Value} **，如下图所示。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 单击 **预览** ，以视图所需的输出。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)















