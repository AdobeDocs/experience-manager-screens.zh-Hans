---
title: 使用Screens启动更新内容
seo-title: 使用Screens启动更新内容
description: 内容作者可以创建渠道的未来版本（称为“启动”），并进一步设置此启动项的发布日期，使内容能够在设备或播放器中实时显示。
seo-description: 内容作者可以创建渠道的未来版本（称为“启动”），并进一步设置此启动项的发布日期，使内容能够在设备或播放器中实时显示。
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
translation-type: tm+mt
source-git-commit: 0f30c01ee936d48a215e0a42eb983daea7fbe731

---


# 使用Screens启动更新内容 {#launches}

内容作者可以创建渠道的未来版本(称为 **Screens启动项** )，并进一步设置此启动项的起始日期。 这允许内容在指定的发布日期在设备或播放器中实时显示。

借助Screens Launch ******，作者可以预览启动项中的每个渠道，并且应能够发起审阅请求。 批准者组将收到通知，并可以批准或拒绝请求。 到达活动日期后，内容将在设备中播放。

例如，如果作者要创建c1、c2(渠道)的未来版本，则会创建启动项并设置起始日期（例如，11月10日上午8:00）。 内容中的任何进一步更新都将发出以供审阅。

批准后，在实时日期（11月10日上午8:00），此启动项将在设备或播放器上播放内容。

## 要求 {#requirements}

在开始在AEM Screens项 *目中启动利用Screens* 之前，请确保您了解宽限期的概念及其相关性。

在播放器的设置起始日期运行体验涉及：

* 启动项的升级（通常需要几秒钟）

* 发布资源以发布实例(通常需要几分钟，具体取决于需要发布的渠道或资产的大小)

* 更新脱机内容所花费的时间（通常需要几分钟）

* 播放器从发布实例下载内容所花费的时间（通常需要几分钟，具体取决于需要下载的资产的带宽和大小）

* 服务器和播放器的任何时间差异

### 了解宽限期 {#understanding-grace-period}

为了使播放器能够开始在设定的发布日期上播放内容，我们需要在发布日期之前开始前面的活动。

如果起始日期为11月24 *日，上午9:00* ，宽限期为 *24小时*，则上述操作序列将在（起始日期——宽限期）（即上午11月23日，上午9:00服务器时间）开始。 这为完成上述所有操作提供了24小时的时间，内容将到达玩家。 播放器将了解这是一个启动内容，因此内容不会立即播放，但播放器会将此内容存储为将来版本，并将在播放器的时区的设置实时日期正确开始播放。

例如，假设服务器在PST中，设备在EST中，最大时间差为3小时，这种情况下，假定从作者开始发布到发布需要10分钟，播放器通常可以在10-15分钟内下载资源。 然后，宽限期=时间差（3小时）+提升启动时间（1分钟）+发布启动时间（10分钟）+在播放器（10-15分钟）下载时间+缓冲时间（要安全，例如30分钟）= 3小时56分钟= 14160秒。

因此，每当我们实时计划任何启动项时，促销活动都会在此偏移量之前提前开始。 在上述等式中，大多数项目不需要太多时间，一旦我们知道服务器与任何播放器之间的最大时间差，我们就可以对此偏移量使用适当的猜测。

>[!NOTE]
>开箱即用时，屏幕启动项的宽限期将设置为24小时，这意味着当我们为 */content/screens下的资源的任何启动项设置起始日期时*，促销将与此偏移开始。

### 更新现成宽限期 {#updating-out-of-the-box-grace-period}

本节介绍如何将现成的宽限期更新为10分钟。

1. 导航到CRXDE Lite，然后导航到 `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`。
2. 右键单击并复制文件。
3. 导航到 `/apps/system/config` 并右键单击并粘贴。
4. 多次单 `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` 击以在CRXDE Lite的编辑器中打开文件。 它必须显示路径／内容／屏 *幕／作为* 86400的宽 **限期**。 将该值更改 **为600**。

现在，文本文件中的内容应类似于：

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

由于您在上一个示例中将宽限期设置为10分钟，因此，当您在 */content/screens下为资源的任何启动项设置起始日期时*，促销将与此偏移开始。

例如，如果实时日期设置为11月24日，上午9:00，宽限期为600秒，则促销作业将于11月24日上午8:50开始。

## 使用Screens启动项 {#using-launches}

请按照以下部分在AEM Screens项目中实施Screens启动。

### 创建屏幕启动项 {#creating-a-launch}

请按照以下步骤将Screens启动功能实施到您的AEM Screens项目：

1. 在AEM Screens项目中创建序列渠道，例如 **LaunchesDemo** —> **渠道** —> **FutureLaunch**，如下所示。

   >[!CAUTION]
   >
   >您必须从AEM Screens项目中的预先存在的渠道创建启动项。

   ![图像](/help/user-guide/assets/launches-images/launches-11.png)

1. 选择渠道 **FutureLaunch** ，然后 **单击操作栏中的创建启动项** 。

   ![图像](/help/user-guide/assets/launches-images/launches-12.png)

