---
title: 创作和发布架构概述
description: AEM Screens架构类似于传统的AEM Sites架构。 内容是在AEM创作实例上创作的，然后转发到多个发布实例。
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '976'
ht-degree: 0%

---

# 创作和发布架构概述 {#author-and-publish-architectural-overview}

本页重点介绍以下主题：

* **发布服务器简介**
* **架构概述**
* **注册流程**

## 先决条件 {#prerequisites}

在开始使用创作服务器和发布服务器之前，您应该事先了解以下知识：

* **AEM拓扑**
* **创建和管理AEM Screens项目**
* **设备注册流程**

>[!NOTE]
>
>此AEM Screens功能仅在您安装了AEM 6.4 Screens Feature Pack 2时才可用。 要访问此功能包，请联系Adobe支持并请求获取访问权限。 获得权限后，从包共享下载。

## 简介 {#introduction}

AEM Screens架构类似于传统的AEM Sites架构。 内容是在AEM创作实例上创作的，然后转发到多个发布实例。 AEM Screens上的设备现在可以通过负载平衡器连接到AEM发布场。 可以添加多个AEM发布实例以继续扩展发布场。

*例如*，AEM Screens内容作者将在创作系统上为特定设备发出命令。 该设备配置为与发布场或AEM Screens内容作者交互，后者获取有关配置为与发布场交互的设备的信息。

下图说明了创作环境和发布环境。

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## 架构设计 {#architectural-design}

有五个体系结构组件有助于此解决方案：

* ***复制内容*** 从创作到发布以供设备显示

* ***反向*** 将二进制内容从发布环境（从设备接收）复制到创作环境。
* ***正在发送*** 通过特定的REST API从作者到发布的命令。
* ***消息传送*** 在发布实例之间同步设备信息更新和命令。
* ***轮询*** 发布实例的作者，通过特定REST API获取设备信息。

### 内容和配置的复制（转发）  {#replication-forward-of-content-and-configurations}

标准复制代理用于复制AEM Screens渠道内容、位置配置和设备配置。 这允许作者更新渠道的内容，并在发布渠道更新之前选择性地完成某种审批工作流。 必须为发布场中的每个发布实例创建复制代理。

下图说明了复制过程：

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>必须为发布场中的每个发布实例创建复制代理。

### Screens复制代理和命令  {#screens-replication-agents-and-commands}

可创建自定义Screens特定的复制代理，以将命令从Author实例发送到AEM Screens设备。 AEM Publish实例用作将这些命令转发到设备的中介程序。

这允许作者继续管理设备，例如，发送设备更新并从创作环境中拍摄屏幕快照。 AEM Screens复制代理具有自定义传输配置，如标准复制代理。

### 发布实例之间的消息传递  {#messaging-between-publish-instances}

通常，命令只用于向设备发送一次。 但是，在负载平衡的发布架构中，未知设备连接到哪个发布实例。

因此，创作实例会将消息发送到所有发布实例。 但是，只应将单个消息中继到设备。 为确保消息传递正确，发布实例之间必须通信。 这是通过使用以下方式实现的 *Apache ActiveMQ Artemis*. 使用基于Oak的Sling发现服务将每个发布实例放置在松散耦合的拓扑中，并配置ActiveMQ以便每个发布实例可以通信并创建单个消息队列。 AEM Screens设备通过负载平衡器轮询AEM发布场，并从队列顶部选取命令。

### 撤消复制 {#reverse-replication}

通常，在命令之后，Screens设备中的某种响应会转发到创作实例。 要实现此AEM ***反向复制*** 已使用。

* 为每个发布实例创建反向复制代理，与标准复制代理和AEM Screens复制代理类似。
* 工作流启动器配置会侦听在AEM发布实例上修改的节点，然后触发工作流以将设备的响应放入AEM发布实例的发件箱中。
* 此上下文中的反向复制仅用于设备提供的二进制数据（例如，日志文件和屏幕截图）。 通过轮询检索非二进制数据。
* 从AEM创作实例反向复制轮询可检索响应并将其保存到创作实例。

### 轮询发布实例  {#polling-of-publish-instances}

创作实例必须能够轮询设备以获取心率并了解已连接设备的运行状况。

设备ping负载平衡器并路由到发布实例。 然后，AEM发布实例通过提供的发布API公开设备的状态。 **api/screens-dcc/devices/static** 所有活动设备和 **api/screens-dcc/devices/&lt;device_id>/status.json** 用于单个设备。

创作实例可轮询所有发布实例，并将设备状态响应合并为单个状态。 轮询作者的计划作业为 `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` 并且可以基于cron表达式进行配置。

## 注册 {#registration}

注册仍源于AEM创作实例。 AEM Screens Device指向创作实例并完成注册。

在AEM创作环境中注册设备后，设备配置和渠道/计划分配将复制到AEM发布实例。 AEM Screens设备配置随后将更新，以指向AEM发布场前的负载平衡器。 此为一次性设置。 成功将Screens设备连接到发布环境后，它可以继续接收来自创作环境的命令。 无需直接将AEM Screens设备连接到AEM创作环境。

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### 后续步骤 {#the-next-steps}

当您了解AEM Screens中创作和发布设置的架构设计时，请参阅 [为AEM Screens配置创作和发布](author-and-publish.md) 以了解更多详细信息。
