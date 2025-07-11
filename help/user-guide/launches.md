---
title: 使用Screens Launch进行内容更新
description: 了解如何创建渠道的未来版本（称为Launch），并设置启动项的上线日期以使内容在设备或播放器上线。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Launches
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1568'
ht-degree: 0%

---

# 使用Screens Launch进行内容更新 {#launches}

内容作者可以创建渠道的未来版本，并进一步设置此启动项的启用日期。 此功能允许内容在指定的上线日期在设备或播放器中上线。

在&#x200B;***Screens Launch***&#x200B;的帮助下，作者可以预览启动项中的每个渠道，并且应该能够发起审查请求。 审批者组收到通知，可以批准或拒绝请求。 当到达实时日期时，内容将在设备中播放。

例如，如果作者想要创建c1、c2（渠道）的未来版本，则会创建启动项并设置启用日期（例如，11月10日上午8:00）。 内容中的任何其他更新都会发送以供审查。

在获得批准并上线日期（11月10日上午8:00）后，本次发布将在设备或播放器上播放内容。

## 要求 {#requirements}

在AEM Screens项目中开始使用&#x200B;*Screens Launch*&#x200B;之前，请确保了解宽限期的概念及其相关性。

在设置的播放器上运行体验的过程包括：

* 提升启动项（通常需要几秒钟）。

* 将资源发布到发布实例（通常需要几分钟，具体取决于必须发布的渠道或资源的大小）。

* 完成更新离线内容所花费的时间（通常需要几分钟）。

* 播放器从发布实例下载内容所用的时间（通常需要几分钟时间，具体取决于必须下载的资源的带宽和大小）。

* 服务器和播放器的任何时间差异。

### 了解宽限期 {#understanding-grace-period}

为了让播放器能够在设置的实时日期开始播放内容，请在实时日期之前开始之前的活动。

如果起始日期是&#x200B;*11月24日，上午9:00*&#x200B;并且&#x200B;*24小时*&#x200B;是宽限期，则上述操作序列将从（起始日期 — 宽限期）开始，即11月23日服务器时间上午9:00。 此设置有24小时来完成上述所有操作，以便内容可到达播放器。 播放器知道此时间段属于启动内容。 因此，内容不会立即播放，但播放器可以将此内容存储为未来版本，并让它在播放器时区的设置实时日期开始播放。

例如，服务器在PST中，设备在EST中。 最长时间差为3小时。 它假定促销活动需要1分钟，从创作到发布需要10分钟，播放器通常可在10-15分钟内下载资源。 然后宽限期=时间差（三个小时）：

* 加上提升启动项所需的时间（1分钟）
* 加上发布启动项的时间（10分钟）
* 此外，还可在播放器上下载时间（10-15分钟）
* 外加缓冲（30分钟）

因此，3小时56分钟(14160秒)。

因此，无论何时安排任何启动直播，促销活动都会提前开始，并会将此偏移量考虑在内。 以上方程式中，多数项用时不大。 当您知道服务器和任何播放器之间的最大时间差时，可以像往常一样猜测此偏移。

>[!NOTE]
>
>现成的Screens Launch的宽限期设置为24小时。 这意味着当您为&#x200B;*/content/screens*&#x200B;下的资源设置任何启动项的启动日期时，促销活动将从此偏移开始。

### 更新现成的宽限期 {#updating-out-of-the-box-grace-period}

本节介绍如何将现成的宽限期更新为10分钟。

1. 导航到CRXDE Lite，然后导航到`/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`。
1. 右键单击并复制文件。
1. 导航到`/apps/system/config`，右键单击并粘贴。
1. 双击`/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`，以便在CRXDE Lite的编辑器中打开该文件。 它必须将路径&#x200B;*/content/screens/*&#x200B;的宽限期显示为&#x200B;**86400**。 将该值更改为&#x200B;**600**。

现在，文本文件中的内容应该类似于：

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

在上例中，您将宽限期设置为10分钟。 因此，当您为&#x200B;*/content/screens*&#x200B;下的资源设置任何启动项的生效日期时，促销活动将从此偏移开始。

例如，如果将起始日期设置为11月24日上午9:00，宽限期为600秒，则提升作业将从11月24日上午8:50开始。

## 使用Screens Launch {#using-launches}

此部分演示如何在AEM Screens项目中实施Screens Launch。

### 创建Screens启动项 {#creating-a-launch}

请按照以下步骤将Screens Launch功能实施到AEM Screens项目：

1. 在您的AEM Screens项目中创建序列渠道，例如&#x200B;**LaunchesDemo** > **渠道** > **FutureLaunch**，如下所示。

   >[!CAUTION]
   >
   >从AEM Screens项目中的现有渠道创建启动项。

   ![图像](/help/user-guide/assets/launches-images/launches-11.png)

1. 单击频道&#x200B;**FutureLaunch**，然后单击操作栏中的&#x200B;**创建启动项**。

   ![图像](/help/user-guide/assets/launches-images/launches-12.png)

1. 将打开&#x200B;**创建启动项**&#x200B;向导。 您可以单击已在向导中可见的频道，也可以单击&#x200B;**+添加频道**&#x200B;以添加要为其创建启动项的频道。

