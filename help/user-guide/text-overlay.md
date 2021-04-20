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
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '853'
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
>**文本叠加**&#x200B;功能仅在您安装了AEM 6.3功能包5或AEM 6.4功能包3时可用。

## 概述 {#overview}

文本叠加是AEM Screens中的一项功能，通过提供覆盖在图像顶部的标题或描述，您可以在序列渠道中创建引人入胜的体验。

要了解如何创建您自己的自定义组件，请参阅&#x200B;**扩展AEM Screens组件**。

此部分仅展示如何在AEM Screens项目中使用和利用海报组件，并将其用作某个序列渠道中的文本叠加。

## 使用文本叠加{#using-text-overlay}

下节介绍了文本叠加在AEM Screens项目中的使用。

**前提条件**

在开始实现此功能之前，请确保已将项目设置为开始实现文本叠加的先决条件。 例如，

* 创建AEM Screens项目（在此示例中，**TextOverlayDemo**）

* 在&#x200B;**渠道**&#x200B;文件夹下创建标题为&#x200B;**TextSample**&#x200B;的序列渠道

* 将内容添加到&#x200B;**TextSample**&#x200B;渠道

下图显示了&#x200B;**渠道**&#x200B;文件夹中具有&#x200B;**TextSample**&#x200B;渠道的&#x200B;**TextOverlayDemo**&#x200B;项目。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

请按照以下步骤在AEM Screens渠道中使用文本叠加：

1. 导航到&#x200B;**TextOverlayDemo** —> **渠道** —> **TextSample**&#x200B;并单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 选择图像，然后单击&#x200B;**配置**（扳手图标）以打开属性对话框。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 从对话框的导航栏中选择&#x200B;**文本叠加**&#x200B;选项，如下图所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 了解文本叠加属性{#understanding-text-overlay-properties}

使用“文本叠加”属性，可以向Screens项目中的任何组件添加文本。 以下部分概述了文本叠加中可用的属性：

![text](assets/text.gif)

您可以向文本框中添加文本，并添加排版重点，如粗体、斜体、下划线等。

**颜色** 变体此选项允许文本为深色（黑色文本）或浅色（白色文本）。

**大小调** 整和定位此选项允许用户水平或垂直对齐文本，或者另外使用细粒度工具进行文本对齐。

>[!NOTE]
>
>要正确使用细粒度工具，请务必使用(px)作为后缀（例如200px）以像素为单位确定正确的位置。 此表达式的结果将是距开始点200像素。

## 在文本叠加{#using-text-overlay-context-hub}中使用ContextHub值

下节介绍数据存储中值的用法，例如，文本叠加组件中的google表。

**前提条件**

必须为AEM Screens项目设置ContextHub配置。

要了解如何使用数据存储设置和管理数据驱动的资产更改，请参阅AEM Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/developing/configuring-context-hub.html)中的[配置ContextHub。

设置项目所需的配置后，请按照以下步骤使用Google工作表中的值：

1. 导航到&#x200B;**TextOverlayDemo** —> **渠道** —> **TextSample**&#x200B;并单击操作栏中的&#x200B;**属性**。

1. 选择&#x200B;**个性化**&#x200B;选项卡以设置ContextHub配置。

   1. 选择&#x200B;**ContextHub路径**&#x200B;作为&#x200B;**libs** > **settings** > **cloudsettings** > **default** > **ContextHub配置**&#x200B;并单击&#x200B;**选择**。

   1. 选择&#x200B;**区段路径**&#x200B;作为&#x200B;**conf** > **屏幕** > **设置** > **wcm** > **区段**，然后单击&#x200B;**选择**。

   1. 单击&#x200B;**保存并关闭**。

      >[!NOTE]
      >
      >使用ContextHub和“区段”路径，您最初在其中保存了Context Hub配置和区段。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 导航到&#x200B;**TextOverlayDemo** —> **渠道** —> **TextSample**&#x200B;并单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 如本页的[使用文本叠加](/help/user-guide/text-overlay.md#using-text-overlay)部分所述，向图像添加图像和文本叠加组件。

1. 单击&#x200B;**配置**（扳手图标）以打开&#x200B;**图像**&#x200B;对话框。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 从&#x200B;**Image**&#x200B;对话框导航到&#x200B;**ContextHub**&#x200B;选项卡。 单击&#x200B;**添加**。

   >[!NOTE]
   >如果您尚未设置ContextHub配置，则将为您的项目禁用此选项。

1. 在&#x200B;**占位符**&#x200B;字段中输入&#x200B;**值**，选择要从&#x200B;**ContextHub变量**&#x200B;的google工作表中获取值的行（在这种情况下，从google工作表的第2行和第1列检索值），然后输入&#x200B;**默认值**&#x200B;如下图所示，**20**。 完成后，单击复选标记。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >以下图像将显示从google工作表检索到的值，以供参考：

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 从&quot;图像&quot;对话框导航回&#x200B;**&quot;文本叠加&quot;**&#x200B;选项卡，并添加文本&#x200B;*&quot;当前温度{Value}*&quot;，如下图所示。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 单击&#x200B;**预览**&#x200B;以视图所需的输出。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)















