---
title: 踢球指南
seo-title: 踢球指南
description: 可查看本页以创建演示AEM Screens项目。 它可帮助您创建从安装和设置新项目开始的数字标牌体验，以便在AEM Screens播放器中查看您的内容。
translation-type: tm+mt
source-git-commit: f2fef18cc73825b3f062a79c560097e8fd00ac9f
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 6%

---


# 踢球指南 {#kickstart-guide}

本部分是AEM Screens的启动，并演示如何设置和运行AEM Screens项目。 它指导您设置基本的数字标牌体验，向每个渠道添加资产和／或视频等内容，并进一步将内容发布到AEM Screens播放器。

>[!NOTE]
>在开始处理项目详细信息之前，请确保已安装最新的功能包。 您可以使用您的AEM Screens从软件分发门户下载Adobe ID6.5.5版 [的最新功能](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 包。

## 在5分钟内创建数字标牌体验 {#creating-a-digital-signage-experience-in-minutes}

请按照以下步骤为AEM Screens创建示例项目，并进一步将内容发布到Screens播放器。

>[!NOTE]
>以下教程展示在Chrome OS播放器中播放渠道的内容。

>[!IMPORTANT]
>**OSGi配置设置**
>您需要启用空推荐人才能允许设备向服务器发布数据。 例如，如果禁用了空推荐人属性，则设备将无法发布屏幕截图。 目前，其中一些功能仅在OSGi配置中启用了Apache Sling推荐人过滤器允许空时才可用。 仪表板可能会显示警告，指出安全设置可能会阻止某些功能正常工作。
>请按照以下步骤启用Apache ***Sling推荐人过滤器允许空***:


## 允许空推荐人请求 {#allow-empty-referrer-requests}

1. 通过AEM **实例** —>锤子图标—>操作—> Web Console **，导航到** Adobe Experience Manager **Web Console** Configuration。

   ![图像](assets/config/empty-ref1.png)

1. **Adobe Experience ManagerWeb控制台配置** 打开。 搜索吊带推荐人。

   要搜索sling推荐人属性， **请按Command** +F( **Mac)****和** Control+F(Windows ****)。

1. 选中“ **允许空** ”选项，如下图所示。

   ![图像](assets/config/empty-ref2.png)

1. 单击 **“保存** ”以启用Apache Sling推荐人过滤器“允许为空”。


## 教程 {#tutorial}

### Creating a new AEM Screens Project {#creating-project}

第一步是创建一个新的AEM Screens项目。

1. 导航到您的Adobe Experience Manager(AEM)实例，然后单击“屏 **幕”**。 或者，您也可以直接从中导 `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`航。

1. Click **Create Screens Project** to create a new Screens project. Enter the title as **DemoScreens** and click **Save**.

   ![图像](assets/kickstart/demo-1.png)

   >[!NOTE]
   >创建项目后，它将您带回到“Screens项目”主页。 现在，您可以选择自己的项目。在项目中，有五个不同的文件夹，标题 **为** Applications ****、 **渠道****、**&#x200B;设备、位 **置、**&#x200B;和计划。


### 创建新渠道 {#creating-channel}

项目就位后，您需要创建新渠道来管理内容。

请按照以下步骤为项目创建新渠道:

1. 创建项目后，选择 **DemoScreens项** 目 **，然后选择**&#x200B;渠道文件夹，如下图所示。 Click **+ Create** from the action bar.

   ![图像](assets/kickstart/demo-2.png)

1. 从向导 **中选择序列渠道** ，然后单击“下 **一步”**。
   ![图像](assets/kickstart/demo-3.png)

1. Enter the **Title** as *TestChannel* and click **Create**.

   ![图像](assets/kickstart/demo-4.png)

将 *创建TestChannel* 并将其添加到您的渠道文件夹，如下图所示。

![图像](assets/kickstart/demo-5.png)

### Adding Content to a Channel {#adding-content}

渠道就位后，您需要向渠道添加内容，Screens播放器将显示这些内容。

请按照以下步骤将内容添加到项&#x200B;*目渠道*(TestChannel):

1. Navigate to the *Test_Project* you created and select the **Channels** folder.

1. Click **Edit** from the action bar (see the figure below). The editor for the *TestChannel* opens.

1. 单击操作栏左侧用于切换侧面板的图标以打开资产和组件。

1. 将您希望添加的组件拖放到渠道中。

   ![chlimage_1-8](assets/chlimage_1-8.png)

在此示例中，编辑器显示添加到渠道的图像。

![chlimage_1-9](assets/chlimage_1-9.png)

### 创建新位置 {#creating-location}

渠道到位后，您需要创建位置。

***位置*** ，将您的各种数字标牌体验划分为不同的区域，并根据不同屏幕的位置包含显示屏的配置。

请按照以下步骤为项目创建新位置：

1. Navigate to the *Test_Project* you created and select the **Locations** folder.

1. 单 **击操** 作栏中加号图标旁边的“创建”（请参阅下图）。 此时将打开一个向导。
1. Select **Location** from the wizard and click **Next**.

1. Enter the **Name** and **Title** for your location (enter the title as *TestLocation*) and click **Create**.

   ![chlimage_1-10](assets/chlimage_1-10.png)

将创 *建TestLocation* 并将其添加到您的 **Locations** 文件夹。

![chlimage_1-11](assets/chlimage_1-11.png)

### 为TestLocation创建新显示屏 {#creating-display}

创建位置后，您需要为位置创建新显示屏。

***显示*** ，代表在一个或多个屏幕上运行的数字体验。

1. 导航到要创建显示屏(Test_*Project —*>位置 **—** > TestLocation) *的位置，如上图所示，并* 选择TestLocation **。

1. 单击操作栏中的&#x200B;**创建**。
1. Select **Display** from the **Create** wizard and click **Next**.

1. 为显 **示位** 置输 **入名称** 和标题(输入TestDisplay *作为标*&#x200B;题)。

1. Under the **Display** tab, choose the details of the Layout.

   1. Choose the **Resolution** as **Full HD**.

   1. Choose the **Number of Devices Horizontally** as 1.

   1. Choose the **Number of Devices Vertically** as 1.

   1. 单击&#x200B;**创建**。

新显示屏(*TestDisplay*)将添加到您 *的位置TestLocation*，如下图所示。

![chlimage_1-12](assets/chlimage_1-12.png)

### 分配渠道 {#assigning-channel}

1. Navigate to the display from *Test_Project* --> **Locations** --> *TestLocation* --> *TestDisplay*.

1. Select *TestDisplay* and tap/click **Assign Channel **from the action bar, *Or*,

1. Click **Dashboard** and select **+Assign Channel** at the top right from **ASSIGNED CHANNELS &amp; SCHEDULES** panel, as shown in the figure below. **渠道分配** (Adobe Assignment)对话框打开。

1. Select **Reference Channel** by **path**

1. Enter the **Channel Role** as *LiveStream*.

1. 在渠道中 **选择** “渠道路&#x200B;*径* ”( *Test_Project* —>渠道 *—*****>测试通道”)。

1. Select the **Priority** for this channel as *1*.

1. Choose the **Supported Events** as **Initial Load** and **Idle Screen**.

1. 输入 **计划** ，并选择有效日期 **的起始日期** , **有效日期**。

1. 单击&#x200B;**保存**。

渠道会创建并添加到面板。

![chlimage_1-15](assets/chlimage_1-15.png)

### 注册设备 {#registering-device}

您需要使用AEM仪表板注册设备。

>[!NOTE]
>您可以使用您下载的AEM Screens应用程序或Web浏览器打开Screens播放器。



### Viewing the content in AEM Screens Player {#viewing-the-content-in-screens-player}

添加上述配置后，播放器应自动显示设备上显示屏的默认渠道。

![chlimage_1-23](assets/chlimage_1-23.png)

请参 [阅AEM Screens](working-with-screens-player.md) Player以获取有关AEM Screens播放器的更多详细信息。
