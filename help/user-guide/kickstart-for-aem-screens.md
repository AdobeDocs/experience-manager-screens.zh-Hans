---
title: Kickstart指南
seo-title: Kickstart指南
description: 请按照本页创建一个演示AEM Screens项目。 它可帮助您创建数字标牌体验，从安装和设置新项目开始，到在AEM Screens播放器中查看您的内容。
feature: 数字标牌概述
role: Business Practitioner
level: Beginner
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1320'
ht-degree: 5%

---


# Kickstart指南{#kickstart-guide}

AEM Screens启动演示了如何设置和运行AEM Screens项目。 它可指导您设置基本的数字标牌体验，并向每个渠道添加资产和/或视频等内容，以及将内容进一步发布到AEM Screens播放器。

>[!NOTE]
>在开始处理项目详细信息之前，请确保已安装最新的AEM Screens功能包。 您可以使用Adobe ID从[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载最新功能包。

## 前提条件 {#prerequisites}

请按照以下步骤为AEM Screens创建示例项目，并进一步将内容发布到Screens播放器。

>[!NOTE]
>以下教程将在Chrome OS播放器中显示渠道的内容。

>[!IMPORTANT]
>**OSGi配置设置**
>必须启用空反向链接，才能允许设备将数据发布到服务器。 例如，如果禁用了空反向链接属性，则设备将无法发布回屏幕截图。 目前，其中某些功能仅在OSGi配置中启用了Apache Sling反向链接过滤器允许为空时才可用。 功能板可能显示一条警告，指出安全设置可能会阻止某些功能正常工作。
>请按照以下步骤启用&#x200B;***Apache Sling反向链接过滤器允许空***:


## 允许空反向链接请求{#allow-empty-referrer-requests}

1. 通过AEM实例导航到&#x200B;**Adobe Experience Manager Web控制台配置** —>锤子图标 — > **操作** —> **Web控制台**。

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web控制台** 配置打开。搜索sling反向链接。

   要搜索Sling反向链接属性，请按&#x200B;**Command+F**（对于&#x200B;**Mac**）和&#x200B;**Control+F**（对于&#x200B;**Windows**）。

1. 选中&#x200B;**允许空**&#x200B;选项，如下图所示。

   ![图像](assets/config/empty-ref2.png)

1. 单击&#x200B;**Save**&#x200B;以启用Apache Sling反向链接过滤器允许为空。

## 在五分钟之内创建一个数字标牌体验{#creating-a-digital-signage-experience-in-minutes}

### 创建AEM Screens项目{#creating-project}

第一步是创建一个AEM Screens项目。

1. 导航到您的Adobe Experience Manager(AEM)实例，然后单击&#x200B;**Screens**。 或者，您也可以直接从`https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`导航。

1. 单击&#x200B;**创建Screens项目**&#x200B;以创建新的Screens项目。 输入&#x200B;**DemoScreens**&#x200B;标题，然后单击&#x200B;**Save**。

   ![图像](assets/kickstart/demo-1.png)

   >[!NOTE]
   >创建项目后，您将返回Screens项目主页。 现在，您可以选择自己的项目。在项目中，有五个不同的文件夹，标题为&#x200B;**应用程序**、**渠道**、**设备**、**位置**&#x200B;和&#x200B;**计划**。

### 创建渠道 {#creating-channel}

创建AEM Screens项目后，您需要创建一个新渠道以在其中管理内容。

请按照以下步骤为项目创建新渠道：

1. 创建项目后，选择&#x200B;**DemoScreens**&#x200B;项目，然后选择&#x200B;**渠道**&#x200B;文件夹，如下图所示。 单击操作栏中的&#x200B;**+创建**。

   ![图像](assets/kickstart/demo-2.png)

1. 从向导中选择&#x200B;**序列渠道**，然后单击&#x200B;**下一步**。
   ![图像](assets/kickstart/demo-3.png)

1. 将&#x200B;**标题**&#x200B;输入为&#x200B;**TestChannel**，然后单击&#x200B;**创建**。

   ![图像](assets/kickstart/demo-4.png)

   **TestChannel**&#x200B;现已添加到渠道文件夹中，如下图所示。

   ![图像](assets/kickstart/demo-5.png)

### 向渠道{#adding-content}添加内容

渠道就绪后，您需要向渠道中添加AEM Screens播放器将显示的内容。

请按照以下步骤向项目中的渠道(**TestChannel**)添加内容：

1. 导航到您创建的&#x200B;**DemoProject**，然后从&#x200B;**Channels**&#x200B;文件夹中选择&#x200B;**TestChannel**。

1. 单击操作栏中的&#x200B;**编辑**（请参阅下图）。 将打开&#x200B;**TestChannel**&#x200B;的编辑器。

   ![图像](assets/kickstart/demo-6.png)

1. 单击操作栏左侧用于切换侧面板的图标以打开资产和组件。

1. 将您希望添加的组件拖放到渠道中。

   ![图像](assets/kickstart/demo-7.png)

### 创建位置 {#creating-location}

渠道就位后，您需要创建一个位置。

>[!NOTE]
>***位置***&#x200B;可划分您的各种数字标牌体验，并包含各种屏幕所在位置所对应的显示器配置。

请按照以下步骤为项目创建新位置：

1. 导航到您创建的&#x200B;**DemoProject**&#x200B;文件夹，然后选择&#x200B;**Locations**&#x200B;文件夹。

1. 单击操作栏中的&#x200B;**+创建**。

1. 从向导中选择&#x200B;**位置**&#x200B;并单击&#x200B;**下一步**。

1. 输入位置的&#x200B;**名称**（输入&#x200B;**TestLocation**&#x200B;的标题），然后单击&#x200B;**创建**。

将创建&#x200B;**TestLocation**&#x200B;并将其添加到您的&#x200B;**Locations**&#x200B;文件夹中。


### 创建位置{#creating-display}的显示

创建位置后，您需要为该位置创建一个新显示屏。

>[!NOTE]
>***显示***&#x200B;表示在一个或多个屏幕上运行的数字体验。

1. 导航到&#x200B;**TestLocation**&#x200B;并选择它。

1. 单击操作栏中的&#x200B;**创建**。

   ![图像](assets/kickstart/demo-disp1.png)

1. 从&#x200B;**创建**&#x200B;向导中选择&#x200B;**显示**，然后单击&#x200B;**下一步**。

   ![图像](assets/kickstart/demo-disp2.png)

1. 将&#x200B;**标题**&#x200B;输入为&#x200B;**LobbyDisplay**，然后单击&#x200B;**创建**。

   ![图像](assets/kickstart/demo-disp3.png)

   标题为&#x200B;**TestDisplay**&#x200B;的新显示屏现已添加到您的位置&#x200B;**TestLocation**，如下图所示。

   ![图像](assets/kickstart/demo-disp4.png)

### 分配渠道{#assigning-channel}

项目设置完成后，必须将渠道分配给显示屏来查看内容。

1. 从&#x200B;**DemoScreens** —> **位置** —> **TestLocation** —> **LobbyDisplay**&#x200B;导航到所需的显示屏。

1. 点按/单击操作栏中的&#x200B;**分配渠道** 。

   ![图像](assets/kickstart/demo-assign1.png)

   或者，

   点按/单击操作栏中的&#x200B;**功能板** ，然后单击&#x200B;**已分配的渠道和计划**&#x200B;面板中的&#x200B;**+分配渠道**。

   ![图像](assets/kickstart/demo-assign2.png)

1. 将打开&#x200B;**渠道分配**&#x200B;对话框。

1. 从&#x200B;**设置**&#x200B;选项中，按路径&#x200B;**和**&#x200B;受支持事件&#x200B;**选择通道**&#x200B;作为&#x200B;**初始加载**&#x200B;和&#x200B;**空闲屏幕**。

   >[!NOTE]
   >
   >默认情况下，将填充&#x200B;**渠道角色**、**优先级**&#x200B;和&#x200B;**中断方法**。 请参阅[渠道属性](/help/user-guide/channel-assignment-latest-fp.md#channel-properties)部分，了解有关渠道分配属性的更多信息。

   ![图像](assets/kickstart/demo-assign3.png)

   此外，您还可以选择&#x200B;**激活窗口**&#x200B;和&#x200B;**重复计划**。

   >[!NOTE]
   >*重复计划*允许您为渠道设置重复计划。 为渠道设置多个重复计划。
   >有关更多详细信息，请参阅[重复计划](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule)。

1. 配置首选项后，单击&#x200B;**Save**。

### 注册设备并将设备分配给显示器{#registering-device}

您需要使用AEM仪表板注册设备。

>[!IMPORTANT]
>在开发人员模式下，Chrome OS播放器可以作为Chrome浏览器插件安装，而无需使用实际的Chrome播放器设备。 要进行安装，请执行以下步骤：
>
>1. 单击[此处](https://download.macromedia.com/screens/)下载最新的Chrome播放器。
>1. 解压缩并将其保存在磁盘上。
>1. 打开Chrome浏览器并从菜单中选择&#x200B;**扩展**，或直接导航到&#x200B;***chrome://extensions***。
>1. 从右上角切换&#x200B;**开发人员模式**。
>1. 单击左上角的&#x200B;**Load Unpacked** ，然后加载已解压的Chrome播放器。
>1. 检查&#x200B;**AEM Screens Chrome Player**&#x200B;插件（如果扩展列表中可用）。
>1. 打开新选项卡，然后单击左上角的&#x200B;**Apps**&#x200B;图标，或直接导航到&#x200B;***chrome://apps***。
>1. 单击&#x200B;**AEM Screens**&#x200B;插件以启动Chrome播放器。 默认情况下，播放器以全屏模式启动。 按&#x200B;**esc**&#x200B;退出全屏模式。


在您的Chrome OS播放器开启后，请按照以下步骤注册Chrome设备。

1. 从AEM实例导航到项目的&#x200B;**Devices**&#x200B;文件夹。

1. 点按/单击操作栏中的&#x200B;**设备管理器**。

   ![图像](assets/kickstart/demo-register1.png)

1. 点按/单击右上方的&#x200B;**设备注册**。

1. 选择所需的设备，然后点按/单击&#x200B;**注册设备**。

   ![图像](assets/kickstart/demo-register2.png)

1. 等待设备发送其注册代码，并同时检查Chrome设备中的&#x200B;**注册代码**。
   ![图像](assets/kickstart/demo-register3.png)

1. 如果两台计算机上的&#x200B;**注册代码**&#x200B;相同，请点按/单击AEM中的&#x200B;**验证**。

1. 将设备的所需名称设置为&#x200B;**ChromeDeviceforDemo**，然后单击&#x200B;**注册**。

   ![图像](assets/kickstart/demo-register4.png)

1. 单击&#x200B;**设备注册成功**&#x200B;对话框中的&#x200B;**指定显示**。

   ![图像](assets/kickstart/demo-register5.png)

1. 选择显示路径，作为&#x200B;**DemoScreens** —> **位置** —> **TestLocation** —> **LobbyDisplay** ，然后单击&#x200B;**分配**。

   ![图像](assets/kickstart/demo-device6.png)

1. 成功分配设备后，您将看到以下确认信息。

   ![图像](assets/kickstart/demo-register8.png)

1. 点按/单击&#x200B;**完成**&#x200B;以完成注册过程。 您应该能够从显示仪表板中查看注册的设备。

   ![图像](assets/kickstart/demo-register9.png)

### 在Chrome播放器{#viewing-content-output}中查看内容

现在，渠道中的所有资产都在您的Chrome OS播放器上播放。

恭喜您现在正在AEM Screens频道中播放内容！

![图像](assets/kickstart/demo-video-screens.gif)
