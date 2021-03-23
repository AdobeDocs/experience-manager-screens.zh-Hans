---
title: 使用Screens启动项进行内容更新
seo-title: 使用Screens启动项进行内容更新
description: 内容作者可以创建渠道的未来版本（称为启动），并进一步设置此启动项的起始日期，使内容可以在设备或播放器中实时。
seo-description: 内容作者可以创建渠道的未来版本（称为启动），并进一步设置此启动项的起始日期，使内容可以在设备或播放器中实时。
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
feature: 创作屏幕，启动项
role: 管理员、开发人员
level: 中间
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1622'
ht-degree: 0%

---


# 使用Screens启动{#launches}进行内容更新

内容作者可以创建渠道的未来版本（称为&#x200B;**屏幕启动项**），并进一步设置此启动项的起始日期。 这允许内容在指定的发布日期在设备或播放器中实时。

借助&#x200B;***屏幕启动***&#x200B;的帮助，作者可以预览启动项中的每个渠道，并应能够启动审阅请求。 批准者组将获得通知，并可以批准或拒绝请求。 当到达实时日期时，内容将在设备中播放。

例如，如果作者要创建c1、c2(渠道)的未来版本，则会创建启动项并设置起始日期（例如，11月10日上午8:00）。 内容中的任何进一步更新都将发出以供审阅。

批准后，在实时日期（11月10日上午8:00），此启动项将在设备或播放器上播放内容。

## 要求{#requirements}

在开始在AEM Screens项目中利用&#x200B;*Screens Launch*&#x200B;之前，请确保您了解宽限期的概念及其相关性。

在播放器的设置起始日期上运行体验涉及：

* 启动项的提升（通常需要几秒钟）

* 发布资源以发布实例(通常需要几分钟，具体取决于需要发布的渠道或资产的大小)

* 更新脱机内容所花费的时间（通常需要几分钟）

* 播放器从发布实例下载内容所花费的时间（通常需要几分钟，具体取决于需要下载的资源的带宽和大小）

* 服务器和播放器的任何时间差异

### 了解宽限期{#understanding-grace-period}

为了使播放器能够开始在设置的发布日期上播放内容，我们需要在发布日期之前开始前面的活动。

如果起始日期为&#x200B;*11月24日，上午9:00*，宽限期为&#x200B;*24小时*，则上述操作序列将在（起始日期 — 宽限期）（即11月23日，上午9:00服务器时间）开始。 这为完成上述所有操作提供了24小时的时间，内容将触及玩家。 播放器将了解这是一个启动内容，因此内容不会立即播放，但播放器会将此内容存储为将来版本，并将开始在播放器的时区的指定实时日期正确播放。

例如，假设服务器为PST，设备为EST，在这种情况下，最大时差为3小时，并假设从作者开始发布到发布需要10分钟，播放器通常可以在10-15分钟内下载资源。 然后，宽限期=时间差（3小时）+提升启动时间（1分钟）+发布启动时间（10分钟）+在播放器下载时间（10-15分钟）+缓冲区（安全，例如30分钟）= 3小时56分钟= 14160秒。

因此，每当我们实时计划任何启动项时，促销将在此偏移量之前开始。 在上述等式中，大多数项目不需要太多时间，一旦我们知道服务器与任何播放器之间的最大时间差，我们就可以对此偏移量使用适当的猜测。

>[!NOTE]
>
>开箱即用后，Screens启动项的宽限期将设置为24小时，这意味着，当我们在&#x200B;*/content/screens*&#x200B;下为资源的任何启动项设置起始日期时，该促销将开始此偏移。

### 更新现成宽限期{#updating-out-of-the-box-grace-period}

本节介绍如何将现成的宽限期更新为10分钟。

1. 导航到CRXDE Lite，然后导航到`/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`。
2. 右键单击并复制文件。
3. 导航到`/apps/system/config`并右键单击并粘贴。
4. 多次单击`/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`以在CRXDE Lite的编辑器中打开文件。 它必须将路径&#x200B;*/content/screens/*&#x200B;的宽限期显示为&#x200B;**86400**。 将该值更改为&#x200B;**600**。

现在，文本文件中的内容应类似于：

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

由于您已在上例中将宽限期设置为10分钟，因此，当您在&#x200B;*/content/screens*&#x200B;下为资源的任何启动项设置起始日期时，促销将开始此偏移。

例如，如果起始日期设置为11月24日，上午9:00，宽限期为600秒，则促销作业将于11月24日上午8:50开始。

## 使用Screens启动{#using-launches}

本节演示如何在您的AEM Screens项目中实施Screens Launch。

### 创建屏幕启动项{#creating-a-launch}

请按照以下步骤将Screens启动功能实施到您的AEM Screens项目：

1. 在您的AEM Screens项目中创建序列渠道，例如&#x200B;**LaunchesDemo** —> **渠道** —> **FutureLaunch**，如下所示。

   >[!CAUTION]
   >
   >您必须从AEM Screens项目中预先存在的渠道创建启动项。

   ![图像](/help/user-guide/assets/launches-images/launches-11.png)

1. 选择渠道&#x200B;**FutureLaunch**，然后单击操作栏中的&#x200B;**创建启动项**。

   ![图像](/help/user-guide/assets/launches-images/launches-12.png)

1. 将打开&#x200B;**创建启动项**&#x200B;向导。 您可以选择向导中已显示的渠道，或单击&#x200B;**+添加渠道**&#x200B;以添加要为其创建启动项的渠道。

