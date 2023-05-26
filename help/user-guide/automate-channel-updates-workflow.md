---
title: 使用工作流自动更新AEM Screens渠道的资源
seo-title: Use workflow to automate asset updates for an AEM Screens channel
description: 了解如何创建工作流以自动处理上传到Adobe Experience Manager的资源并动态地将它们分配给Screens渠道。 在此示例中，当将图像添加到特定文件夹时，将触发一个工作流，该工作流应用动态水印并将图像分配给Screens渠道。 从本示例中汲取的经验教训可以应用于各种自动化场景。
seo-description: Learn how to create a workflow to automatically process assets uploaded to Adobe Experience Manager and dynamically assign them to a Screens channel. In this example when an image is added to a specific folder, a workflow is triggered that applies a dynamic watermark and assigns the image to a Screens channel. Lessons learned from this example can be applied to a wide variety of automation scenarios.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 8d1633dab9e70ea988516cf9ee4d1b0a780bc7e9
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 5%

---


# 使用工作流自动更新AEM Screens渠道的资源 {#automate-channel-updates-workflow}

了解如何创建工作流以自动处理上传到Adobe Experience Manager的资源并动态地将它们分配给Screens渠道。 在此示例中，将图像添加到特定文件夹时，会触发一个工作流，该工作流应用动态文本叠加（水印流程）并将图像分配给Screens渠道。 从本示例中汲取的经验教训可以应用于各种自动化场景。

## 前提条件 {#prerequisites}

要完成本教程，需要执行以下操作：

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=zh-Hans)
1. [AEM Service Pack 8或更高版本](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html)
1. [AEM 6.5 Screens FP7或更高版本](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## 快速设置 {#quick-setup}

以下视频演示了如何安装示例代码包，该代码包将向Adobe Experience Manager引入新工作流。 此功能允许用户更新AEM Assets中文件夹的属性，以指向Screens频道。 每当向该文件夹添加图像时，该图像都会添加到指定的Screens渠道中。

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. 下载编译后的代码包： **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. 使用AEM包管理器安装上述包。

## 工作流模型 {#workflow-model}

已创建自定义文件夹元数据架构，以捕获应添加图像的目标Screens渠道。 可使用两个工作流模型来自动处理资源。 此 **DAM更新资产** 修改了工作流以调用自定义工作流， **Screens演示资产处理** ，这将检查资产的包含文件夹以确定目标Screens渠道。 此 **Screens演示资产处理** 工作流还负责将水印应用于图像。

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## 自定义工作流流程步骤 {#workflow-process-step}

Inspect的两个自定义工作流流程步骤，它们用作 **Screens演示资产处理** 工作流。

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` 是一个自定义工作流进程，它检查工作流的有效负载以确定该有效负载是否为资产，以及包含文件夹是否配置为指向Screens渠道。 如果满足要求，则流程步骤将保留两个属性： `screen-channel` 和 `asset-path`，指向工作流的元数据。

`AddAssetToChannel.java` 是一个自定义工作流流程步骤，用于检查工作流的元数据并更新Screens渠道以引用图像。

1. 下载源代码： **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. 使用您喜爱的IDE解压缩并查看代码。
