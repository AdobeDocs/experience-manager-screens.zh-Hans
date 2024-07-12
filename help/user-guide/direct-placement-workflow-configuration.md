---
title: 直接放置工作流配置
description: 本页重点介绍直接放置工作流配置。
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 1%

---


# 直接放置工作流配置 {#direct-placement-workflow}

关注此页面，以便了解如何配置资源工作流，该工作流允许您以编程方式将资源插入到预定义的AEM Screens渠道。

本节涵盖以下主题：

* 概述
* 配置直接放置工作流

## 概述 {#overview}

直接放置工作流配置将AEM Screens项目渠道映射到资源中的特定文件夹，并允许在该文件夹中放置任何资源。 Adobe建议您触发批量脱机更新以完成发布。

或者，作为内容作者，您可以手动单击&#x200B;**更新离线内容**。

>[!NOTE]
>
>要了解如何使用批量脱机更新，请参阅[内容更新即服务](/help/user-guide/content-update-as-a-service.md)。

## 配置直接放置工作流 {#configuring-workflow}

>[!IMPORTANT]
>
>开始配置之前，请安装`[Demo  Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)`。 安装包后，您应该能够从AEM实例>工具（图标）> **工作流** > **工作流模型**&#x200B;查看和访问包。

请按照以下步骤配置直接放置工作流：

1. 从您的AEM实例导航到AEM Screens，并创建一个标题为&#x200B;**资产工作流**&#x200B;的Screens项目。

1. 在&#x200B;**Channels**&#x200B;文件夹下创建标题为&#x200B;**Workflow-Assets**&#x200B;的频道。

