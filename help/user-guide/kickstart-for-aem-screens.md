---
title: Kickstart指南
description: 了解如何创建演示AEM Screens项目。 它可帮助您创建数字标牌体验，从安装和设置新项目开始，一直到在AEM Screens播放器中查看内容。
feature: Overview, Digital Signage
role: User
level: Beginner
exl-id: 9b7c7f50-2846-4727-a0ec-0220b4cd52c4
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '1279'
ht-degree: 2%

---

# Kickstart指南 {#kickstart-guide}

AEM Screens快速入门演示了如何设置和运行AEM Screens项目。 它将指导您逐步建立基本的数字标牌体验，并向每个渠道添加内容（如资产和/或视频），然后进一步将内容发布到AEM Screens播放器。

>[!NOTE]
>在处理项目详细信息之前，请确保已安装了适用于AEM Screens的最新功能包。 您可以从以下网站下载最新的功能包： [软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。

## 先决条件 {#prerequisites}

请按照以下步骤为AEM Screens创建一个示例项目，然后将内容进一步发布到Screens播放器。

>[!NOTE]
>以下教程展示了如何在Chrome OS播放器中播放渠道的内容。

>[!IMPORTANT]
>**osgi配置设置**
>必须启用空反向链接以允许设备向服务器发布数据。 例如，如果禁用empty referrer属性，设备将无法张贴屏幕快照。 目前，其中某些功能仅在OSGi配置中启用Apache Sling反向链接过滤器允许空后才可用。 仪表板可能会显示警告，指出安全设置可能会阻止这些功能中的某些功能正常工作。
>请按照以下步骤启用 ***Apache Sling引用过滤器允许为空***：


## 允许空反向链接请求 {#allow-empty-referrer-requests}

1. 导航到 **Adobe Experience Manager Web控制台配置** 通过AEM实例>锤子图标> **操作** > **Web控制台**.

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web控制台配置** 打开。 搜索Sling反向链接。

   要搜索sling反向链接属性，请按 **Command+F** 对象 **Mac** 和 **Control+F** 对象 **Windows**.

1. 查看 **允许为空** 选项，如下图所示。

   ![图像](assets/config/empty-ref2.png)

1. 单击 **保存** 以启用Apache Sling引用过滤器允许为空。

## 在5分钟内创建数字标牌体验 {#creating-a-digital-signage-experience-in-minutes}

### 创建AEM Screens项目 {#creating-project}

第一步是创建一个AEM Screens项目。

1. 导航到您的Adobe Experience Manager (AEM)实例，然后单击 **Screens**. 或者，您可以直接从以下位置导航： `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. 单击 **创建屏幕项目** 以便创建屏幕项目。
1. 输入标题为 **DemoScreens**，然后单击 **保存**.

   ![图像](assets/kickstart/demo-1.png)

   >[!NOTE]
   >创建项目后，您将返回到屏幕项目主页。 您现在可以选择您的项目。 在项目中，有五个标题为 **应用程序**， **渠道**， **设备**， **位置**、和 **时间表**.

### 创建渠道 {#creating-channel}

创建AEM Screens项目后，必须创建一个用于管理内容的渠道。

请按照以下步骤为您的项目创建渠道：

1. 创建项目后，选择 **DemoScreens** 项目并选择 **渠道** 文件夹，如下图所示。 单击 **+创建** 从操作栏中。

   ![图像](assets/kickstart/demo-2.png)

1. 选择 **序列渠道** 在向导中单击 **下一个**.
   ![图像](assets/kickstart/demo-3.png)

1. 输入 **标题** 作为 **TestChannel** 并单击 **创建**.

   ![图像](assets/kickstart/demo-4.png)

   此 **TestChannel** 现已添加到您的渠道文件夹中，如下图所示。

   ![图像](assets/kickstart/demo-5.png)

### 向渠道添加内容 {#adding-content}

设置好渠道后，将内容添加到AEM Screens播放器可以显示的渠道。

请按照以下步骤将内容添加到渠道(**TestChannel**)：

1. 导航至 **演示项目** 您已创建并选择 **TestChannel** 从 **渠道** 文件夹。

1. 单击 **编辑** 从操作栏中（参见下图）。 的编辑器 **TestChannel** 打开。

   ![图像](assets/kickstart/demo-6.png)

1. 单击用于切换操作栏左侧的侧面板的图标以打开资源和组件。

1. 拖放要添加到渠道的组件。

   ![图像](assets/kickstart/demo-7.png)

### 创建位置 {#creating-location}

准备好渠道后，创建一个位置。

>[!NOTE]
>***位置*** 将您的各种数字标牌体验划分开来，并根据各种屏幕的位置包含显示器的配置。

请按照以下步骤为您的项目创建位置：

1. 导航至 **演示项目** 您已创建并选择 **位置** 文件夹。
1. 单击 **+创建** 从操作栏中。
1. 选择 **位置** 在向导中单击 **下一个**.
1. 输入 **名称** (输入标题为 **TestLocation**)，然后单击 **创建**.

此 **TestLocation** 创建并添加到您的 **位置** 文件夹。


### 创建位置显示 {#creating-display}

创建位置后，为您的位置创建一个显示。

>[!NOTE]
>***显示*** 表示在一个或多个屏幕上运行的数字体验。

1. 导航至 **TestLocation** 并选择它。
1. 单击 **创建** 从操作栏中。

   ![图像](assets/kickstart/demo-disp1.png)

1. 选择 **显示** 从 **创建** 向导并单击 **下一个**.

   ![图像](assets/kickstart/demo-disp2.png)

1. 输入 **标题** 作为 **LobbyDisplay** 并单击 **创建**.

   ![图像](assets/kickstart/demo-disp3.png)

   标题为 **TestDisplay** 现已添加到您的位置 **TestLocation**，如下图所示。

   ![图像](assets/kickstart/demo-disp4.png)

### 分配渠道 {#assigning-channel}

项目设置完成后，必须将渠道分配给显示区，以查看内容。

1. 从以下位置导航到所需的显示区 **DemoScreens** > **位置** > **TestLocation** > **LobbyDisplay**.

1. 点按/单击 **分配渠道** 从操作栏中。

   ![图像](assets/kickstart/demo-assign1.png)

   或者，

   点按/单击 **仪表板** 操作栏中，然后单击 **+指定渠道** 从 **已分配的渠道和计划** 面板。

   ![图像](assets/kickstart/demo-assign2.png)

1. 此 **渠道分配** 对话框打开。

1. 从 **设置** 选项，选择渠道 **按路径**  和 **受支持的事件** 作为 **初始加载** 和 **空闲屏幕**.

   >[!NOTE]
   >
   >此 **渠道角色**， **优先级**、和 **中断方法** 默认情况下全部填充。 请参阅 [渠道属性](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) 部分以了解有关渠道分配属性的更多信息。

   ![图像](assets/kickstart/demo-assign3.png)

   此外，您还可以选择 **激活窗口** 和 **周期性计划**.

   >[!NOTE]
   >此 *周期性计划* 允许您为渠道设置定期计划。 您可以为一个渠道设置多个周期性计划。
   >请参阅 [周期性计划](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) 以了解更多详细信息。

1. 单击 **保存** 配置您的首选项后。

### 注册设备并将设备分配给显示器 {#registering-device}

使用AEM仪表板注册设备。

>[!IMPORTANT]
>在开发人员模式下，Chrome操作系统播放器可以安装为Chrome浏览器插件，而无需实际的Chrome播放器设备。 要安装，请执行以下步骤：
>
>1. 单击 [此处](https://download.macromedia.com/screens/) 以下载最新的Chrome播放器。
>1. 解压缩并将其保存在磁盘上。
>1. 打开Chrome浏览器并选择 **扩展** 或直接导航到 ***chrome://extensions***.
>1. 打开 **开发人员模式** 从右上角。
>1. 单击 **加载已解压缩** 从左上角，加载解压的Chrome播放器。
>1. Check **AEM Screens Chrome Player** 插件（如果在扩展列表中可用）。
>1. 打开新选项卡，然后单击 **应用程序** 图标，或直接导航到 ***chrome://apps***.
>1. 单击 **AEM Screens** 插件，以便您能够启动Chrome Player。 默认情况下，播放器将以全屏模式启动。 按 **Esc** 退出全屏模式。

打开Chrome OS播放器后，请按照以下步骤注册Chrome设备。

1. 导航至 **设备** 从AEM实例中删除项目文件夹。

1. 点按/单击 **设备管理器** 从操作栏中。

   ![图像](assets/kickstart/demo-register1.png)

1. 点按/单击 **设备注册** 从右上角。

1. 选择所需的设备，然后点按/单击 **注册设备**.

   ![图像](assets/kickstart/demo-register2.png)

1. 等待设备发送其注册码，同时检查 **注册码** 从您的Chrome设备中。
   ![图像](assets/kickstart/demo-register3.png)

1. 如果 **注册码** 两台计算机上相同，请点按/单击 **验证** 在AEM中。

1. 将所需名称设置为 **ChromeDeviceforDemo** （对于设备），然后单击 **注册**.

   ![图像](assets/kickstart/demo-register4.png)

1. 单击 **分配显示区** 从 **设备注册成功** 对话框。

   ![图像](assets/kickstart/demo-register5.png)

1. 选择显示方式 **DemoScreens** > **位置** > **TestLocation** > **LobbyDisplay** 并单击 **分配**.

   ![图像](assets/kickstart/demo-device6.png)

1. 成功分配设备后，您将看到以下确认。

   ![图像](assets/kickstart/demo-register8.png)

1. 选择 **完成** 以完成注册流程。 您现在可以从显示仪表板查看已注册的设备。

   ![图像](assets/kickstart/demo-register9.png)

### 在Chrome播放器中查看内容 {#viewing-content-output}

渠道中的所有资产现在都可在Chrome OS播放器上播放。

恭喜您现在在AEM Screens渠道中播放内容！

![图像](assets/kickstart/demo-video-screens.gif)
