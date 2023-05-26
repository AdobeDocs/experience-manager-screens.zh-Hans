---
title: 使用屏幕启动项更新内容
seo-title: Content Update using Screens Launch
description: 内容作者可以创建渠道的未来版本（称为Launch），并进一步为此启动设置上线日期，以使内容在设备或播放器中上线。
seo-description: Content authors can create future version of the channel(s), known as Launch and further setting live date for this launch allows content to be live in devices or players.
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
feature: Authoring Screens, Launches
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: 2cc613454d0d20a42871858e3d754e1b0e161dc3
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 0%

---

# 使用屏幕启动项更新内容 {#launches}

内容作者可以创建渠道的未来版本，称为 **屏幕启动** 并进一步设置此启动项的启用日期。 这允许内容在指定的上线日期在设备或播放器中上线。

在的帮助下 ***屏幕启动***，作者可以预览启动项中的每个渠道，并且应该能够发起审阅请求。 审批者组将收到通知，可以批准或拒绝请求。 当到达上线日期时，内容将在设备中播放。

例如，如果作者想要创建未来版本的c1、c2（渠道），则会创建启动项并设置上线日期（例如，11月10日上午8:00）。 内容中的任何进一步更新都会发送以供审阅。

一旦获得批准并在上线日期（11月10日上午8:00）上线，此发布将在设备或播放器上播放内容。

## 要求 {#requirements}

开始利用之前 *屏幕启动* 在AEM Screens项目中，确保您了解宽限期的概念及其相关性。

在设置的播放器上运行体验的过程包括：

* 启动项的提升（通常需要几秒钟）

* 将资源发布到发布实例（通常需要几分钟，具体取决于需要发布的渠道或资产的大小）

* 更新离线内容完成所用的时间（通常需要几分钟）

* 播放器从发布实例下载内容所用的时间（通常需要几分钟时间，具体取决于需要下载的资源的带宽和大小）

* 服务器和播放器的任何时间差异

### 了解宽限期 {#understanding-grace-period}

为了使播放器能够在设置的上线日期开始播放内容，我们需要在上线日期之前开始之前的活动。

如果上线日期为 *11月24日，上午9:00* 宽限期为 *24小时*，则上述操作序列将从（起始日期 — 宽限期）开始，即11月23日服务器时间上午9:00。 这将给予24小时时间来完成上述所有操作，并且内容将到达播放器。 播放器将了解这是一项启动内容，因此不会立即播放该内容，但播放器会将此内容存储为未来版本，并将在播放器时区的设置上线日期完全开始播放。

例如，假设服务器处于PST状态，设备处于EST状态，在这种情况下，最大时间差为3小时，并假设提升将需要1分钟，从作者发布到发布需要10分钟，播放器通常可在10-15分钟后下载资源。 然后宽限期=时间差（3小时）+提升启动项的时间（1分钟）+发布启动项的时间（10分钟）+播放器下载的时间（10-15分钟）+缓冲时间（安全起见，比如30分钟）= 3小时56分钟= 14160秒。

因此，无论我们何时安排了任何启动项的上线，促销活动都将在此时间之前提早开始。 在上面的方程式中，大多数项目不会花费太多时间，一旦我们知道服务器和任何播放器之间的最大时间差，我们就可以很好地猜测此偏移。

>[!NOTE]
>
>开箱即用，Screens Launch的宽限期设置为24小时，这意味着当我们为下的资源设置任何启动项的有效日期时 */content/screens*，促销活动将从此偏移开始。

### 更新现成的宽限期 {#updating-out-of-the-box-grace-period}

本节介绍如何将现成的宽限期更新为10分钟。

