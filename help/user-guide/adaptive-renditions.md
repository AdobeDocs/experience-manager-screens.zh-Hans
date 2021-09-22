---
title: AEM Screens中的自适应演绎版
description: 本页介绍了AEM Screens中自适应呈现的架构概述和配置。
index: false
source-git-commit: 08f47e6542a7832f64d5d0dde9cdd463176f5f5d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 1%

---


# 自适应演绎版：体系结构概述和配置 {#adaptive-renditions}

## 简介 {#introduction}

自适应演绎版允许设备根据客户定义的规则自动为设备选择最佳演绎版。 这些设备将根据这些规则自动下载并播放资产的最合适演绎版，这样客户就只能专注于设计&#x200B;*主*&#x200B;体验。

## 目标 {#objective}

作为AEM Screens开发人员，您现在可以将特定于设备的资产演绎版配置为自动下载和播放，而无需手动创建所有内容变体。 您必须先配置自适应演绎版，内容作者才能在AEM Screens渠道中使用此功能。

因此，如果您部署了多种设备，则使用此功能后，设备将可以根据规则自动下载和播放资产的最合适演绎版。

## 架构概述 {#architectural-overview}

自适应演绎版是基于这样一种想法：让多个资产演绎版按照特定的命名约定进行命名。 通过评估媒体查询表达式来决定是否播放特定呈现，这些表达式只能在具有预期功能的设备上解析。 具有关联的演绎版命名模式的功能定义了演绎版映射规则。 在计算所有可用的表达式后，Screens播放器将收集与匹配规则对应的命名模式。 在序列播放期间，通过查找演绎版名称中的模式，可使用这些模式找到正确的演绎版。

![图像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## 配置设置以使用自适应演绎版 {#setup-adaptive-renditions}

要启用自适应演绎版功能，应当存在映射规则，并且CA配置可针对渠道进行解析并显示：

1. 检查`JCR`中是否存在演绎版映射配置。 所有最新功能包都预填充了此节点结构。

   >[!NOTE]
   >所有最新功能包都预填充了此节点结构。

   ![图像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

1. 确保Screens项目具有与其关联的演绎版映射配置。

   * 使用Screens项目向导创建的每个新项目都将包含一个指向演绎版映射配置的引用。

      ![图像](/help/user-guide/assets/adaptive-renditions/mapping-rules2.png)

   * 在旧版Screens项目中，需要通过将指向`/conf/screens`的`sling:configRef`属性添加到项目内容节点来明确定义关联。

      ![图像](/help/user-guide/assets/adaptive-renditions/mapping-rules3.png)



## 设置创作和发布 {#setup-author-publish}

在使用自适应演绎版之前，请在创作和发布中考虑以下建议：

* 必须手动复制演绎版映射。

* 默认情况下，资产演绎版不会复制。 需要手动复制所有相关资产。

## 添加演绎版映射规则 {#add-rendition-mapping-rules}

1. 要添加映射规则，您需要在演绎版映射节点下创建类型为`nt:unstructured`的节点。

1. 使用包含查询表达式的值添加表达式属性。

   >[!NOTE]
   >请参阅[使用媒体查询语法](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)以了解更多信息。

1. 如果将表达式计算为true，请添加模式属性，其值包含将选中的演绎版命名模式。

   ![图像](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)



## 后续步骤 {#next-steps}

配置并上传演绎版后，您现在可以在AEM Screens渠道中使用自适应演绎版。 有关更多详细信息，请参阅使用自适应演绎版。
