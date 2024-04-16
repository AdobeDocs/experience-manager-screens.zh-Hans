---
title: 自适应演绎版架构概述和配置
description: 了解AEM Screens中自适应演绎版的CRXDE Lite中的架构概述和配置。
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 2%

---

# 自适应演绎版：架构概述和配置 {#adaptive-renditions}

## 简介 {#introduction}

自适应演绎版允许设备根据客户定义的规则自动单击适合设备的最佳演绎版。 这些设备会根据这些规则自动下载并播放最合适的资源演绎版，从而让客户只需专注于设计 *主要* 体验。

## 目标 {#objective}

作为AEM Screens开发人员，您现在可以将特定于设备的资源呈现配置为自动下载和播放，而无需手动创建所有内容变体。 在内容作者能够在AEM Screens渠道中使用此功能之前，配置自适应演绎版。

## 架构概述 {#architectural-overview}

自适应演绎版基于这样一种理念：拥有一个按照特定命名惯例命名的资产的多个演绎版。 播放特定演绎版的决定是通过评估只能在具有预期功能的设备上解析的媒体查询表达式做出的。

具有关联的演绎版命名模式的功能定义了一个演绎版映射规则，如纵向或横向，如下图所示。 计算所有可用表达式后，Screens播放器会收集与匹配规则对应的命名模式。 这些图案用于在序列播放过程中通过查找演绎版名称中的图案来查找正确的演绎版。

![图像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## 将演绎版映射属性添加到屏幕项目 {#rendition-mapping-new}

要启用自适应演绎版功能，应存在以下映射规则，并且上下文感知(CA)配置对于渠道和显示应可解析。

>[!NOTE]
>要了解有关内容感知配置的更多信息，请参阅 [此处](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

请按照以下步骤配置设置：

1. 导航到 **CRXDE Lite**. 检查，如果 **演绎版映射** 配置存在于中 `/conf/screens/sling:configs/rendition-mapping`，如下图所示。

   >![图像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >如果您安装了最新的功能包202109，您会看到 **演绎版映射** 在中预填充的节点结构 `/conf/screens/sling:configs/rendition-mapping` CRXDE Lite中。 请参阅 [功能包202109发行说明](/help/user-guide/release-notes-fp-202109.md) 以了解有关最新功能包的详细信息。
   >对于现有项目，请确保屏幕项目具有 **演绎版映射** 关联的配置。 请参阅 [将演绎版映射添加到现有项目](#rendition-mapping-existing) 部分以了解更多信息。

### 将演绎版映射属性添加到现有项目 {#rendition-mapping-existing}

1. 导航到 **CRXDE Lite**.

1. 通过添加显式定义演绎版 — 映射关联 `sling:configRef` 属性指向 `/conf/screens` “项目内容”节点，如下图所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## 添加节目映射规则 {#add-rendition-mapping-rules}

按照以下步骤在“节目映射”下添加节点：

1. 导航到此路径 `/conf/screens/sling:configs/rendition-mapping` 从 **CRXDE Lite**.
1. 在下创建节点 **演绎版映射**. 右键单击 **演绎版映射** 并单击 **创建** > **创建节点**，如下图所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. 输入 **名称** 的映射规则，例如 **规则1** 和节点 **类型** 作为 **`nt:unstructured`** 在 **创建节点** 对话框。 单击&#x200B;**确定**。

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. 使用包含查询表达式的值添加表达式属性。

   >[!NOTE]
   >请参阅 [使用媒体查询语法](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries) 了解更多信息。

   单击 **规则1** 创建，然后输入 **表达式** 在 **名称** 和 **(orientation：landscape)** 在 **值**，如下所示。 单击 **添加**.

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. 添加pattern属性，其值包含演绎版命名模式。

   >[!NOTE]
   >pattern属性中定义的值与新资源演绎版匹配，如果表达式被计算为true，则选中该值。

   要添加模式属性，请单击 **规则1** 创建，然后输入 **模式** 在 **名称** 和 **横向** 在 **值**，如下所示。 单击 **添加**.

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. 单击 **全部保存** 并注意您在下创建的节点下的属性 **演绎版映射**.

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## 后续步骤 {#next-steps}

在添加演绎版映射属性和规则后，作为内容作者，您可以配置资源。 为此，您需要使用自适应演绎版，并且还要为大型网络迁移设备，以便在AEM Screens渠道中使用此功能。 请参阅 [在AEM Screens中使用自适应演绎版](/help/user-guide/using-adaptive-renditions.md) 以了解更多信息。
