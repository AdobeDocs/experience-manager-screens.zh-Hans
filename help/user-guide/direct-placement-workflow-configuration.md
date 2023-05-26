---
title: 直接投放工作流配置
seo-title: Direct Placement Workflow Configuration
description: 本页重点介绍直接放置工作流配置。
seo-description: This page highlights Direct Placement Workflow Configuration.
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# 直接投放工作流配置 {#direct-placement-workflow}

阅读本页，了解如何配置资源工作流，以便通过编程方式将资源插入到预定义的AEM Screens渠道。

本节涵盖以下主题：

* 概述
* 配置直接投放工作流

## 概述 {#overview}

直接放置工作流配置将AEM Screens项目渠道映射到资源中的特定文件夹，并允许在该文件夹中放置任何资源。 建议触发批量脱机更新以完成发布。

或者，作为内容作者，您可以手动单击 **更新离线内容**.

>[!NOTE]
>
>要了解如何使用批量脱机更新，请参阅 [内容更新即服务](/help/user-guide/content-update-as-a-service.md).

## 配置直接投放工作流 {#configuring-workflow}

>[!IMPORTANT]
>
>在开始配置之前，您必须安装 [演示包](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). 安装包后，您应该能够从AEM实例查看和访问包 — >工具（图标） — > **工作流** —> **工作流模型**.

按照以下步骤配置直接投放工作流：

1. 从您的AEM实例导航到AEM Screens，并创建一个标题为 **资产工作流**.

1. 创建标题为 **Workflow-Assets** 下 **渠道** 文件夹。

