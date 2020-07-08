---
title: '直接放置工作流配置 '
seo-title: 直接放置工作流配置
description: 本页重点介绍直接放置工作流配置。
seo-description: 本页重点介绍直接放置工作流配置。
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# 直接放置工作流配置 {#direct-placement-workflow}

可查看本页以了解有关配置资产工作流的信息，该工作流允许您以编程方式将资产插入预定义的AEM Screens渠道。

本节涵盖以下主题：

* 概述
* 配置直接置入工作流

## 概述 {#overview}

直接放置工作流配置将AEM Screens项目渠道映射到资产中的特定文件夹，并允许将任何资产放置到该文件夹中。 建议触发批量脱机更新以完成发布。

或者，作为内容作者，您也可以手动单击“更 **新脱机内容”**。

>[!NOTE]
>
>要了解如何使用批量脱机更新，请参 [阅内容更新为服务](/help/user-guide/content-update-as-a-service.md)。

## 配置直接置入工作流 {#configuring-workflow}

>[!IMPORTANT]
>
>在开始配置之前，必须安装演 [示包](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)。 安装包后，您应能够从AEM实例—>工具（图标）—>工作流—>工作流模型中视图并 **访问** 它 ****。

请按照以下步骤配置直接放置工作流：

1. 导航到AEM实例中的AEM Screens，然后创建标题为“资产工作流” **的Screens项目**。

1. 在“渠道”文件夹 **下创建标题为** “工作 **流资产** ”的渠道。

1. 
