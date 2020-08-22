---
title: 使用Screens启动进行内容更新
seo-title: 使用Screens启动进行内容更新
description: 内容作者可以创建渠道的未来版本（称为启动），并进一步设置此启动项的起始日期，使内容可以在设备或播放器中实时。
seo-description: 内容作者可以创建渠道的未来版本（称为启动），并进一步设置此启动项的起始日期，使内容可以在设备或播放器中实时。
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
translation-type: tm+mt
source-git-commit: 081db31efda17ac12cdc88f79ed2f4e1fbfc7edf
workflow-type: tm+mt
source-wordcount: '1616'
ht-degree: 0%

---


# 使用Screens启动进行内容更新 {#launches}

内容作者可以创建渠道的未来版本(称为“屏 **幕启动** ”)，并进一步设置此启动的起始日期。 这允许内容在指定的发布日期在设备或播放器中实时。

借助Screens Launch ***的帮助***，作者可以预览启动项中的每个渠道，并应能够启动审核请求。 批准者组将获得通知，并可以批准或拒绝请求。 当到达实时日期时，内容将在设备中播放。

例如，如果作者要创建c1、c2(渠道)的未来版本，则会创建启动项并设置起始日期（例如，11月10日上午8:00）。 内容中的任何进一步更新都将发出以供审阅。

批准后，在实时日期（11月10日上午8:00），此启动项将在设备或播放器上播放内容。

## 要求 {#requirements}

在开始在 *AEM Screens项* 目中利用Screens Launch之前，请确保您了解宽限期的概念及其相关性。

在播放器的设定起始日期运行体验涉及：

* 启动项的提升（通常需要几秒钟）

* 发布资源以发布实例(通常需要几分钟，具体取决于需要发布的渠道或资产的大小)

* 更新脱机内容完成所花费的时间（通常需要几分钟）

* 播放器从发布实例下载内容所花费的时间（通常需要几分钟，具体取决于需要下载的资源的带宽和大小）

* 服务器和播放器的任何时间差异

### 了解宽限期 {#understanding-grace-period}

为了使播放器能够开始在设定的发布日期上播放内容，我们需要在发布日期之前开始前面的活动。

如果起始日期为 *11月24日，上午9:00* ，宽限期为 *24小时*，则上述操作序列将在（起始日期——宽限期）（即11月23日，上午9:00服务器时间）开始。 这为完成上述所有操作提供了24小时的时间，内容将触及玩家。 玩家将了解这是一个启动内容，因此内容不会立即播放，但玩家将将此内容存储为未来版本，并将开始在玩家的时区上的预定实时日期正确播放。

例如，假设服务器在太平洋标准时间内，设备在东部标准时间内，最大时差为3小时，在这种情况下，假设从作者到发布的升级需要1分钟，发布需要10分钟，播放器通常可以在10-15分钟内下载资源。 然后，宽限期=时间差（3小时）+提升启动时间（1分钟）+发布启动时间（10分钟）+在播放器下载时间（10-15分钟）+缓冲区（安全，例如30分钟）= 3小时56分钟= 14160秒。

因此，每当我们实时计划任何启动项时，促销将在此偏移量下提前开始。 在上述等式中，大多数项目不需要太多时间，一旦我们知道服务器与任何播放器之间的最大时间差，我们就可以对此偏移量使用适当的猜测。

>[!NOTE]
>
>开箱即用时，屏幕启动项的宽限期设置为24小时，这意味着当我们为/content/screens下的资源的任何启动项设置起始日期时 **，促销将开始此偏移。

### 更新现成宽限期 {#updating-out-of-the-box-grace-period}

本节介绍如何将现成的宽限期更新为10分钟。

1. 导航到CRXDE Lite，然后导航到 `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`。
2. 右键单击并复制文件。
3. 导航到 `/apps/system/config` 并右键单击并粘贴。
4. 多次单 `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` 击以CRXDE Lite在编辑器中打开文件。 它必须将路径／内容／屏 *幕／的宽限期* 显示 **为86400**。 将该值更改 **为600**。

现在，文本文件中的内容应类似于：

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

由于您已在上一个示例中将宽限期设置为10分钟，因此，当您在/content/screens下为资源的任何启动项设置 *起始日期时*，促销将开始此偏移。

例如，如果起始日期设置为11月24日，上午9:00，宽限期为600秒，则促销作业将于11月24日上午8:50开始。

## 使用屏幕启动 {#using-launches}

本节演示如何在您的AEM Screens项目中实施Screens Launch。

### 创建屏幕启动项 {#creating-a-launch}

请按照以下步骤对您的AEM Screens项目实施Screens启动功能：

1. 在您的AEM Screens项目中创建序列渠道, **例如** LaunchesDemo — **>****渠道**—> FutureLaunch，如下所示。

   >[!CAUTION]
   >
   >您必须从AEM Screens项目中的现有渠道创建启动项。

   ![图像](/help/user-guide/assets/launches-images/launches-11.png)

1. 选择渠道 **FutureLaunch** ，然后 **单击操作栏** 中的创建启动项。

   ![图像](/help/user-guide/assets/launches-images/launches-12.png)