1. 从&#x200B;**创建启动项**&#x200B;向导中单击&#x200B;**下一步**。 默认情况下选中&#x200B;**包含子页面**&#x200B;选项。

   ![图像](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >您可以使用&#x200B;**+添加渠道**&#x200B;选项添加要为其创建启动项的另一个渠道。

   要使用&#x200B;**添加渠道**&#x200B;选项，请导航到要为其创建启动项的渠道，然后单击&#x200B;**选择**。

   如果尝试单击多个渠道或文件夹以添加启动项，则将禁用&#x200B;**选择**&#x200B;选项。

   ![图像](/help/user-guide/assets/launches-images/launches-14.png)

   单击渠道/渠道后，单击&#x200B;**下一步**。


1. 输入&#x200B;**启动项标题**&#x200B;作为&#x200B;**SummerPromotions**，您无需设置&#x200B;**启动项日期**，如下图所示。 单击&#x200B;**创建**。

   >[!NOTE]
   >
   >*正在启用或检查*&#x200B;选项&#x200B;**继承源页面活动数据**&#x200B;允许将渠道创建为启动项中的活动副本。 如果在原始渠道中进行任何更改，这些更改将自动应用于启动渠道。
   >
   >
   >*禁用或取消选中* **继承源页面活动数据**&#x200B;允许复制渠道，而不必在启动项中建立任何实时关系。 因此，如果对原始渠道进行了任何更改，则这些更改不会应用于启动渠道。

   ![图像](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >您可以在此步骤中设置启动项的实时日期，也可以在以后创建启动项之后编辑启动项的属性时设置该日期。

   **了解启动项提升范围**

   * **提升整个启动项** — 启动项的所有渠道在设置的活动日期提升。
   * **提升已修改的页面** — 仅提升已修改的启动资源。 在不需要启动项审阅时使用此选项。
   * **提升批准的页面** — 此选项要求在启动项渠道上运行启动项批准工作流。 只有经过批准的页面才会在设置的活动日期提升。

     >[!CAUTION]
     >
     >启动起始日期遵循播放器/设备的时区，而不是服务器。

1. 请注意，您的启动项已创建。 您可以单击&#x200B;**打开**&#x200B;查看编辑器中的页面，或单击&#x200B;**完成**&#x200B;导航回您的项目。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   选择&#x200B;**完成**&#x200B;可让您导航回&#x200B;**FutureLaunch**&#x200B;频道。

   ![图像](/help/user-guide/assets/launches-images/launches-16.png)


### 编辑启动项属性以设置上线日期和范围 {#editing-the-launch-properties-to-set-the-live-date-and-scope}

创建启动项后，您可以使用&#x200B;**启动项属性**&#x200B;更新活动日期、启动项标题和提升范围等属性。

* **启动日期** — 上线日期，即根据播放器的时区，内容在Screens播放器中播放的日期或时间。
* **生产就绪** — 提升后，它将允许发布渠道并启用现成功能，因此无需进行更改。
* **范围** — 决定在启动项提升期间提升哪些渠道。

请按照以下步骤编辑启动项属性：

1. 导航到频道&#x200B;**FutureLaunch** *（待处理启动项）*，然后单击该频道，如下图所示。

   ![图像](/help/user-guide/assets/launches-images/launches-17.png)

1. 单击操作栏中的&#x200B;**仪表板**，您会看到渠道仪表板中的&#x200B;**待处理启动项**&#x200B;面板。

   ![图像](/help/user-guide/assets/launches-images/launches-18.png)

1. 单击启动项，然后单击&#x200B;**待处理启动项**&#x200B;面板中的&#x200B;**启动项属性**。

   ![图像](/help/user-guide/assets/launches-images/launches-19.png)

### 编辑Screens Launch以添加或删除渠道 {#editing-the-screens-launch-to-add-or-remove-channels}

创建启动项后，可以使用&#x200B;**编辑启动项**&#x200B;选项向现有启动项添加或删除渠道。

完成后，单击&#x200B;**保存**&#x200B;以导航回&#x200B;**FutureLaunch**&#x200B;渠道。

### 手动提升Screens启动项{#promote-the-screens-launch-manually}

您可以使用&#x200B;**待处理启动项**&#x200B;面板中的&#x200B;**`Promote Launch`**&#x200B;选项手动提升启动项。

您可以在&#x200B;**启动项提升向导**&#x200B;中选择要作为此手动提升的一部分提升的资源。

![图像](/help/user-guide/assets/launches-images/launches-e.png)

1. 您可以启用或禁用在生产之后删除启动项的选项。
1. 您可以使用以下选项设置启动项的&#x200B;**范围**：
   * **提升整个启动项** — 启动项的所有渠道在设置的活动日期提升。
   * **提升已修改的页面** — 仅提升已修改的启动资源。 在不需要启动项审阅时使用此选项。
   * **提升批准的页面** — 此选项要求在启动项渠道上运行启动项批准工作流。 只有经过批准的页面才会在设置的活动日期提升。
   * **提升当前页面** — 此选项要求启动项批准工作流仅针对当前页面运行。
1. 在&#x200B;**提升启动项**&#x200B;向导中单击&#x200B;**下一步**。
1. 单击&#x200B;**提升**&#x200B;以提升启动项。

### 删除Screens Launch

您可以使用&#x200B;**待处理启动项**&#x200B;面板中的&#x200B;**删除启动项**&#x200B;选项删除启动项。

>[!CAUTION]
>
>此操作还将删除所有子项（嵌套启动项）。
