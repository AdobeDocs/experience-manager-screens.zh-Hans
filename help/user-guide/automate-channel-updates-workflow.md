---
title: 使用工作流自动更新AEM Screens渠道的资产
seo-title: 使用工作流自动更新AEM Screens渠道的资产
description: 了解如何创建工作流以自动处理上传到Adobe Experience Manager的资产，并将其动态分配到Screens渠道。 在此示例中，当将图像添加到特定文件夹时，将触发一个工作流，该工作流会应用动态水印并将图像分配到Screens渠道。 从此示例中吸取的经验教训可以应用于各种自动化情景。
seo-description: 了解如何创建工作流以自动处理上传到Adobe Experience Manager的资产，并将其动态分配到Screens渠道。 在此示例中，当将图像添加到特定文件夹时，将触发一个工作流，该工作流会应用动态水印并将图像分配到Screens渠道。 从此示例中吸取的经验教训可以应用于各种自动化情景。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: 开发屏幕
role: Developer
level: Intermediate
source-git-commit: 8d1633dab9e70ea988516cf9ee4d1b0a780bc7e9
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 2%

---


# 使用工作流自动更新AEM Screens渠道{#automate-channel-updates-workflow}的资产

了解如何创建工作流以自动处理上传到Adobe Experience Manager的资产，并将其动态分配到Screens渠道。 在此示例中，当将图像添加到特定文件夹时，将触发一个工作流，该工作流会应用动态文本叠加（水印过程）并将图像分配到Screens渠道。 从此示例中吸取的经验教训可以应用于各种自动化情景。

## 前提条件 {#prerequisites}

要完成本教程，需要满足以下条件：

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=zh-Hans)
1. [AEM Service Pack 8或更高版本](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=zh-Hans)
1. [AEM 6.5 Screens FP7或更高版本](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## 快速设置{#quick-setup}

以下视频演示了如何安装示例代码包，该代码包将向Adobe Experience Manager引入新的工作流。 此功能允许用户更新AEM Assets中文件夹的属性以指向Screens渠道。 每当将图像添加到该文件夹时，都会将其添加到指定的屏幕渠道中。

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. 下载编译的代码包：**[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. 使用AEM包管理器安装上述包。

## 工作流模型 {#workflow-model}

创建了自定义文件夹元数据架构，以捕获应添加图像的目标Screens渠道。 可使用两个工作流模型来自动处理资产。 修改了&#x200B;**DAM更新资产**&#x200B;工作流以调用自定义工作流&#x200B;**Screens演示资产处理**，该工作流将检查资产的包含文件夹以确定目标Screens渠道。 **Screens演示资产处理**&#x200B;工作流还负责将水印应用到图像。

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## 自定义工作流流程步骤{#workflow-process-step}

Inspect两个自定义工作流流程步骤，用作&#x200B;**Screens演示资产处理**&#x200B;工作流的一部分。

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` 是一个自定义工作流流程，用于对工作流的有效负载执行检查，以确定有效负载是否为资产，以及容器文件夹是否配置为指向Screens渠道。如果满足要求，流程步骤会将`screen-channel`和`asset-path`两个属性保留到工作流的元数据中。

`AddAssetToChannel.java` 是一个自定义工作流流程步骤，用于检查工作流的元数据并更新Screens渠道以引用图像。

1. 下载源代码：**[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. 使用您喜爱的IDE解压缩并查看代码。