1. 单击&#x200B;**创建启动项**&#x200B;向导中的&#x200B;**下一步**。 默认情况下，**包含子页**&#x200B;选项处于选中状态。

   ![图像](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >可以使用&#x200B;**+添加渠道**&#x200B;选项添加要为其创建启动项的其他渠道。

   要使用&#x200B;**添加渠道**&#x200B;选项，请导航到要为其创建启动项的渠道，然后单击&#x200B;**选择**。

   如果您尝试选择多个渠道或文件夹以添加启动项，将禁用&#x200B;**选择**&#x200B;选项。

   ![图像](/help/user-guide/assets/launches-images/launches-14.png)

   选择渠道/渠道后，单击&#x200B;**下一步**。


1. 将&#x200B;**启动项标题**&#x200B;输入为&#x200B;**SummerPromotions**，您无需设置&#x200B;**启动日期**，如下图所示。 单击&#x200B;**创建**。

   >[!NOTE]
   >
   >*启用或* 选中“ **继承源页** 面Live Data”选项后，渠道可在启动项中创建为Live Copy。如果在原始渠道中进行了任何更改，则这些更改会自动应用于启动渠道。
   >
   >
   >*禁用或取* **消检查继承源页** 面活动数据允许在启动项中复制渠道时不与任何活动关系。因此，如果对原始渠道进行了任何更改，则这些更改不会应用于启动渠道。

   ![图像](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >您可以在此步骤中设置实时启动日期，也可以在稍后编辑启动项的属性时设置该日期（一旦已创建）。

   **了解启动项促销范围**

   * **提升完整启动**:启动项的所有渠道都在设置的起始日期提升。
   * **提升修改的页面**:将只提升已修改的启动资源。建议在不需要启动项审阅时使用此选项。
   * **提升已批准的页面**:此选项要求启动项批准工作流在启动项渠道上运行。只有经过批准的页面才会在设置的起始日期提升。

      >[!CAUTION]
      >
      >启动起始日期以播放器/设备的时区而非服务器为准。

1. 您将看到启动项已创建。 您可以单击&#x200B;**打开**&#x200B;以视图编辑器中的页面，或单击&#x200B;**完成**&#x200B;以导航回您的项目。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   单击&#x200B;**完成**&#x200B;可导航回&#x200B;**FutureLaunch**&#x200B;渠道。

   ![图像](/help/user-guide/assets/launches-images/launches-16.png)


### 编辑启动项属性以设置起始日期和范围{#editing-the-launch-properties-to-set-the-live-date-and-scope}

创建启动项后，您可以使用&#x200B;**启动属性**&#x200B;更新活动日期、启动项标题和升级范围等属性。

* **启动日期**，指实时日期，即根据播放器的时区，内容在Screens播放器中播放的日期或时间。
* **Production Ready**，允许在提升这些现成功能后发布渠道，因此无需更改。
* **范围**，决定在启动升级期间将提升哪些渠道。


请按照以下步骤编辑启动项属性：

1. 导航到渠道&#x200B;**FutureLaunch**、*（即待定启动项）*&#x200B;并选择渠道，如下图所示。

   ![图像](/help/user-guide/assets/launches-images/launches-17.png)

1. 单击操作栏中的&#x200B;**仪表板**，您会看到渠道仪表板中的&#x200B;**挂起的启动项**&#x200B;面板。

   ![图像](/help/user-guide/assets/launches-images/launches-18.png)

1. 选择启动项，然后单击&#x200B;**挂起启动项**&#x200B;面板中的&#x200B;**启动属性**。

   ![图像](/help/user-guide/assets/launches-images/launches-19.png)

### 编辑Screens启动项以添加或删除渠道{#editing-the-screens-launch-to-add-or-remove-channels}

在创建启动项后，可以使用&#x200B;**编辑启动项**&#x200B;选项向现有启动项添加或删除渠道。

完成后，单击&#x200B;**保存**&#x200B;以导航回&#x200B;**FutureLaunch**&#x200B;渠道。

### 手动提升屏幕启动{#promote-the-screens-launch-manually}

您可以使用&#x200B;**挂起启动项**&#x200B;面板中的&#x200B;**提升启动项**&#x200B;选项手动提升启动项。

您可以在&#x200B;**启动升级向导**&#x200B;中选择要升级的资源，作为此手动升级的一部分。

![图像](/help/user-guide/assets/launches-images/launches-e.png)

1. 您可以启用或禁用此选项，以在生产后删除启动项。
1. 您可以设置启动项的&#x200B;**范围**，具有以下选项：
   1. **提升完整启动**:启动项的所有渠道都在设置的起始日期提升。
   1. **提升修改的页面**:将只提升已修改的启动资源。建议在不需要启动项审阅时使用此选项。
   1. **提升已批准的页面**:此选项要求启动项批准工作流在启动项渠道上运行。只有经过批准的页面才会在设置的起始日期提升。
   1. **提升当前页面**:此选项要求启动项批准工作流仅针对当前页面运行。
1. 单击&#x200B;**提升启动项**&#x200B;向导中的&#x200B;**下一步**。
1. 单击&#x200B;**提升**&#x200B;以提升启动项。

### 删除屏幕启动{#deleting-the-screens-launch}

您可以使用&#x200B;**删除启动项**&#x200B;选项从&#x200B;**挂起启动项**&#x200B;面板中删除启动项。

>[!CAUTION]
>
>此操作还将删除所有子体（嵌套启动项）。

