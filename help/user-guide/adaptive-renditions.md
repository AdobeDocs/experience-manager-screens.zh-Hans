---
title: 自适应演绎版体系结构概述和配置
description: 本页介绍了AEM Screens中自适应演绎版的CRXDE Lite架构概述和配置。
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: e5da55eeb5da3d0ef9f21bd47bfec75d660a6a1e
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 3%

---

# 自适应演绎版：架构概述和配置 {#adaptive-renditions}

## 简介 {#introduction}

自适应呈现版本允许设备根据客户定义的规则自动为设备选择最佳呈现版本。 这些设备将根据这些规则自动下载并播放最合适的资源演绎版，从而让客户只需专注于设计 *主要* 体验。

## 目标 {#objective}

作为AEM Screens开发人员，您现在可以将特定于设备的资源演绎版配置为自动下载和播放，而无需手动创建所有内容变体。 必须先配置自适应演绎版，内容作者才能在AEM Screens渠道中使用此功能。

## 架构概述 {#architectural-overview}

自适应演绎版基于以下理念：让多个资源演绎版按照特定的命名约定命名。 播放特定演绎版的决定是通过评估只能在具有预期功能的设备上解析的媒体查询表达式做出的。

具有关联的演绎版命名模式的功能定义了演绎版映射规则，例如纵向或横向，如下图所示。 计算所有可用表达式后，Screens播放器将收集与匹配规则对应的命名模式。 在序列播放过程中，可以使用模式通过查找演绎版名称中的模式来查找正确的演绎版。

![图像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## 将演绎版映射属性添加到屏幕项目 {#rendition-mapping-new}

要启用自适应呈现版本功能，应存在以下映射规则，并且上下文感知(CA)配置对于渠道和显示应该是可解析的。

>[!NOTE]
>要了解有关内容感知配置的更多信息，请参阅 [此处](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

按照以下步骤配置设置：

1. 导航到 **CRXDE Lite**. 检查，如果 **演绎版映射** 配置存在于 `/conf/screens/sling:configs/rendition-mapping`，如下图所示。

   >![图像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >如果您安装了最新的功能包202109，您将看到 **演绎版映射** 节点结构预填充于 `/conf/screens/sling:configs/rendition-mapping` 在CRXDE Lite中。 参见 [功能包202109的发行说明](/help/user-guide/release-notes-fp-202109.md) 以了解有关最新功能包的详细信息。
   >对于现有项目，请确保屏幕项目具有 **演绎版映射** 关联的配置。 参见 [将演绎版映射添加到现有项目](#rendition-mapping-existing) 部分，了解更多信息。

### 将演绎版映射属性添加到现有项目 {#rendition-mapping-existing}

1. 导航到 **CRXDE Lite**.

1. 通过添加来明确定义演绎版映射关联 `sling:configRef` 属性指向 `/conf/screens` “项目内容”节点，如下图所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## 添加节目映射规则 {#add-rendition-mapping-rules}

按照以下步骤在“节目映射”下添加节点：

1. 导航到此路径 `/conf/screens/sling:configs/rendition-mapping` 起始日期 **CRXDE Lite**.

1. 在下创建节点 **演绎版映射**. 右键单击 **演绎版映射** 并单击 **创建** —> **创建节点**，如下图所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. 输入 **名称** 映射规则，例如 **rule1** 和节点 **类型** 作为 **nt：unstructured** 在 **创建节点** 对话框。 单击 **确定**.

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. 您需要添加表达式属性，其值包含查询表达式。

   >[!NOTE]
   >请参阅 [使用媒体查询语法](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) 了解更多信息。

   单击 **rule1** ，然后输入 **表达式** 在 **名称** 和 **(orientation：landscape)** 在 **值**，如下所示。 单击 **添加**.

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. 添加pattern属性，其值包含演绎版命名模式。

   >[!NOTE]
   >pattern属性中定义的值将与新资源演绎版匹配，如果表达式被评估为true，则将选择此值。

   要添加pattern属性，请单击 **rule1** ，然后输入 **模式** 在 **名称** 和 **横向** 在 **值**，如下所示。 单击 **添加**.

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. 单击 **全部保存** 并且您将在您创建的节点下看到属性 **演绎版映射**.

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## 后续步骤 {#next-steps}

添加演绎版映射属性和规则后，现在作为内容作者，您可以将资源配置为使用自适应演绎版，还可以在AEM Screens渠道中为大型网络迁移设备以使用此功能。 参见 [在AEM Screens中使用自适应演绎版](/help/user-guide/using-adaptive-renditions.md) 了解更多详细信息。
