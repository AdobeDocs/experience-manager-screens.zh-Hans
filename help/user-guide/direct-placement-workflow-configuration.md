---
title: '直接放置工作流配置 '
seo-title: 直接放置工作流配置
description: 本页重点介绍了直接放置工作流配置。
seo-description: 本页重点介绍了直接放置工作流配置。
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# 直接放置工作流配置{#direct-placement-workflow}

可查看本页以了解有关配置资产工作流的信息，该工作流允许您以编程方式将资产插入预定义的AEM Screens渠道。

本节涵盖以下主题：

* 概述
* 配置直接放置工作流

## 概述 {#overview}

直接放置工作流配置可将AEM Screens项目渠道映射到资产中的特定文件夹，并允许在该文件夹中放置任何资产。 建议触发批量离线更新以完成发布。

或者，作为内容作者，您也可以手动单击&#x200B;**更新离线内容**。

>[!NOTE]
>
>要了解如何使用批量离线更新，请参阅[内容更新为服务](/help/user-guide/content-update-as-a-service.md)。

## 配置直接放置工作流{#configuring-workflow}

>[!IMPORTANT]
>
>在开始配置之前，必须安装[演示包](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)。 安装包后，您应该能够从AEM实例 — >工具（图标） — > **工作流** —> **工作流模型**&#x200B;中查看并访问该包。

请按照以下步骤配置直接投放工作流：

1. 从AEM实例导航到AEM Screens，并创建一个标题为&#x200B;**资产工作流**&#x200B;的Screens项目。

1. 在&#x200B;**渠道**&#x200B;文件夹下，创建标题为&#x200B;**Workflow-Assets**&#x200B;的渠道。

