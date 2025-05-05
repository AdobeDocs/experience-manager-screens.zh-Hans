---
title: 在AEM Screens中使用自适应演绎版
description: 了解如何在AEM Screens中使用自适应演绎版。
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# 在AEM Screens中使用自适应演绎版 {#adaptive-renditions}

## 简介 {#introduction}

自适应演绎版允许设备根据客户定义的规则自动为设备单击最佳演绎版。 设备将根据这些规则自动下载并播放最合适的资源演绎版。 它使客户能够专注于设计&#x200B;*主要*&#x200B;体验。

## 目标 {#objective}

作为AEM Scrßens内容作者，您现在可以将特定于设备的资源呈现配置为自动下载和播放，而无需手动创建所有内容变体。
开发人员添加演绎版映射属性和规则后，您便可以将演绎版映射应用于资源，然后将其包含在AEM Screens渠道中。

>[!IMPORTANT]
>在开始在AEM Screens渠道中使用自适应演绎版之前，Adobe建议您了解此功能的架构概述和配置。 请参阅[自适应演绎版：架构概述和配置](/help/user-guide/adaptive-renditions.md)。

## 在渠道中使用自适应演绎版 {#using-adaptive-renditions}

>[!NOTE]
>在将[rendition-mapping属性添加到Screens项目](/help/user-guide/adaptive-renditions.md#rendition-mapping-new)和[rendition-mapping rules](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)后，作为内容作者，您现在可以将演绎版应用于资源。

### 将演绎版应用到Assets {#apply-renditions-assets}

要将演绎版应用到要在“导览Screens”渠道中使用的资源，请执行以下操作。

1. 导航到AEM实例中的&#x200B;**Assets**&#x200B;文件夹。
1. 创建更适合标牌显示的资源版本，例如`seahorse.jpg`。
1. 选择与&#x200B;**CRXDE Lite**&#x200B;中的&#x200B;**模式**&#x200B;属性中定义的格式副本命名模式，例如`landscape`。 有关更多详细信息，请参阅[添加节目映射规则](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)。
1. 单击&#x200B;**添加演绎版**&#x200B;以上传该演绎版，如下图所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. 单击重命名后的资源文件。 您要添加的演绎版必须包含模式（在步骤3中定义），例如`seahorse-landscape.png`。
1. 添加资产后，单击该资产，然后单击操作栏中的&#x200B;**管理发布**&#x200B;以发布资产。

   ![图像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >请参阅[按需内容更新](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content)，了解有关管理出版物以及将内容更新从作者交付到Publish到设备的更多信息。

## 迁移策略 {#migration-strategy}

>[!IMPORTANT]
>对于大型网络，Adobe建议逐步迁移以减轻风险。 原因在于，该功能可能会引入清单和文件存储格式的更改。 将`sling:configRef`添加到整个项目包括将所有播放器更新到Feature Pack 6.5.9。如果您更新了一些播放器，请仅将`sling:configRef`添加到所有播放器都已更新到Feature Pack 6.5.9的显示、位置或渠道文件夹中。

下图描述了大型网络的迁移策略：

![图像](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

要启用该功能，请至少添加一个映射规则，并确保呈现版本映射配置在显示和渠道的上下文中可解析。 请按照以下步骤进行迁移：

1. 添加[节目映射规则](/help/user-guide/adaptive-renditions.md)。
1. 为新渠道创建文件夹，并添加指向演绎版映射配置的引用。
1. 创建替换旧渠道的渠道并上传演绎版。
1. 将显示重新分配给新渠道。
1. 添加对迁移的显示或指向演绎版映射配置的位置的引用。
1. 对所有剩余的渠道和显示器重复步骤3、4和5。

   >[!NOTE]
   >完成迁移后，请确保从渠道、显示区和位置中删除所有配置引用，并将一个配置引用添加到项目内容节点。
