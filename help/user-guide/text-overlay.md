---
title: 文本覆盖
seo-title: 文本覆盖
description: 文本叠加是AEM Screens中的一项功能，通过提供覆盖在图像顶部的标题或描述，您可以在序列渠道中创建引人入胜的体验。 可查看本页以了解更多信息。
seo-description: 文本叠加是AEM Screens中的一项功能，通过提供覆盖在图像顶部的标题或描述，您可以在序列渠道中创建引人入胜的体验。 可查看本页以了解更多信息。
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 文本覆盖 {#text-overlay}

本节涵盖以下主题：

* **概述**
* **使用文本叠加**
* **前提条件**
* **了解文本叠加属性**

>[!CAUTION]
>
>仅 **** 当您安装了AEM 6.3功能包5或AEM 6.4功能包3时，“文本叠加”功能才可用。

## 概述 {#overview}

文本叠加是AEM Screens中的一项功能，通过提供覆盖在图像顶部的标题或描述，您可以在序列渠道中创建引人入胜的体验。

要了解如何创建您自己的自定义组件，请参阅 **扩展AEM Screens组件**。

此部分仅展示如何在AEM Screens项目中使用和利用海报组件，并将其用作序列渠道之一中的文本叠加。

## 使用文本叠加 {#using-text-overlay}

下节介绍了在AEM Screens项目中使用文本叠加的方法。

### 前提条件 {#prerequisites}

在开始实施此功能之前，请确保已将项目设置为开始实施文本叠加的先决条件。 例如，

* 创建AEM Screens项目(在此示例中， **TextOverlayDemo**)

* 在“渠道”文件夹下 **创建TextSample****作** 为渠道。

* 将内容添加到 **TextSample** Channel

下图显示了TextOverlayDemo项目， **该项目在Channels** 文件夹中包含TextSample **channel****** 。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

1. 导航到 **TextOverlayDemo** —&gt; **Channels** —&gt; **TextSample** —并单击操 **** 作栏中的EditAdit以打开操作栏。

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
>要正确使用细粒度工具，请务必使用(px)作为后缀（例如200px）以像素为单位确定正确的位置。 此表达式的结果将是距起始点200像素。