1. 导航到CRXDE Lite，然后导航到 `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. 右键单击并复制文件。
3. 导航到 `/apps/system/config` 和右键单击并粘贴。
4. 双击 `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` 以在CRXDE Lite的编辑器中打开文件。 它必须显示路径的宽限期 */content/screens/* 作为 **86400**. 将该值更改为 **600**.

现在，文本文件中的内容应当类似于以下内容：

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

由于您已将上例中的宽限期设置为10分钟，因此当您为下的资源设置任何启动项的有效日期时， */content/screens*，促销活动将从此偏移开始。

例如，如果将启用日期设置为11月24日上午9:00，宽限期为600秒，则提升作业将从11月24日上午8:50开始。

## 使用Screens启动项 {#using-launches}

此部分演示如何在AEM Screens项目中实施Screens Launch。

### 创建屏幕启动项 {#creating-a-launch}

请按照以下步骤将Screens Launch功能实施到AEM Screens项目：

1. 例如，在AEM Screens项目中创建序列渠道 **LaunchDemo** —> **渠道** —> **Futurelaunch**，如下所示。

   >[!CAUTION]
   >
   >您必须从AEM Screens项目中预先存在的渠道创建启动项。

   ![图像](/help/user-guide/assets/launches-images/launches-11.png)

1. 选择渠道 **Futurelaunch** 并单击 **创建启动项** 操作栏中的。

   ![图像](/help/user-guide/assets/launches-images/launches-12.png)

1. 此 **创建启动项** 向导打开。 您可以选择已在向导中可见的渠道或单击 **+添加渠道** 以添加要为其创建启动项的渠道。

1. 单击 **下一个** 从 **创建启动项** 向导。 此 **包括子页面** 选项默认处于选中状态。

   ![图像](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >您可以使用 **+添加渠道** 选项来添加另一个要为其创建启动项的渠道。

   使用 **添加渠道** 选项，导航到要为其创建启动项的渠道并单击 **选择**.

   此 **选择** 如果尝试选择多个渠道或一个文件夹来添加启动项，则将禁用该选项。

   ![图像](/help/user-guide/assets/launches-images/launches-14.png)

   选择渠道/渠道后，单击 **下一个**.


1. 输入 **启动项标题** 作为 **SummerPromotions** 而且您无需设置 **启动日期**，如下图所示。 单击&#x200B;**创建**。

   >[!NOTE]
   >
   >*启用或检查* 选项 **继承源页面活动数据** 允许将渠道创建为启动项中的活动副本。 如果在原始渠道中进行任何更改，这些更改将自动应用于启动渠道。
   >
   >
   >*禁用或取消选中* **继承源页面活动数据** 允许复制渠道，而无需在启动项中设置任何实时关系。 因此，如果对原始渠道进行了任何更改，则这些更改不会应用于Launch渠道。

   ![图像](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >您可以在此步骤中设置启动项的实时日期，也可以在以后创建启动项属性时设置该日期。

   **了解启动项提升范围**

   * **提升整个启动项**：启动项的所有渠道将在设置的活动日期提升。
   * **提升已修改的页面**：仅提升已修改的启动项资源。 建议在不需要启动审查时使用此选项。
   * **提升批准的页面**：此选项要求对启动项渠道运行启动项批准工作流。 只有经过批准的页面才会在设置的上线日期提升。

      >[!CAUTION]
      >
      >启动起始日期遵循播放器/设备的时区，而不是服务器的时区。

1. 您将看到您的启动项已创建。 您可以单击 **打开** 在编辑器中查看页面或单击 **完成** 以导航回您的项目。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   点击 **完成** 允许您导航回 **Futurelaunch** 渠道。

   ![图像](/help/user-guide/assets/launches-images/launches-16.png)


### 编辑启动项属性以设置活动日期和范围 {#editing-the-launch-properties-to-set-the-live-date-and-scope}

创建启动项后，您可以使用更新属性，例如启用日期、启动项标题和促销活动范围 **启动项属性**.

* **启动日期**&#x200B;是指实时日期，即内容按照播放器的时区在Screens播放器中播放的日期或时间。
* **生产就绪**，允许在提升这些渠道后发布渠道，这将启用现成功能，因此无需进行更改。
* **范围**，可决定在启动项促销活动期间促销哪些渠道。


请按照以下步骤编辑启动项属性：

1. 导航到渠道 **Futurelaunch**， *（即待执行的启动）* 并选择频道，如下图所示。

   ![图像](/help/user-guide/assets/launches-images/launches-17.png)

1. 单击 **仪表板** 从操作栏中可以看到 **待处理启动项** 面板中。

   ![图像](/help/user-guide/assets/launches-images/launches-18.png)

1. 选择启动项并单击 **启动项属性** 从 **待处理启动项** 面板。

   ![图像](/help/user-guide/assets/launches-images/launches-19.png)

### 编辑屏幕启动项以添加或删除渠道  {#editing-the-screens-launch-to-add-or-remove-channels}

创建启动项后，可以使用向现有启动项添加或删除渠道 **编辑启动项** 选项。

完成后，单击 **保存** 以导航回 **Futurelaunch** 渠道。

### 手动提升屏幕启动项{#promote-the-screens-launch-manually}

您可以使用手动提升启动 **提升启动项** 选项来自 **待处理启动项** 面板。

在此手动促销活动中，您可以选择想要促销的资源 **启动项提升向导**.

![图像](/help/user-guide/assets/launches-images/launches-e.png)

1. 您可以启用或禁用在生产后删除启动项的选项。
1. 您可以设置 **范围** ，并提供以下选项：
   1. **提升整个启动项**：启动项的所有渠道将在设置的活动日期提升。
   1. **提升已修改的页面**：仅提升已修改的启动项资源。 建议在不需要启动审查时使用此选项。
   1. **提升批准的页面**：此选项要求对启动项渠道运行启动项批准工作流。 只有经过批准的页面才会在设置的上线日期提升。
   1. **提升当前页面**：此选项要求启动项批准工作流仅对当前页面运行。
1. 单击 **下一个** 在 **提升启动项** 向导。
1. 单击 **提升** 以提升启动项。

### 删除屏幕启动项 {#deleting-the-screens-launch}

您可以使用以下方式删除启动项 **删除启动项** 选项来自 **待处理启动项** 面板。

>[!CAUTION]
>
>此操作还将删除所有子项（嵌套启动项）。
