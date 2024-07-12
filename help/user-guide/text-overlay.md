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
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '775'
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
>仅当您安装了AEM 6.3 Feature Pack 5或AEM 6.4 Feature Pack 3时，**文本叠加**&#x200B;功能才可用。

## 概述 {#overview}

文本叠加是AEM Screens中一项可用的功能。 它通过在图像上方提供标题或描述，让您在序列渠道中创建引人入胜的体验。

要了解如何创建自己的自定义组件，请参阅&#x200B;**扩展AEM Screens组件**。

本节仅显示如何在AEM Screens项目中使用和应用海报组件。 它还展示了如何在一个序列渠道中将其用作文本叠加。

## 使用文本叠加 {#using-text-overlay}

下节介绍如何在AEM Screens项目中使用文本叠加。

**前提条件**

在实施此功能之前，请确保已设置项目作为开始实施文本叠加的先决条件。 例如，

* 创建一个AEM Screens项目（在此示例中，**TextOverlayDemo**）

* 在&#x200B;**Channels**&#x200B;文件夹下创建标题为&#x200B;**TextSample**&#x200B;的序列频道

* 将内容添加到您的&#x200B;**TextSample**&#x200B;频道

下图显示了&#x200B;**渠道**&#x200B;文件夹中具有&#x200B;**TextSample**&#x200B;渠道的&#x200B;**TextOverlayDemo**&#x200B;项目。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

请按照以下步骤在AEM Screens渠道中使用文本叠加：

1. 导航到&#x200B;**TextOverlayDemo** > **渠道** > **TextSample**，然后单击操作栏中的&#x200B;**编辑**。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 单击图像，然后单击&#x200B;**配置** （扳手图标）以打开属性对话框。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 单击对话框导航栏中的&#x200B;**文本叠加**&#x200B;选项，如下图所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 了解文本叠加属性 {#understanding-text-overlay-properties}

使用文本覆盖属性，您可以将文本添加到Screens项目中的任何组件。 以下部分概述了文本叠加中可用的属性：

![文本](assets/text.gif)

您可以向文本框中添加文本并添加印刷强调字符，例如粗体、斜体和下划线。

**颜色变量**&#x200B;此选项允许文本为深色（黑色的文本）或浅色（白色的文本）。

**调整大小和定位**&#x200B;此选项允许用户水平或垂直对齐文本，或者使用细粒度工具对齐文本。

>[!NOTE]
>
>使用细粒度工具时，请确保使用作为后缀的(px)以像素为单位标识正确的位置，例如200像素。 此表达式的结果是从起点算起的200像素。

## 在文本覆盖中使用ContextHub值 {#using-text-overlay-context-hub}

以下部分介绍数据存储中的值的用法，例如，文本覆盖组件中的google sheets 。

**前提条件**

为您的AEM Screens项目设置ContextHub配置。

要了解如何使用数据存储设置和管理数据驱动资源更改，请参阅[在AEM Screens中配置ContextHub](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/configuring-context-hub)。

在为项目设置所需的配置后，请按照以下步骤使用Google工作表中的值：

1. 导航到&#x200B;**TextOverlayDemo** > **渠道** > **TextSample**，然后单击操作栏中的&#x200B;**属性**。

1. 单击&#x200B;**Personalization**&#x200B;选项卡，以便设置ContextHub配置。

   1. 单击&#x200B;**ContextHub路径**&#x200B;作为&#x200B;**libs** > **设置** > **cloudsettings** > **默认值** > **ContextHub配置**，然后单击&#x200B;**选择**。

   1. 单击&#x200B;**区段路径**&#x200B;作为&#x200B;**conf** > **屏幕** > **设置** > **wcm** > **区段**，然后单击&#x200B;**选择**。

   1. 单击“**保存并关闭**”。

      >[!NOTE]
      >
      >使用ContextHub和区段路径，您最初是在其中保存了Context Hub配置和区段。

      ![图像1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 导航到&#x200B;**TextOverlayDemo** > **渠道** > **TextSample**，然后单击操作栏中的&#x200B;**编辑**。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 按照此页面的[使用文本叠加](/help/user-guide/text-overlay.md#using-text-overlay)部分中的说明，将图像和文本叠加组件添加到您的图像中。

1. 单击&#x200B;**配置** （扳手图标）以打开&#x200B;**图像**&#x200B;对话框。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 从&#x200B;**图像**&#x200B;对话框中导航到&#x200B;**ContextHub**&#x200B;选项卡。 单击&#x200B;**添加**。

   >[!NOTE]
   >如果尚未设置ContextHub配置，则会为您的项目禁用此选项。

1. 在&#x200B;**占位符**&#x200B;字段中输入&#x200B;**值**。 在&#x200B;**ContextHub变量**&#x200B;中单击要从Google工作表中获取值的行。 在这种情况下，将从Google工作表中的行2和列1检索值。 现在，输入&#x200B;**默认值**&#x200B;为&#x200B;**20**，如下图所示。 完成后，单击复选标记。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >供您参考，下图显示了从Google工作表中检索的值：

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 从“图像”对话框导航回&#x200B;**文本叠加**&#x200B;选项卡，并添加文本&#x200B;*当前温度{Value}*，如下图所示。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 单击&#x200B;**预览**。

   ![图像1](/help/user-guide/assets/text-overlay/text-overlay10.png)
