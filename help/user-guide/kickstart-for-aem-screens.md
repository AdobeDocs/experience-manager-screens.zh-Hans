---
title: Kickstart指南
description: 了解如何创建演示AEM Screens项目。 它可帮助您创建数字标牌体验，从安装和设置新项目开始，一直到在AEM Screens Player中查看内容为止。
feature: Overview, Digital Signage
role: User
level: Beginner
exl-id: 9b7c7f50-2846-4727-a0ec-0220b4cd52c4
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 2%

---

# Kickstart指南 {#kickstart-guide}

AEM Screens快速入门演示了如何设置和运行AEM Screens项目。 它将指导您逐步建立基本的数字标牌体验，并向每个渠道添加内容（如资产和/或视频），然后将内容进一步发布到AEM Screens播放器。

>[!NOTE]
>在处理项目详细信息之前，请确保已安装了适用于AEM Screens的最新功能包。 您可以使用您的Adobe ID从[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载最新的功能包。

## 先决条件 {#prerequisites}

请按照以下步骤为AEM Screens创建示例项目，然后将内容进一步发布到Screens播放器。

>[!NOTE]
>以下教程展示了如何在Chrome操作系统播放器中播放渠道内容。

>[!IMPORTANT]
>**OSGi配置设置**
>>必须启用空反向链接以允许设备向服务器发布数据。 例如，如果禁用empty referrer属性，设备将无法张贴屏幕快照。 当前，这些功能中的某些功能仅在OSGi配置中启用`Apache Sling`反向链接筛选条件允许空后才可用。 仪表板可能会显示警告，指出安全设置可能会阻止这些功能中的某些功能正常工作。
>>按照以下步骤启用&#x200B;***Apache Sling引用过滤器允许为空***：


## 允许空反向链接请求 {#allow-empty-referrer-requests}

1. 通过Adobe Experience Manager实例>锤子图标> **操作** > **Web控制台**&#x200B;导航到&#x200B;**AEM Web控制台配置**。

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web控制台配置**&#x200B;打开。 搜索Sling反向链接。

   要搜索sling反向链接属性，请在&#x200B;**Mac**&#x200B;中按&#x200B;**Command+F**，在&#x200B;**Windows**&#x200B;中按&#x200B;**Control+F**。

1. 选中&#x200B;**允许为空**&#x200B;选项，如下图所示。

   ![图像](assets/config/empty-ref2.png)

1. 单击&#x200B;**保存**&#x200B;以启用Apache Sling引用过滤器允许为空。

## 在5分钟内创建数字标牌体验 {#creating-a-digital-signage-experience-in-minutes}

### 创建AEM Screens项目 {#creating-project}

第一步是创建一个AEM Screens项目。

1. 导航到您的Adobe Experience Manager (AEM)实例，然后单击&#x200B;**Screens**。 或者，您也可以直接从`https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`导航。

1. 单击&#x200B;**创建Screens项目**，以便您可以创建Screens项目。
1. 将标题输入为&#x200B;**DemoScreens**，然后单击&#x200B;**保存**。

   ![图像](assets/kickstart/demo-1.png)

   >[!NOTE]
   >创建项目后，将返回到AEM Screens项目主页。 您现在可以单击项目。 在项目中，有五个标题为&#x200B;**应用程序**、**渠道**、**设备**、**位置**&#x200B;和&#x200B;**计划**&#x200B;的不同文件夹。

### 创建渠道 {#creating-channel}

创建AEM Screens项目后，创建一个用于管理内容的渠道。

请按照以下步骤为您的项目创建渠道：

1. 创建项目后，单击&#x200B;**DemoScreens**&#x200B;项目，然后单击&#x200B;**Channels**&#x200B;文件夹，如下图所示。 从操作栏中单击&#x200B;**+创建**。

   ![图像](assets/kickstart/demo-2.png)

1. 从向导中选择&#x200B;**序列频道**，然后单击&#x200B;**下一步**。
   ![图像](assets/kickstart/demo-3.png)

1. 输入&#x200B;**标题**&#x200B;作为&#x200B;**TestChannel**，然后单击&#x200B;**创建**。

   ![图像](assets/kickstart/demo-4.png)

   **TestChannel**&#x200B;现已添加到您的渠道文件夹中，如下图所示。

   ![图像](assets/kickstart/demo-5.png)

### 向渠道添加内容 {#adding-content}

设置好渠道后，将内容添加到AEM Screens Player可以显示的渠道。

请按照以下步骤将内容添加到您项目中的渠道(**TestChannel**)：

1. 导航到您创建的&#x200B;**DemoProject**，然后单击&#x200B;**Channels**&#x200B;文件夹中的&#x200B;**TestChannel**。

1. 在操作栏中单击&#x200B;**编辑**（参见下图）。 **TestChannel**&#x200B;的编辑器打开。

   ![图像](assets/kickstart/demo-6.png)

1. 单击用于切换操作栏左侧的侧面板的图标以打开资源和组件。

1. 拖放要添加到渠道的组件。

   ![图像](assets/kickstart/demo-7.png)

### 创建位置 {#creating-location}

准备好渠道后，创建一个位置。

>[!NOTE]
>***位置***&#x200B;将您的各种数字标牌体验划分开来，并根据各种屏幕的位置包含显示器的配置。

请按照以下步骤为您的项目创建位置：

1. 导航到您创建的&#x200B;**演示项目**，然后单击&#x200B;**位置**&#x200B;文件夹。
1. 从操作栏中单击&#x200B;**+创建**。
1. 单击向导中的&#x200B;**位置**，然后单击&#x200B;**下一步**。
1. 输入您所在位置的&#x200B;**Name**（输入标题为&#x200B;**TestLocation**），然后单击&#x200B;**创建**。

已创建&#x200B;**TestLocation**&#x200B;并将其添加到您的&#x200B;**位置**&#x200B;文件夹。


### 创建位置显示 {#creating-display}

创建位置后，为您的位置创建一个显示。

>[!NOTE]
>***Display***&#x200B;表示在一个或多个屏幕上运行的数字体验。

1. 导航到&#x200B;**TestLocation**&#x200B;并单击它。
1. 单击操作栏中的&#x200B;**创建**。

   ![图像](assets/kickstart/demo-disp1.png)

1. 从&#x200B;**创建**&#x200B;向导中单击&#x200B;**显示**，然后单击&#x200B;**下一步**。

   ![图像](assets/kickstart/demo-disp2.png)

1. 输入&#x200B;**Title**&#x200B;作为&#x200B;**LobbyDisplay**，然后单击&#x200B;**创建**。

   ![图像](assets/kickstart/demo-disp3.png)

   标题为&#x200B;**TestDisplay**&#x200B;的新显示现已添加到您的位置&#x200B;**TestLocation**，如下图所示。

   ![图像](assets/kickstart/demo-disp4.png)

### 分配渠道 {#assigning-channel}

项目设置完成后，将渠道分配给显示区，以查看内容。

1. 从&#x200B;**DemoScreens** > **位置** > **TestLocation** > **LobbyDisplay**&#x200B;导航到所需的显示。

1. 单击操作栏中的&#x200B;**分配渠道**。

   ![图像](assets/kickstart/demo-assign1.png)

   或者，

   在操作栏中单击&#x200B;**仪表板**，然后在&#x200B;**“已分配的渠道和计划”**&#x200B;面板中单击&#x200B;**+分配渠道**。

   ![图像](assets/kickstart/demo-assign2.png)

1. **渠道分配**&#x200B;对话框打开。

1. 从&#x200B;**设置**&#x200B;选项中，按路径&#x200B;**和**&#x200B;支持的事件&#x200B;**选择频道**，例如&#x200B;**初始加载**&#x200B;和&#x200B;**空闲屏幕**。

   >[!NOTE]
   >
   >默认情况下会填充&#x200B;**渠道角色**、**优先级**&#x200B;和&#x200B;**中断方法**。 有关渠道分配属性的更多信息，请参阅[渠道属性](/help/user-guide/channel-assignment-latest-fp.md#channel-properties)部分。

   ![图像](assets/kickstart/demo-assign3.png)

   此外，您还可以单击&#x200B;**激活窗口**&#x200B;和&#x200B;**周期性计划**。

   >[!NOTE]
   >*周期性计划*允许您为渠道设置周期性计划。 您可以为一个渠道设置多个周期性计划。
   >有关详细信息，请参阅[周期性计划](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule)。

1. 配置首选项后，单击&#x200B;**保存**。

### 注册设备并将设备分配给显示器 {#registering-device}

使用AEM仪表板注册设备。

>[!IMPORTANT]
>在开发人员模式下，Chrome OS播放器可安装为Chrome浏览器插件，而无需实际的Chrome Player设备。 要安装，请执行以下步骤：
>
>1. 单击[此处](https://download.macromedia.com/screens/)下载最新的Chrome播放器。
>1. 解压缩并将其保存在磁盘上。
>1. 打开Chrome浏览器，然后单击菜单中的&#x200B;**扩展**，或直接导航到&#x200B;***chrome://extensions***。
>1. 从右上角打开&#x200B;**开发人员模式**。
>1. 从左上角单击&#x200B;**加载解压缩**，然后加载解压缩的Chrome Player。
>1. 如果扩展列表中有&#x200B;**AEM Screens Chrome Player**&#x200B;插件，请选中该插件。
>1. 打开新选项卡并单击左上角的&#x200B;**应用程序**&#x200B;图标，或直接导航到&#x200B;***chrome://apps***。
>1. 单击&#x200B;**AEM Screens**&#x200B;插件，以便启动Chrome Player。 默认情况下，播放器将以全屏模式启动。 按&#x200B;**Esc**&#x200B;退出全屏模式。

打开Chrome OS播放器后，请按照以下步骤注册Chrome设备。

1. 从AEM实例导航到项目的&#x200B;**设备**&#x200B;文件夹。

1. 单击操作栏中的&#x200B;**设备管理器**。

   ![图像](assets/kickstart/demo-register1.png)

1. 单击右上角的&#x200B;**设备注册**。

1. 单击所需的设备，然后单击&#x200B;**注册设备**。

   ![图像](assets/kickstart/demo-register2.png)

1. 等待设备发送其注册码，同时从Chrome设备检查&#x200B;**注册码**。
   ![图像](assets/kickstart/demo-register3.png)

1. 如果两台计算机上的&#x200B;**注册码**&#x200B;相同，请单击AEM中的&#x200B;**验证**。

1. 将设备所需的名称设置为&#x200B;**ChromeDeviceforDemo**，然后单击&#x200B;**注册**。

   ![图像](assets/kickstart/demo-register4.png)

1. 在&#x200B;**设备注册成功**&#x200B;对话框中单击&#x200B;**分配显示区**。

   ![图像](assets/kickstart/demo-register5.png)

1. 单击显示为&#x200B;**DemoScreens** > **位置** > **TestLocation** > **LobbyDisplay**&#x200B;的路径，然后单击&#x200B;**分配**。

   ![图像](assets/kickstart/demo-device6.png)

1. 成功分配设备后，您将看到以下确认。

   ![图像](assets/kickstart/demo-register8.png)

1. 单击&#x200B;**完成**&#x200B;以完成注册过程。 您现在可以从显示仪表板查看已注册的设备。

   ![图像](assets/kickstart/demo-register9.png)

### 在Chrome播放器中查看内容 {#viewing-content-output}

渠道中的所有资源现在都可在Chrome OS播放器上播放。

恭喜您现在在AEM Screens渠道中播放内容！

![图像](assets/kickstart/demo-video-screens.gif)
