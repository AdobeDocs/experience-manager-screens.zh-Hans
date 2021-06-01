---
title: 使用Screens Launch更新内容
seo-title: 使用Screens Launch更新内容
description: 内容作者可以创建渠道的未来版本（称为Launch），并进一步设置此启动的起始日期，以便内容在设备或播放器中处于实时状态。
seo-description: 内容作者可以创建渠道的未来版本（称为Launch），并进一步设置此启动的起始日期，以便内容在设备或播放器中处于实时状态。
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
feature: 创作屏幕、启动项
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1619'
ht-degree: 0%

---


# 使用Screens Launch更新内容 {#launches}

内容作者可以创建渠道的未来版本（称为&#x200B;**Screens Launch**），并进一步设置此启动的起始日期。 这允许内容在指定的实时日期在设备或播放器中实时显示。

借助&#x200B;***Screens Launch***&#x200B;的帮助，作者可以预览启动项中的每个渠道，并应该能够启动审核请求。 批准者组将收到通知并可批准或拒绝请求。 达到实时日期后，内容将在设备中播放。

例如，如果作者希望创建c1、c2（渠道）的未来版本，则会创建启动项并设置起始日期（例如，上午11月10日8:00）。 内容中的任何进一步更新都将发出以供审阅。

获得批准并处于实时日期（11月10日上午8:00）后，此启动会在设备或播放器上播放内容。

## 要求 {#requirements}

在AEM Screens项目中开始使用&#x200B;*Screens Launch*&#x200B;之前，请确保您了解宽限期的概念及其相关性。

在播放器的设置起始日期运行体验涉及：

* 启动项的提升（通常需要几秒钟）

* 发布资源以发布实例（通常需要几分钟，具体取决于需要发布的渠道或资产的大小）

* 完成更新离线内容所花费的时间（通常需要几分钟）

* 播放器从发布实例下载内容所花费的时间（通常需要几分钟，具体取决于需要下载的资产的带宽和大小）

* 服务器和播放器的任何时间差异

### 了解宽限期{#understanding-grace-period}

为了让播放器能够在设置的起始日期开始播放内容，我们需要在起始日期之前开始之前的活动。

如果实时日期为&#x200B;*11月24日，上午9:00*，宽限期为&#x200B;*24小时*，则上述操作顺序将从（实时日期 — 宽限期）（即上午11月23日9:00服务器时间）开始。 这将为完成上述所有操作提供24小时的时间，内容将会到达播放器。 播放器将了解这是一个启动内容，因此内容不会立即播放，但播放器会将此内容存储为未来版本，并且将完全在播放器时区的设置起始日期开始播放。

例如，假设服务器为PST，设备为EST，在这种情况下，最大时间差为3小时，并且假定促销活动将花费1分钟，而从作者发布到发布将花费10分钟，播放器通常可以在10-15分钟内下载资源。 然后，宽限期=时间差（3小时）+提升启动的时间（1分钟）+发布启动的时间（10分钟）+在播放器下载时间（10-15分钟）+缓冲区（安全，例如30分钟）= 3小时56分钟= 14160秒。

因此，无论我们何时计划任何启动活动的实时时间，促销活动都将在此偏移量之前提前开始。 在上述等式中，大多数项目都不需要太多时间，只要我们知道服务器与任何播放器之间的最大时间差，就可以对此偏移量使用适当的猜测。

>[!NOTE]
>
>现成的Screens Launch的宽限期设置为24小时，这意味着当我们在&#x200B;*/content/screens*&#x200B;下为任何资源启动设置起始日期时，促销活动将以此偏移开始。

### 更新现成的宽限期{#updating-out-of-the-box-grace-period}

本节将介绍如何将现成的宽限期更新为10分钟。

1. 导航到CRXDE Lite，然后导航到`/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`。
2. 右键单击并复制文件。
3. 导航到`/apps/system/config`并右键单击并粘贴。
4. 双击`/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`以在编辑器中以CRXDE Lite打开文件。 它必须将路径&#x200B;*/content/screens/*&#x200B;的宽限期显示为&#x200B;**86400**。 将该值更改为&#x200B;**600**。

现在，文本文件中的内容应类似于：

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

由于您在上例中将宽限期设置为10分钟，因此当您为&#x200B;*/content/screens*&#x200B;下的资源的任何启动设置起始日期时，促销活动将以此偏移开始。

例如，如果实时日期设置为11月24日、上午9:00和宽限期为600秒，则促销作业将于11月24日上午8:50开始。

## 使用Screens Launch {#using-launches}

此部分将演示如何在您的AEM Screens项目中实施Screens Launch。

### 创建屏幕启动项{#creating-a-launch}

请按照以下步骤将Screens Launch功能实施到您的AEM Screens项目：

1. 在AEM Screens项目中创建序列渠道，例如&#x200B;**LaunchesDemo** —> **渠道** —> **FutureLaunch**，如下所示。

   >[!CAUTION]
   >
   >您必须从AEM Screens项目中预先存在的渠道创建启动项。

   ![图像](/help/user-guide/assets/launches-images/launches-11.png)

1. 选择渠道&#x200B;**FutureLaunch**，然后单击操作栏中的&#x200B;**创建Launch**。

   ![图像](/help/user-guide/assets/launches-images/launches-12.png)

1. 此时会打开&#x200B;**创建Launch**&#x200B;向导。 您可以选择向导中已显示的渠道，或单击&#x200B;**+添加渠道**&#x200B;以添加要为其创建启动项的渠道。

