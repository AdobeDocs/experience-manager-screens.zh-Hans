---
title: 在AEM Screens中使用自适应演绎版
description: 本页介绍如何在AEM Screens中使用自适应演绎版。
source-git-commit: 6d9dab9fd59289aafdb688682fea47589d3ec873
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# 在AEM Screens中使用自适应演绎版 {#adaptive-renditions}

## 简介 {#introduction}

自适应演绎版允许设备根据客户定义的规则自动为设备选择最佳演绎版。 这些设备将根据这些规则自动下载并播放资产的最合适演绎版，这样客户就只能专注于设计&#x200B;*主*&#x200B;体验。

## 目标 {#objective}

作为AEM Screens内容作者，您现在可以将特定于设备的资产演绎版配置为自动下载和播放，而无需手动创建所有内容变体。
开发人员添加演绎版映射属性和规则后，您现在可以将演绎版映射应用到资产，并随后将其包含在AEM Screens渠道中。

>[!IMPORTANT]
>在开始使用自适应演绎版之前，建议您在AEM Screens渠道中了解此功能的架构概述和配置。 请参阅[自适应演绎版：架构概述和配置](/help/user-guide/adaptive-renditions.md)以了解更多详细信息。

## 在渠道中使用自适应演绎版 {#using-adaptive-renditions}

>[!NOTE]
>将[演绎版映射属性添加到Screens项目](/help/user-guide/adaptive-renditions.md#rendition-mapping-new)和[演绎版映射规则](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)后，作为内容作者，您现在可以将这些演绎版应用到资产。

### 将演绎版应用于资产 {#apply-renditions-assets}

请按照以下步骤将演绎版应用到您要在导览屏幕渠道中使用的资产：

1. 导航到AEM实例中的&#x200B;**Assets**&#x200B;文件夹。

1. 创建更适合标牌显示的资产版本，例如`seahorse.jpg`。

1. 选择演绎版命名模式，例如`landscape`，与&#x200B;**CRXDE Lite**&#x200B;中&#x200B;**pattern**&#x200B;属性中定义的模式类似。 有关更多详细信息，请参阅[添加演绎版映射规则](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)。

1. 单击&#x200B;**添加演绎版**&#x200B;以上传演绎版，如下图所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. 选择重命名的资产文件。 要添加的演绎版必须包含模式（在步骤3中定义），例如`seahorse-landscape.png`。

1. 添加资产后，选择资产，然后单击操作栏中的&#x200B;**管理发布**&#x200B;以发布资产。

   ![图像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >请参阅[按需内容更新](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content.html?lang=en) ，了解有关管理发布和将内容更新从创作传送到设备的更多信息。


## 迁移策略 {#migration-strategy}

>[!IMPORTANT]
>对于大型网络，建议逐步迁移以降低风险，因为该功能将对清单和文件存储格式进行更改。 将`sling:configRef`添加到整个项目涉及将所有播放器更新到功能包6.5.9。如果您更新了某些播放器，则需要仅将`sling:configRef`添加到所有播放器都更新到功能包6.5.9的显示、位置或渠道文件夹。

下图描述了大型网络的迁移策略：

![图像](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

要启用该功能，请至少添加一个映射规则，并确保在显示和渠道的上下文中可解析演绎版映射配置。 按照以下步骤进行迁移：

1. 添加[演绎版映射规则](/help/user-guide/adaptive-renditions.md)。
1. 为新渠道创建文件夹，并添加指向演绎版映射配置的引用。
1. 创建替换旧渠道的新渠道并上传演绎版。
1. 将显示的内容重新分配给新渠道。
1. 添加对指向演绎版映射配置的已迁移显示屏或位置的引用。
1. 对所有剩余的渠道和显示屏重复步骤3、4和5。

   >[!NOTE]
   >完成迁移后，请确保从渠道、显示屏和位置中删除所有配置引用，并向项目内容节点添加一个配置引用。

