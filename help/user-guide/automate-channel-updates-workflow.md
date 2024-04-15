---
title: 使用工作流自动更新AEM Screens渠道的资源
description: 了解如何创建工作流以自动处理上传到Adobe Experience Manager的资源并动态将其分配到Screens渠道。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 3c4b37b3b9f268b500562fa4ce3782b7be1e7d74
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 1%

---


# 使用工作流自动更新AEM Screens渠道的资源 {#automate-channel-updates-workflow}

了解如何创建工作流以自动处理上传到Adobe Experience Manager的资源并动态将其分配到Screens渠道。 在此示例中，将图像添加到特定文件夹时，会触发一个工作流，该工作流应用动态文本叠加（水印流程）并将图像分配到Screens渠道。 从本示例中汲取的经验教训可以应用于各种自动化场景。

## 先决条件 {#prerequisites}

要完成本教程，需要执行以下操作：

1. [AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65)
1. [AEM Service Pack 8或更高版本](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/release-notes)
1. [AEM 6.5 Screens FP7或更高版本](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103)

## 快速设置 {#quick-setup}

以下视频介绍了如何安装向Adobe Experience Manager引入新工作流的示例代码包。 此功能允许用户更新AEM Assets中文件夹的属性，以指向Screens渠道。 每当向该文件夹添加图像时，该图像都会添加到指定的AEM Screens渠道中。

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. 下载编译后的代码包： **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. 使用AEM包管理器安装上述包。

## 工作流模型 {#workflow-model}

已创建自定义文件夹元数据架构，以捕获应添加图像的目标Screens渠道。 可使用两个工作流模型来自动处理资源。 此 **DAM更新资产** 修改工作流以调用自定义工作流， **Screens演示资产处理** ，可检查资产的包含文件夹以确定目标Screens渠道。 此 **Screens演示资产处理** 工作流还负责将水印应用到图像。

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## 自定义工作流流程步骤 {#workflow-process-step}

Inspect中用到的两个自定义工作流流程步骤 **Screens演示资产处理** 工作流。

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

此 `AssetProcessingCheck.java` 自定义工作流是对工作流的有效负载执行检查的进程。 它可确定有效负载是否为资源，以及包含文件夹是否配置为指向AEM Screens渠道。 如果满足要求，则流程步骤将保留两个属性： `screen-channel` 和 `asset-path`，更改为工作流的元数据。

此 `AddAssetToChannel.java` 自定义工作流是一个流程步骤，可检查工作流的元数据并更新AEM Screens渠道以引用图像。

1. 下载源代码： **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. 使用您喜爱的IDE解压缩并查看代码。
