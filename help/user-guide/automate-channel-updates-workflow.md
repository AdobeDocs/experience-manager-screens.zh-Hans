---
title: 使用工作流自动更新AEM Screens渠道的资产
seo-title: 使用工作流自动更新AEM Screens渠道的资产
description: 了解如何创建工作流，以自动处理上传到Adobe Experience Manager的资产并将资产动态分配给Screens渠道。 在此示例中，当将图像添加到特定文件夹时，将触发应用动态水印并将图像分配到Screens渠道的工作流。 从此示例中吸取的经验教训可以应用于各种自动化场景。
seo-description: 了解如何创建工作流，以自动处理上传到Adobe Experience Manager的资产并将资产动态分配给Screens渠道。 在此示例中，当将图像添加到特定文件夹时，将触发应用动态水印并将图像分配到Screens渠道的工作流。 从此示例中吸取的经验教训可以应用于各种自动化场景。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: 开发屏幕
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 1667fd10f415214a5301e9740d205eb33cc34f89
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 3%

---


# 使用工作流自动更新AEM Screens渠道{#automate-channel-updates-workflow}的资产

了解如何创建工作流，以自动处理上传到Adobe Experience Manager的资产并将资产动态分配给Screens渠道。 在此示例中，当将图像添加到特定文件夹时，将触发应用动态水印并将图像分配到Screens渠道的工作流。 从此示例中吸取的经验教训可以应用于各种自动化场景。

## 前提条件 {#prerequisites}

要完成本教程，需要执行以下操作：

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=zh-Hans)
1. [AEM Service Pack 8或更高版本](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=zh-Hans)
1. [AEM 6.5 Screens FP7或更高](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## 快速设置{#quick-setup}

以下视频说明了如何安装示例代码包，该代码包将为Adobe Experience Manager引入新的工作流。 此功能允许用户更新AEM Assets中文件夹的属性以指向Screens渠道。 只要将图像添加到该文件夹，就会将其添加到指定的屏幕渠道。

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. 下载编译的代码包：**[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. 使用AEM Package Manager安装上述包。

## 工作流模型 {#workflow-model}

已创建自定义文件夹元数据模式，以捕获应添加图像的目标屏幕渠道。 两种工作流模型用于自动处理资产。 将修改&#x200B;**DAM更新资产**&#x200B;工作流以调用自定义工作流&#x200B;**屏幕演示资产处理**，该工作流将检查资产的包含文件夹以确定目标屏幕渠道。 **屏幕演示资产处理**&#x200B;工作流还负责将水印应用到图像。

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## 自定义工作流进程步骤{#workflow-process-step}

Inspect用作&#x200B;**屏幕演示资产处理**&#x200B;工作流的一部分的两个自定义工作流进程步骤。

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` 是一个自定义工作流进程，它会对工作流的有效负荷执行检查，以确定有效负荷是否为资产以及包含文件夹是否配置为指向Screens渠道。如果满足要求，则流程步骤会将两个属性（`screen-channel`和`asset-path`）保留到工作流的元数据中。

`AddAssetToChannel.java` 是一个自定义工作流进程步骤，它检查工作流的元数据并更新Screens渠道以引用图像。

1. 下载源代码：**[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. 使用您喜爱的IDE解压缩并视图代码。
