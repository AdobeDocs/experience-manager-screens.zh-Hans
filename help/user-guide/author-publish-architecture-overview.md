---
title: 创作和发布架构概述
seo-title: 创作和发布架构概述
description: AEM Screens架构类似于传统的AEM Sites架构。 在AEM创作实例上创作内容，然后将其转发复制到多个发布实例。 可查看本页以了解有关作者和发布架构概述的更多信息。
seo-description: AEM Screens架构类似于传统的AEM Sites架构。 在AEM创作实例上创作内容，然后将其转发复制到多个发布实例。 可查看本页以了解有关作者和发布架构概述的更多信息。
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
feature: 管理屏幕
role: Administrator, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 3%

---

# 创作和发布架构概述{#author-and-publish-architectural-overview}

本页重点介绍以下主题：

* **发布服务器简介**
* **架构概述**
* **注册流程**

## 前提条件 {#prerequisites}

在开始使用创作和发布服务器之前，您应该事先了解：

* **AEM拓扑**
* **创建和管理AEM Screens项目**
* **设备注册过程**

>[!NOTE]
>
>仅当您安装了AEM 6.4 Screens功能包2时，才提供此AEM Screens功能。 要获取此功能包，您必须联系 Adobe 支持人员并申请访问权限。您获得权限后，就可以从“包共享”下载它。

## 简介 {#introduction}

AEM Screens架构类似于传统的AEM Sites架构。 在AEM创作实例上创作内容，然后将其转发复制到多个发布实例。 AEM Screens设备现在可以通过负载平衡器连接到AEM发布场。 可以添加多个AEM发布实例以继续扩展发布场。

*例如*,AEM Screens内容作者在创作系统中为特定设备发出命令，该设备配置为与发布场交互，或者为AEM Screens内容作者发出命令，该设备获取有关配置为与发布场交互的设备的信息。

下图说明了创作和发布环境。

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## 架构设计{#architectural-design}

有五个体系结构组件，可促进此解决方案：

* ***将内*** 容从创作复制到发布以供设备显示

* ****** 将二进制内容从发布（从设备接收）还原为创作
* ****** 通过特定REST API将从创作到发布的命令发送到
* ****** 在发布实例之间发送消息以同步设备信息更新和命令
* ****** 由发布实例作者通过特定REST API获取设备信息的轮询

### 内容和配置的复制（转发）{#replication-forward-of-content-and-configurations}

标准复制代理用于复制Screens渠道内容、位置配置和设备配置。 这允许作者在发布渠道更新之前更新渠道的内容，并选择性地执行某种批准工作流程。 需要为发布场中的每个发布实例创建复制代理。

下图说明了复制过程：

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>需要为发布场中的每个发布实例创建复制代理。

### 屏幕复制代理和命令{#screens-replication-agents-and-commands}

将创建特定于自定义屏幕的复制代理，以将命令从创作实例发送到AEM Screens设备。 AEM Publish实例用作将这些命令转发到设备的中介。

这允许作者继续管理设备，例如发送设备更新，并从创作环境中拍摄屏幕截图。 AEM Screens复制代理具有自定义传输配置，如标准复制代理。

### 发布实例{#messaging-between-publish-instances}之间的消息传送

在很多情况下，命令仅用于一次发送到设备。 但是，在负载平衡的发布架构中，设备正在连接哪个发布实例尚未可知。

因此，创作实例会将消息发送到所有发布实例。 但是，只应将一条消息中继到设备。 要确保消息正确，必须在发布实例之间进行一些通信。 使用&#x200B;*Apache ActiveMQ Artemis*&#x200B;实现此目的。 每个发布实例都使用基于Oak的Sling发现服务放置在一个松散耦合的拓扑中，并且配置了ActiveMQ，以便每个发布实例都可以通信并创建单个消息队列。 Screens设备通过负载平衡器轮询发布场，并从队列顶部选取命令。

### 反向复制{#reverse-replication}

在许多情况下，在发出命令后，Screens设备中会出现某种响应，需要将其转发到创作实例。 为了实现此AEM ***使用反向复制***。

* 为每个发布实例创建反向复制代理，类似于标准复制代理和屏幕复制代理。
* 工作流启动器配置监听发布实例上修改的节点，然后触发一个工作流，将设备响应放置在发布实例的发件箱中。
* 此上下文中的反向复制仅用于设备提供的二进制数据（例如，日志文件和屏幕截图）。 非二进制数据通过轮询进行检索。
* 从AEM创作实例轮询的反向复制将检索响应并将其保存到创作实例。

### 轮询发布实例{#polling-of-publish-instances}

创作实例需要能够轮询设备以获取心率并了解已连接设备的运行状况。

设备ping负载平衡器并被路由到发布实例。 随后，发布实例会通过在&#x200B;**api/screens-dcc/devices/static**&#x200B;中提供的发布API（适用于所有活动设备）和&#x200B;**api/screens-dcc/devices/&lt;device_id>/status.json**&#x200B;中针对单个设备公开设备的状态。

创作实例会轮询所有发布实例，并将设备状态响应合并到单个状态。 在作者上轮询的计划作业是`com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob`，可以基于cron表达式进行配置。

## 注册 {#registration}

注册仍源自AEM创作实例。 AEM Screens设备指向创作实例，并且注册已完成。

在创作环境中注册设备后，设备配置和渠道/计划分配将复制到AEM发布实例。 然后，将更新AEM Screens设备配置，以指向AEM发布场前的负载平衡器。 这是一次性设置，在Screens设备成功连接到发布环境后，它可以继续接收来自创作环境的命令，而且从来不需要将Screens设备直接连接到创作环境。

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### 后续步骤 {#the-next-steps}

了解AEM Screens中作者和发布设置的体系结构设计后，请参阅[为AEM Screens配置作者和发布](author-and-publish.md) ，以获取更多详细信息。