1. 此时将 **打开创建启动** 项向导。 您可以选择向导中已显示的渠道，或单击 **+添加渠道** ，以添加要为其创建启动项的渠道。

1. 单击 **创建启动** 向导中 **的下一步** 。 默认 **情况下，“包括子页** ”选项处于选中状态。

   ![图像](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >您可以使 **用+添加渠道** ，以添加要为其创建启动项的其他渠道。

   ![图像](/help/user-guide/assets/launches-images/launches-13.png)

   要使用 **添加渠道** ，请导航到要为其创建启动项的渠道，然后单击选择 ****。

   如果 **您尝试选择多个渠道或用于添加启动项的文件夹，则“选择** ”选项将被禁用。

   ![图像](/help/user-guide/assets/launches-images/launches-14.png)

   选择渠道/渠道后，单击“下 **一步”**。


1. 将启 **动项标题输入****SummerPromotions******，您无需设置启动日期，如下图所示。 单击&#x200B;**创建**。

   >[!NOTE]
   >
   >*启用或选中* “继 **承源页面Live Data** ”选项，可在启动项中将渠道创建为Live Copy。 如果在原始渠道中进行了任何更改，则这些更改会自动应用于启动渠道。
   >
   >
   >*禁用或取消选* 中“继承源页面动态数据 **** ”允许复制渠道，而不会在启动项中产生任何实时关系。 因此，如果对原始渠道进行了任何更改，则这些更改不会应用于启动渠道。

   ![图像](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >您可以在此步骤中设置实时启动日期，也可以在稍后编辑启动项的属性时设置它，直到该启动项已创建。

   **了解启动项促销范围**

   * **提升完整启动项**:启动项的所有渠道在设置的起始日期提升。
   * **提升修改的页面**:将仅提升修改后的启动项资源。 建议在不需要启动项审阅时使用此选项。
   * **提升已批准的页面**:此选项要求启动项批准工作流在启动项渠道上运行。 只有经过批准的页面才会在设置的起始日期提升。

      >[!CAUTION]
      >
      >启动起始日期遵循播放器／设备的时区，而不是服务器的时区。

1. 您将看到已创建启动项。 您可以单击“打 **开** ”以视图编辑器中的页面，或单击“ **完成** ”以导航回项目。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   单击 **完成** ，可导航回您的 **FutureLaunch** 渠道。

   ![图像](/help/user-guide/assets/launches-images/launches-16.png)


### 编辑启动项属性以设置实时日期和范围 {#editing-the-launch-properties-to-set-the-live-date-and-scope}

在创建启动项后，您可以使用启动项属性来更新属性，如起始日期、启动项标题和促 **销范围**。

* **启动日期**，指实时日期，即根据播放器的时区，内容在Screens播放器中播放的日期或时间。
* **Production Ready**，允许渠道在升级这些现成功能后发布，因此无需更改。
* **范围**，决定在启动项促销期间将提升哪些渠道。


请按照以下步骤编辑启动项属性：

1. 导航到渠道 **FutureLaunch**( *即待定启动项)* ，然后选择渠道，如下图所示。

   ![图像](/help/user-guide/assets/launches-images/launches-17.png)

1. 单击操 **作栏中的** “仪表板” **，您会在渠道仪表板中看到“** 待定启动项”面板。

   ![图像](/help/user-guide/assets/launches-images/launches-18.png)

1. 选择启动项，然后从“待定 **的启动项** ”面板中 **单击启动项属性** 。

   ![图像](/help/user-guide/assets/launches-images/launches-19.png)

#### 编辑屏幕启动项以添加或删除渠道 {#editing-the-screens-launch-to-add-or-remove-channels}

在创建启动项后，您可以使用编辑启动项操作向现有启动项添加或删除 **渠道** 。

完成操作后，单击保 **存** ，导航回 **FutureLaunch** 渠道。

#### 手动提升屏幕启动{#promote-the-screens-launch-manually}

您可以使用“待定启动项”面板中的“ **提升启动项** ”选项 **手动提升启动项** 。

您可以在启动提升向导中选择要提升的资源，作为此手动提升的一 **部分**。

![图像](/help/user-guide/assets/launches-images/launches-e.png)

1. 您可以启用或禁用在生产后删除启动项的选项。
1. 您可以设置启 **动项的** “范围”，具有以下选项：
   1. **提升完整启动项**:启动项的所有渠道在设置的起始日期提升。
   1. **提升修改的页面**:将仅提升修改后的启动项资源。 建议在不需要启动项审阅时使用此选项。
   1. **提升已批准的页面**:此选项要求启动项批准工作流在启动项渠道上运行。 只有经过批准的页面才会在设置的起始日期提升。
   1. **提升当前页面**:此选项要求启动项批准工作流仅针对当前页面运行。
1. 单击 **提升** 启动 **向导中的下一步** 。
1. 单击 **提升** ，以提升启动项。


#### 删除屏幕启动项 {#deleting-the-screens-launch}

您可以使用删除启动项操作 **来删除启动** 项。

>[注意]
>此操作还将删除所有子代嵌套启动项。

