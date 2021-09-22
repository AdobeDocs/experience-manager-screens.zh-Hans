---
title: AEM Screens中的自适应演绎版
description: 本页介绍了AEM Screens中自适应呈现的架构概述和配置。
index: false
source-git-commit: 951fd38d5f69cdab1bf9b23f07b4e92075e87baf
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 2%

---


# 自适应演绎版：体系结构概述和配置 {#adaptive-renditions}

## 简介 {#introduction}

自适应演绎版允许设备根据客户定义的规则自动为设备选择最佳演绎版。 这些设备将根据这些规则自动下载并播放资产的最合适演绎版，这样客户就只能专注于设计&#x200B;*主*&#x200B;体验。

## 目标 {#objective}

作为AEM Screens开发人员，您现在可以将特定于设备的资产演绎版配置为自动下载和播放，而无需手动创建所有内容变体。 您必须先配置自适应演绎版，内容作者才能在AEM Screens渠道中使用此功能。

## 架构概述 {#architectural-overview}

自适应演绎版是基于这样一种想法：让多个资产演绎版按照特定的命名约定进行命名。 通过评估媒体查询表达式来决定是否播放特定呈现，这些表达式只能在具有预期功能的设备上解析。

具有关联的演绎版命名模式的功能可定义演绎版映射规则，如纵向或横向，如下图所示。 在计算所有可用的表达式后，Screens播放器将收集与匹配规则对应的命名模式。 在序列播放期间，通过查找演绎版名称中的模式，可使用这些模式找到正确的演绎版。

![图像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## 将演绎版映射属性添加到Screens项目 {#rendition-mapping-new}

要启用自适应演绎版功能，应当存在以下映射规则，并且上下文感知(CA)配置应当可以针对渠道和显示进行解析。

>[!NOTE]
>要了解有关内容感知配置的更多信息，请参阅[此处](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)。

请按照以下步骤配置设置：

1. 导航到&#x200B;**CRXDE Lite**。 如果&#x200B;**rendition-mapping**&#x200B;配置存在于`/conf/screens/sling:configs/rendition-mapping`中，请检查，如下图所示。

   >![图像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >如果安装了最新的功能包202109，您将看到在CRXDE Lite的`/conf/screens/sling:configs/rendition-mapping`中预填充了&#x200B;**rendition-mapping**&#x200B;节点结构。 请参阅[功能包202109](/help/user-guide/release-notes-fp-202109.md)发行说明，以获取有关最新功能包的详细信息。
   >对于现有项目，请确保Screens项目关联&#x200B;**rendition-mapping**&#x200B;配置。 请参阅[将演绎版映射添加到现有项目](#rendition-mapping-existing)一节，以了解更多信息。

### 将演绎版映射属性添加到现有项目 {#rendition-mapping-existing}

1. 导航到&#x200B;**CRXDE Lite**。

1. 通过向项目内容节点添加指向`/conf/screens`的`sling:configRef`属性来显式定义演绎版映射关联，如下图所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## 设置创作和发布 {#setup-author-publish}

在使用自适应演绎版之前，请在创作和发布中考虑以下建议：

* 必须手动复制演绎版映射。

* 默认情况下，资产演绎版不会复制。 需要手动复制所有相关资产。

## 添加演绎版映射规则 {#add-rendition-mapping-rules}

1. 要添加映射规则，您需要在&#x200B;**rendition-mapping**&#x200B;节点下创建类型为`nt:unstructured`的节点。

1. 使用包含查询表达式的值添加表达式属性。

   >[!NOTE]
   >请参阅[使用媒体查询语法](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)以了解更多信息。

1. 如果将表达式计算为true，请添加模式属性，其值包含将选中的演绎版命名模式。

   ![图像](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)


## 后续步骤 {#next-steps}

配置并上传演绎版后，您现在可以作为内容作者使用自适应演绎版，并且还可以在AEM Screens渠道中为大型网络迁移设备以使用此功能。 有关更多详细信息，请参阅[使用自适应演绎版](/help/user-guide/using-adaptive-renditions.md)。
