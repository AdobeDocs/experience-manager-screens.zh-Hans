---
title: 自适应演绎版架构概述和配置
description: 了解AEM Screens中自适应演绎版的CRXDE Lite中的架构概述和配置。
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 2%

---

# 自适应演绎版：架构概述和配置 {#adaptive-renditions}

## 简介 {#introduction}

自适应演绎版允许设备根据客户定义的规则自动单击设备的最佳演绎版。 设备根据这些规则自动下载并播放最合适的资源演绎版，从而允许客户专注于设计&#x200B;*main*&#x200B;体验。

## 目标 {#objective}

作为AEM Screens开发人员，您现在可以将特定于设备的资源呈现配置为自动下载和播放，而无需手动创建所有内容变体。 在内容作者能够在AEM Screens渠道中使用此功能之前配置自适应演绎版。

## 架构概述 {#architectural-overview}

自适应演绎版基于这样一种理念：拥有一个按照特定命名惯例命名的资产的多个演绎版。 播放特定演绎版的决定是通过评估只能在具有预期功能的设备上解析的媒体查询表达式做出的。

具有关联的演绎版命名模式的功能定义了一个演绎版映射规则，如纵向或横向，如下图所示。 计算所有可用表达式后，Screens播放器会收集与匹配规则对应的命名模式。 这些图案用于在序列播放过程中通过查找演绎版名称中的图案来查找正确的演绎版。

![图像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## 将演绎版映射属性添加到Screens项目 {#rendition-mapping-new}

要启用自适应演绎版功能，应存在以下映射规则，并且上下文感知(CA)配置对于渠道和显示应可解析。

>[!NOTE]
>若要了解有关内容感知配置的更多信息，请参阅[此处](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)。

请按照以下步骤配置设置：

1. 导航到&#x200B;**CRXDE Lite**。 检查`/conf/screens/sling:configs/rendition-mapping`中是否存在&#x200B;**rendition-mapping**&#x200B;配置，如下图所示。

   >![图像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >如果您安装了最新的功能包202109，则会在CRXDE Lite中看到`/conf/screens/sling:configs/rendition-mapping`中预填充的&#x200B;**rendition-mapping**&#x200B;节点结构。 请参阅[功能包202109](/help/user-guide/release-notes-fp-202109.md)的发行说明，以了解有关最新功能包的详细信息。
   >对于现有项目，请确保Screens项目具有关联的&#x200B;**rendition-mapping**&#x200B;配置。 有关详细信息，请参阅[将演绎版映射添加到现有项目](#rendition-mapping-existing)部分。

### 将演绎版映射属性添加到现有项目 {#rendition-mapping-existing}

1. 导航到&#x200B;**CRXDE Lite**。

1. 通过将指向`/conf/screens`的`sling:configRef`属性添加到项目内容节点，显式定义格式副本映射关联，如下图所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## 添加节目映射规则 {#add-rendition-mapping-rules}

按照以下步骤在“节目映射”下添加节点：

1. 从&#x200B;**CRXDE Lite**&#x200B;导航到此路径`/conf/screens/sling:configs/rendition-mapping`。
1. 在&#x200B;**rendition-mapping**&#x200B;下创建节点。 右键单击&#x200B;**rendition-mapping**，然后单击&#x200B;**创建** > **创建节点**，如下图所示。

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. 在&#x200B;**创建节点**&#x200B;对话框中输入映射规则的&#x200B;**名称**，例如&#x200B;**规则1**，节点&#x200B;**类型**&#x200B;为&#x200B;**`nt:unstructured`**。 单击&#x200B;**确定**。

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. 使用包含查询表达式的值添加表达式属性。

   >[!NOTE]
   >请参阅[使用媒体查询语法](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries)以了解详情。

   单击您创建的&#x200B;**规则1**，然后在&#x200B;**名称**&#x200B;中输入&#x200B;**表达式**，在&#x200B;**值**&#x200B;中输入&#x200B;**(orientation：landscape)**，如下所示。 单击&#x200B;**添加**。

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. 添加pattern属性，其值包含演绎版命名模式。

   >[!NOTE]
   >pattern属性中定义的值与新资源演绎版匹配，如果表达式被计算为true，则选中该值。

   要添加模式属性，请单击您创建的&#x200B;**规则1**，然后在&#x200B;**名称**&#x200B;中输入&#x200B;**模式**，在&#x200B;**值**&#x200B;中输入&#x200B;**横向**，如下所示。 单击&#x200B;**添加**。

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. 单击&#x200B;**全部保存**，并注意您在&#x200B;**rendition-mapping**&#x200B;下创建的节点下的属性。

   ![图像](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## 后续步骤 {#next-steps}

在添加演绎版映射属性和规则后，作为内容作者，您可以配置资源。 您可以使用自适应演绎版，还可以为大型网络迁移设备，以便在AEM Screens渠道中使用此功能。 有关详细信息，请参阅[在AEM Screens中使用自适应演绎版](/help/user-guide/using-adaptive-renditions.md)。