1. 单击&#x200B;**创建Launch**&#x200B;向导中的&#x200B;**Next**。 默认情况下，会选中&#x200B;**Include subpages**&#x200B;选项。

   ![图像](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >您可以使用&#x200B;**+添加渠道**&#x200B;选项添加要为其创建启动项的其他渠道。

   要使用&#x200B;**添加渠道**&#x200B;选项，请导航到要为其创建启动项的渠道，然后单击&#x200B;**选择**。

   如果您尝试选择多个渠道或文件夹来添加启动项，则&#x200B;**选择**&#x200B;选项将被禁用。

   ![图像](/help/user-guide/assets/launches-images/launches-14.png)

   选择渠道/渠道后，单击&#x200B;**下一步**。


1. 将&#x200B;**启动标题**&#x200B;输入为&#x200B;**SummerPromotions**，您无需设置&#x200B;**启动日期**，如下图所示。 单击&#x200B;**创建**。

   >[!NOTE]
   >
   >*启用或选* 中“继承源 **页面实时** 数据”选项，即可在启动项中将渠道创建为Live Copy。如果在原始渠道中进行了任何更改，则这些更改会自动应用于启动渠道。
   >
   >
   >*禁用或取* **消选中“继承源页** 面实时数据”后，可以复制渠道，而无需在启动项中建立任何实时关系。因此，如果对原始渠道进行了任何更改，则这些更改不会应用到启动渠道。

   ![图像](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >您可以在此步骤中设置启动项的实时日期，也可以在启动项创建后编辑其属性时稍后进行设置。

   **了解Launch促销范围**

   * **提升完整启动项**:启动项的所有渠道都会在设置的起始日期进行提升。
   * **提升修改的页面**:将只提升已修改的启动资源。当不需要启动项审阅时，建议使用此选项。
   * **提升已批准的页面**:此选项要求在启动渠道上运行启动项批准工作流。只有在设置的起始日期才会提升已批准的页面。

      >[!CAUTION]
      >
      >启动启动日期遵循播放器/设备的时区，而不是服务器的时区。

1. 您将看到启动项已创建。 您可以单击&#x200B;**Open**&#x200B;在编辑器中查看页面，或单击&#x200B;**Done**&#x200B;导航回项目。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   单击&#x200B;**Done**&#x200B;可导航回&#x200B;**FutureLaunch**&#x200B;渠道。

   ![图像](/help/user-guide/assets/launches-images/launches-16.png)


### 编辑Launch属性以设置启动日期和范围{#editing-the-launch-properties-to-set-the-live-date-and-scope}

创建启动项后，您可以使用&#x200B;**启动属性**&#x200B;来更新属性，例如启动日期、启动项标题和促销活动范围。

* **启动日期**，指实时日期，即根据播放器的时区，内容在Screens播放器中播放的日期或时间。
* **生产就绪**，允许渠道在提升后发布，且启用了此功能，因此无需更改。
* **范围**，可决定在启动促销期间要促销的渠道。


请按照以下步骤编辑启动项属性：

1. 导航到渠道&#x200B;**FutureLaunch**、*（即待定的启动）*&#x200B;并选择渠道，如下图所示。

   ![图像](/help/user-guide/assets/launches-images/launches-17.png)

1. 单击操作栏中的&#x200B;**功能板**，您会看到渠道功能板中的&#x200B;**待定启动项**&#x200B;面板。

   ![图像](/help/user-guide/assets/launches-images/launches-18.png)

1. 选择启动项，然后单击&#x200B;**待定启动项**&#x200B;面板中的&#x200B;**启动属性** 。

   ![图像](/help/user-guide/assets/launches-images/launches-19.png)

### 编辑Screens Launch以添加或删除渠道{#editing-the-screens-launch-to-add-or-remove-channels}

创建启动项后，可以使用&#x200B;**编辑启动项**&#x200B;选项向现有启动项添加或删除渠道。

完成后，单击&#x200B;**Save**&#x200B;以导航回&#x200B;**FutureLaunch**&#x200B;渠道。

### 手动提升屏幕启动{#promote-the-screens-launch-manually}

您可以使用&#x200B;**待定启动项**&#x200B;面板中的&#x200B;**提升启动项**&#x200B;选项来手动提升启动项。

在&#x200B;**启动升级向导**&#x200B;中，可以选择要作为此手动升级的一部分进行升级的资源。

![图像](/help/user-guide/assets/launches-images/launches-e.png)

1. 您可以启用或禁用在生产后删除启动项的选项。
1. 您可以设置启动项的&#x200B;**范围**，其中包含以下选项：
   1. **提升完整启动项**:启动项的所有渠道都会在设置的起始日期进行提升。
   1. **提升修改的页面**:将只提升已修改的启动资源。当不需要启动项审阅时，建议使用此选项。
   1. **提升已批准的页面**:此选项要求在启动渠道上运行启动项批准工作流。只有在设置的起始日期才会提升已批准的页面。
   1. **提升当前页面**:此选项要求启动项批准工作流仅为当前页面运行。
1. 在&#x200B;**提升启动项**&#x200B;向导中，单击&#x200B;**下一步**。
1. 单击&#x200B;**Promote**&#x200B;以提升启动项。

### 删除屏幕启动项{#deleting-the-screens-launch}

您可以使用&#x200B;**从**&#x200B;待定启动项&#x200B;**面板中的删除启动项**&#x200B;选项来删除启动项。

>[!CAUTION]
>
>此操作还将删除所有子项（嵌套启动项）。

