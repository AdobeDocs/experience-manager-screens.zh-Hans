---
title: 文本覆盖
seo-title: 文本覆盖
description: 文本叠加是AEM Screens中提供的一项功能，通过提供覆盖在图像顶部的标题或描述，该功能允许您在序列渠道中创建引人入胜的体验。 请阅读本页以了解更多信息。
seo-description: 文本叠加是AEM Screens中提供的一项功能，通过提供覆盖在图像顶部的标题或描述，该功能允许您在序列渠道中创建引人入胜的体验。 请阅读本页以了解更多信息。
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: 创作屏幕
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 3%

---

# 文本覆盖 {#text-overlay}

本节涵盖以下主题：

* **概述**
* **使用文本叠加**
* **了解文本叠加属性**
* **在文本叠加中使用ContextHub值**

>[!CAUTION]
>
>仅当您安装了AEM 6.3功能包5或AEM 6.4功能包3时，**文本叠加**&#x200B;功能才可用。

## 概述 {#overview}

文本叠加是AEM Screens中提供的一项功能，通过提供覆盖在图像顶部的标题或描述，该功能允许您在序列渠道中创建引人入胜的体验。

要了解如何创建您自己的自定义组件，请参阅&#x200B;**扩展AEM Screens组件**。

此部分仅展示如何在AEM Screens项目中使用和利用海报组件，并将其用作序列渠道中的一个渠道中的文本叠加。

## 使用文本叠加 {#using-text-overlay}

以下部分介绍如何在AEM Screens项目中使用文本叠加。

**前提条件**

在开始实施此功能之前，请确保已将项目设置为开始实施文本叠加的先决条件。 例如，

* 创建AEM Screens项目（在此示例中，**TextOverlayDemo**）

* 在&#x200B;**Channels**&#x200B;文件夹下创建名为&#x200B;**TextSample**&#x200B;的序列渠道

* 向&#x200B;**TextSample**&#x200B;渠道中添加内容

下图显示了&#x200B;**渠道**&#x200B;文件夹中具有&#x200B;**TextSample**&#x200B;渠道的&#x200B;**TextOverlayDemo**&#x200B;项目。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

请按照以下步骤在AEM Screens渠道中使用文本叠加：

1. 导航到&#x200B;**TextOverlayDemo** —> **渠道** —> **TextSample** ，然后单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 选择图像，然后单击&#x200B;**配置**（扳手图标）以打开属性对话框。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 从对话框的导航栏中选择&#x200B;**文本叠加**&#x200B;选项，如下图所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 了解文本叠加属性 {#understanding-text-overlay-properties}

使用文本叠加属性，您可以向Screens项目中的任何组件添加文本。 以下部分概述了文本叠加中可用的属性：

![text](assets/text.gif)

您可以在文本框中添加文本，并添加排版重点，如粗体、斜体、下划线等。

**颜色** 变体此选项允许文本为“深色”（黑色文本）或“浅色”（白色文本）。

**大小调** 整和定位此选项允许用户水平或垂直对齐文本，或者额外使用细粒度工具进行文本对齐。

>[!NOTE]
>
>要正确使用细粒度工具，请务必以像素(px)作为后缀来识别正确的位置，例如200px。 此表达式的结果将为距起始点200像素。

## 在文本叠加中使用ContextHub值 {#using-text-overlay-context-hub}

以下部分介绍数据存储中值的用法，例如，文本叠加组件中的google工作表。

**前提条件**

您必须为AEM Screens项目设置ContextHub配置。

要了解如何使用数据存储来设置和管理数据驱动的资产更改，请参阅[在AEM Screens中配置ContextHub](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/developing/configuring-context-hub.html)。

为项目设置所需配置后，请按照以下步骤使用google工作表中的值：

1. 导航到&#x200B;**TextOverlayDemo** —> **渠道** —> **TextSample** ，然后单击操作栏中的&#x200B;**属性**。

1. 选择&#x200B;**Personalization**&#x200B;选项卡以设置ContextHub配置。

   1. 选择&#x200B;**ContextHub路径**&#x200B;作为&#x200B;**libs** > **设置** > **cloudsettings** > **默认** > **ContextHub配置**&#x200B;并单击&#x200B;**选择**。

   1. 选择&#x200B;**区段路径**&#x200B;作为&#x200B;**conf** > **屏幕** > **设置** > **wcm** > **区段**&#x200B;并单击&#x200B;**选择**。

   1. 单击&#x200B;**保存并关闭**。

      >[!NOTE]
      >
      >使用ContextHub和区段路径，您最初在其中保存了ContextHub配置和区段。

      ![图像1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 导航到&#x200B;**TextOverlayDemo** —> **渠道** —> **TextSample** ，然后单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 按照本页[使用文本叠加](/help/user-guide/text-overlay.md#using-text-overlay)部分中的说明，向图像添加图像和文本叠加组件。

1. 单击&#x200B;**配置**（扳手图标）以打开&#x200B;**图像**&#x200B;对话框。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 从&#x200B;**Image**&#x200B;对话框中导航到&#x200B;**ContextHub**&#x200B;选项卡。 单击&#x200B;**添加**。

   >[!NOTE]
   >如果尚未设置ContextHub配置，则将为您的项目禁用此选项。

1. 在&#x200B;**Placeholder**&#x200B;字段中输入&#x200B;**值**，在&#x200B;**ContextHub Variable**&#x200B;中选择要从Google工作表中获取值的行（在本例中，该值是从Google工作表的行2和列1中检索），然后输入&#x200B;**默认值**&#x200B;作为&#x200B;**20**，如下图所示。 完成后，单击复选标记。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >以下图像显示了从google工作表中检索的值，供您参考：

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 从“图像”对话框中导航回&#x200B;**文本叠加**&#x200B;选项卡，并添加文本&#x200B;*当前温度{Value}*，如下图所示。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 单击&#x200B;**预览**&#x200B;以查看所需的输出。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay10.png)
