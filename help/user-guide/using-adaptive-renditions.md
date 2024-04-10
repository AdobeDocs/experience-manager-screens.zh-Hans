---
title: 在AEM Screens中使用自适应演绎版
description: 本页介绍如何在AEM Screens中使用自适应演绎版。
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# 在AEM Screens中使用自适应演绎版 {#adaptive-renditions}

## 简介 {#introduction}

自适应演绎版允许设备根据客户定义的规则自动为设备选择最佳演绎版。 这些设备将根据这些规则自动下载并播放最合适的资源演绎版，从而让客户仅专注于设计 *主要* 体验。

## 目标 {#objective}

作为AEM Screens内容作者，您现在可以将特定于设备的资源呈现配置为自动下载和播放，而无需手动创建所有内容变体。
在开发人员添加演绎版映射属性和规则后，您现在可以将演绎版映射应用于资源，并随后将资源包含到AEM Screens渠道中。

>[!IMPORTANT]
>在开始使用自适应呈现版本之前，建议在AEM Screens渠道中了解这项功能的架构概述和配置。 请参阅 [自适应演绎版：架构概述和配置](/help/user-guide/adaptive-renditions.md) 以了解更多详细信息。

## 在渠道中使用自适应演绎版 {#using-adaptive-renditions}

>[!NOTE]
>添加后 [将格式副本映射属性到屏幕项目](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) 和 [节目映射规则](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)，作为内容作者，您现在可以将演绎版应用于资源。

### 将演绎版应用到资源 {#apply-renditions-assets}

请按照以下步骤将演绎版应用到要在导览Screens渠道中使用的资源：

1. 导航至 **资产** AEM文件夹。

1. 创建更适合标牌显示的资源版本，例如， `seahorse.jpg`.

1. 选择演绎版命名模式，例如`landscape`，与中定义的内容类似 **模式** 中的属性 **CRXDE Lite**. 请参阅 [添加节目映射规则](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) 以了解更多详细信息。

1. 单击 **添加节目** 上传节目，如下图所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. 选择重命名后的资源文件。 要添加的演绎版必须包含模式（在步骤3中定义），例如， `seahorse-landscape.png`.

1. 添加资产后，选择资产并单击 **管理发布** 以发布资产。

   ![图像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >请参阅 [按需内容更新](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content.html?lang=en) 了解有关管理发布以及将内容更新从作者交付到发布到设备的更多信息。


## 迁移策略 {#migration-strategy}

>[!IMPORTANT]
>对于大型网络，建议逐步完成迁移以减轻风险，因为该功能将会引入清单和文件存储格式的更改。 添加 `sling:configRef` 整个项目涉及将所有播放器更新到Feature Pack 6.5.9。如果您更新了一些播放器，则需要添加 `sling:configRef` 仅限所有播放器都已更新为功能包6.5.9的显示、位置或渠道文件夹。

下图描述了大型网络的迁移策略：

![图像](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

要启用该功能，请至少添加一个映射规则，并确保演绎版映射配置在显示和渠道的上下文中可解析。 请按照以下步骤进行迁移：

1. 添加 [节目映射规则](/help/user-guide/adaptive-renditions.md).
1. 为新渠道创建文件夹，并添加指向演绎版映射配置的引用。
1. 创建新渠道以替换旧渠道并上传演绎版。
1. 将显示重新分配给新渠道。
1. 添加对迁移的显示或指向演绎版映射配置的位置的引用。
1. 对所有剩余的渠道和显示器重复步骤3、4和5。

   >[!NOTE]
   >完成迁移后，请确保从渠道、显示区和位置中删除所有配置引用，并将一个配置引用添加到项目内容节点。
