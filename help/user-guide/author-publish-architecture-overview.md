---
title: 创作和发布架构概述
seo-title: 创作和发布架构概述
description: AEM Screens架构类似于传统的AEM Sites架构。 内容是在AEM作者实例上创作的，然后转发复制到多个发布实例。 可查看本页以了解有关作者和发布架构概述的更多信息。
seo-description: AEM Screens架构类似于传统的AEM Sites架构。 内容是在AEM作者实例上创作的，然后转发复制到多个发布实例。 可查看本页以了解有关作者和发布架构概述的更多信息。
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 创作和发布架构概述 {#author-and-publish-architectural-overview}

本页重点介绍以下主题：

* **发布服务器简介**
* **架构概述**
* **注册流程**

## 前提条件 {#prerequisites}

在开始使用创作和发布服务器之前，您应该事先了解：

* **AEM Topology**
* **创建和管理AEM Screens项目**
* **设备注册过程**

>[!NOTE]
>
>此AEM Screens功能仅在您安装了AEM 6.4 Screens功能包2时可用。 要获取此功能包，您必须联系 Adobe 支持人员并申请访问权限。您获得权限后，就可以从“包共享”下载它。

## 简介 {#introduction}

AEM Screens架构类似于传统的AEM Sites架构。 内容是在AEM作者实例上创作的，然后转发复制到多个发布实例。 AEM Screens设备现在可以通过负载平衡器连接到AEM发布群。 可以添加多个AEM发布实例以继续缩放发布农场。

*例如*,AEM Screens内容作者在创作系统中为配置为与发布场交互的特定设备或AEM Screens内容作者发出命令，该内容作者获取有关配置为与发布场交互的设备的信息。

下图说明了创作和发布环境。

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## 建筑设计 {#architectural-design}

有五个架构组件，可促进此解决方案：

* ***将内容从作者复制*** ，发布到设备显示

* ***从发布*** （从设备接收）反向复制二进制内容到创作
* ***通过*** REST API将命令从作者发送到发布
* ***在发布实例*** 之间传递消息以同步设备信息更新和命令
* ***发布实例的作者*** 轮询，以通过特定的REST API获取设备信息

### 内容和配置的复制（转发） {#replication-forward-of-content-and-configurations}

标准复制代理用于复制屏幕渠道内容、位置配置和设备配置。 这允许作者更新渠道的内容，并有选择地在发布渠道更新之前完成某种类型的批准工作流程。 需要为发布场中的每个发布实例创建复制代理。

下图说明了复制过程：

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>需要为发布场中的每个发布实例创建复制代理。

### 屏幕复制代理和命令 {#screens-replication-agents-and-commands}

将创建特定于Screens的自定义复制代理，以将命令从Author实例发送到AEM Screens设备。 AEM Publish实例用作将这些命令转发到设备的中介。

这允许作者继续管理设备，如发送设备更新并从创作环境中拍摄截屏。 AEM Screens复制代理具有自定义传输配置，如标准复制代理。

### 发布实例之间的消息传递 {#messaging-between-publish-instances}

在很多情况下，命令仅一次发送到设备。 但是，在负载平衡发布架构中，未知设备要连接到哪个发布实例。

因此，作者实例会将消息发送到所有Publish实例。 但是，应该只向设备中继一条消息。 要确保消息的正确，必须在发布实例之间进行一些通信。 这是使用*Apache ActiveMQ Artemis实现的。 *每个发布实例都使用基于Oak的Sling发现服务放在松耦合的Toplogy中，并配置ActiveMQ，以便每个发布实例能够通信并创建一个消息队列。 Screens设备通过负载平衡器轮询发布群，并从队列顶部选取命令。

### 反向复制 {#reverse-replication}

在许多情况下，在执行命令后，Screens设备中应会有某种响应转发到作者实例。 为了实现此AEM反向复 ***制*** ，请使用。

* 为每个发布实例创建一个反向复制代理，类似于标准复制代理和屏幕复制代理。
* 工作流启动器配置监听在发布实例上修改的节点，然后触发将设备响应放入发布实例的发布框的工作流。
* 在此上下文中的反向复制仅用于设备提供的二进制数据（如日志文件和截屏）。 通过轮询检索非二进制数据。
* 从AEM作者实例反向轮询的复制将检索响应并将其保存到作者实例。

### 发布实例的轮询 {#polling-of-publish-instances}

创作实例需要能够轮询设备以获得心跳并了解已连接设备的运行状况。

设备ping负载平衡器并路由到发布实例。 随后，发布实例通过在所有活动设备上提供的@ **api/screens-dcc/devices/stati** ，以及单个设备上的 **api/screens-dcc/devices/&lt;device_id&gt;/status.json** ，公开设备状态。

作者实例将轮询所有发布实例，并将设备状态响应合并为单个状态。 对作者进行轮询的计划作 `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` 业是基于cron表达式进行配置的。

## 注册 {#registration}

注册会继续源自AEM作者实例。 AEM Screens设备指向创作实例，且注册已完成。

在创作环境中注册设备后，设备配置和渠道／计划分配将复制到AEM发布实例。 随后将更新AEM Screens设备配置，以指向AEM发布群前面的负载平衡器。 这是一次性设置，当Screens设备成功连接到发布环境后，它可以继续接收来自创作环境的命令，并且无需将Screens设备直接连接到创作环境。

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### 后续步骤 {#the-next-steps}

了解AEM Screens中作者和发布设置的架构设计后，请参阅为AEM Screens配 [置作者和发布](author-and-publish.md) ，以了解更多详细信息。
