---
title: 在AEM Screens中使用自适应演绎版
description: 本页介绍如何在AEM Screens中使用自适应演绎版。
index: false
source-git-commit: d3a54ed85b9fa2ddf3918161566ba2c82c373be0
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 1%

---

# 在AEM Screens中使用自适应演绎版 {#adaptive-renditions}

## 简介 {#introduction}

自适应演绎版允许设备根据客户定义的规则自动为设备选择最佳演绎版。 这些设备将根据这些规则自动下载并播放资产的最合适演绎版，这样客户就只能专注于设计&#x200B;*主*&#x200B;体验。

## 目标 {#objective}

作为AEM Screens内容作者，您现在可以将特定于设备的资产演绎版配置为自动下载和播放，而无需手动创建所有内容变体。
开发人员添加演绎版映射属性和规则后，您现在可以将演绎版映射应用到资产，并随后将其包含在AEM Screens渠道中。

>[!IMPORTANT]
>在开始使用自适应演绎版之前，建议您在AEM Screens渠道中了解此功能的架构概述和配置。 请参阅自适应演绎版：架构概述和配置，以了解更多详细信息。

## 迁移策略 {#migration-strategy}

>[!IMPORTANT]
>对于大型网络，建议逐步迁移以降低风险，因为该功能将对清单和文件存储格式进行更改。

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


## 在AEM Screens渠道中上传演绎版和使用自适应演绎版 {#upload-renditions}

1. 创建更适合标牌显示的资产版本，例如`portrait orientation`。

1. 选择演绎版命名模式，例如`portrait`。

1. 重命名资产文件，使其包含模式，例如`my_asset_portrait.png`。

1. 单击&#x200B;**添加演绎版**&#x200B;以上传演绎版，如下图所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/add-rendition.png)