1. 此时 **将打开创建** 启动项向导。 您可以选择向导中已显示的渠道，或单击 **+添加渠道** ，以添加要为其创建启动项的渠道。

1. 单击 **创建** 启动 **项向导中的下** 一步。 默认 **情况下** ,“包括子页面”选项处于选中状态。

   ![图像](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >您可以使用 **+添加渠道** 选项来添加要为其创建启动项的其他渠道。

   要使用 **添加渠道** ，请导航到要为其创建启动项的渠道，然后单击选 **择**。

   如果 **您尝试** 选择多个渠道或文件夹来添加启动项，则将禁用选择选项。

   ![图像](/help/user-guide/assets/launches-images/launches-14.png)

   选择渠道/渠道后，单击“下 **一步**”。


1. 将启动 **项标题输****入SummerPromotions** ，您无需设置启 **动日期**，如下图所示。 单击&#x200B;**创建**。

   >[!NOTE]
   >
   >*启用或选中* “继 **承源页面Live Data** ”选项，可在启动项中将渠道创建为Live Copy。 如果在原始渠道中进行了任何更改，则这些更改会自动应用于启动渠道。
   >
   >
   >*禁用或取消选* 中“继承源页面 **** ”活动渠道允许复制，而在启动项中没有任何活动关系。 因此，如果对原始渠道进行了任何更改，则这些更改不会应用于启动渠道。

   ![图像](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >您可以在此步骤中设置实时启动日期，也可以在启动项创建后编辑其属性时稍后设置它。

   **了解启动项提升范围**

   * **提升完整启动**:启动项的所有渠道在设置的起始日期提升。
   * **提升修改的页面**:将只提升修改的启动资源。 建议在不需要启动项审阅时使用此选项。
   * **提升已批准的页面**:此选项要求启动项批准工作流在启动渠道上运行。 只有经过批准的页面才会在设置的起始日期进行提升。

      >[!CAUTION]
      >
      >启动起始日期采用播放器／设备的时区，而非服务器的时区。

1. 您将看到已创建启动项。 您可以单击“打 **开** ”以视图编辑器中的页面，或 **单击“完** 成”以导航回您的项目。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   单击 **完成** ，即可导航回 **FutureLaunch** 渠道。

   ![图像](/help/user-guide/assets/launches-images/launches-16.png)


### 编辑启动项属性以设置起始日期和范围 {#editing-the-launch-properties-to-set-the-live-date-and-scope}

在创建启动项后，您可以使用启动项属性更新诸如起始日期、启动项标题和升级范 **围等属性**。

* **启动日期**，指实时日期，即根据播放器的时区在Screens播放器中播放内容的日期或时间。
* **Production Ready**，允许渠道在升级这些现成功能后发布，因此无需更改它。
* **范围**，决定在启动升级期间将提升哪些渠道。


请按照以下步骤编辑启动项属性：

1. 导航到 **渠道Future** Launch( *即待定启动项)* ，然后选择渠道，如下图所示。

   ![图像](/help/user-guide/assets/launches-images/launches-17.png)

1. 单击操 **作栏** 中的仪表板，您会看到 **渠道仪表板中** 的“待定启动项”面板。

   ![图像](/help/user-guide/assets/launches-images/launches-18.png)

1. 选择启动项，然后单 **击“待定** ”启动 **项面板中的启动属性** 。

   ![图像](/help/user-guide/assets/launches-images/launches-19.png)

### 编辑屏幕启动项以添加或删除渠道  {#editing-the-screens-launch-to-add-or-remove-channels}

创建启动项后，可以使用编辑启动项选项向现有启动项添加或 **删除渠道** 。

完成后，单击保 **存** ，导航回 **FutureLaunch** 渠道。

### 手动提升屏幕启动{#promote-the-screens-launch-manually}

您可以使用“待定启动项”面板 **中的提升启** 动项选 **项手动提升启动项** 。

您可以在启动升级向导中选择要升级的资源，作为此手动升级的 **一部分**。

![图像](/help/user-guide/assets/launches-images/launches-e.png)

1. 您可以启用或禁用此选项以在生产后删除启动项。
1. 您可以设置 **启动** 的范围，具有以下选项：
   1. **提升完整启动**:启动项的所有渠道在设置的起始日期提升。
   1. **提升修改的页面**:将只提升修改的启动资源。 建议在不需要启动项审阅时使用此选项。
   1. **提升已批准的页面**:此选项要求启动项批准工作流在启动渠道上运行。 只有经过批准的页面才会在设置的起始日期进行提升。
   1. **提升当前页面**:此选项要求启动项批准工作流仅为当前页面运行。
1. 单击 **提升** 启动 **向导中的下一步** 。
1. 单击 **提升** ，以提升启动项。

### 删除屏幕启动项 {#deleting-the-screens-launch}

您可以使用“待定启动项” **面板中的** “删除启动 **项”选项删除启动项** 。

>[!CAUTION]
>
>此操作还将删除所有子体（嵌套启动项）。

