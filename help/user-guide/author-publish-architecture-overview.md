---
title: 作者和Publish架构概述
description: AEM Screens架构与传统AEM Sites架构类似。 内容是在AEM创作实例上创作的，然后转发到多个发布实例。
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---

# 作者和Publish架构概述 {#author-and-publish-architectural-overview}

本页重点介绍以下主题：

* **Publish服务器简介**
* **架构概述**
* **注册流程**

## 先决条件 {#prerequisites}

在开始使用创作服务器和发布服务器之前，您应该事先了解以下知识：

* **AEM拓扑**
* **创建和管理AEM Screens项目**
* **设备注册流程**

>[!NOTE]
>
>此AEM Screens功能仅在安装了AEM 6.4 Screens Feature Pack 2时才可用。 要访问此功能包，请联系Adobe支持并请求获取访问权限。 获得权限后，从包共享下载。

## 简介 {#introduction}

AEM Screens架构与传统AEM Sites架构类似。 内容是在AEM创作实例上创作的，然后转发到多个发布实例。 AEM Screens上的设备现在可以通过负载平衡器连接到AEM发布场。 可以添加多个AEM发布实例以继续扩展发布场。

*例如*，AEM Screens内容作者在创作系统上为特定设备发出命令。 该设备配置为与发布场交互。 或者，与AEM Screens内容作者交互，该作者将获取有关配置为与发布场交互的设备的信息。

下图说明了创作环境和发布环境。

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## 架构设计 {#architectural-design}

有五个体系结构组件有助于此解决方案：

* ***正在将内容***&#x200B;从作者复制到发布以供设备显示

* ***反向***&#x200B;将二进制内容从发布环境（从设备接收）复制到创作环境。
* ***正在从作者发送***&#x200B;命令，以通过特定的REST API进行发布。
* 在发布实例之间发送&#x200B;***消息***&#x200B;以同步设备信息更新和命令。
* 发布实例的作者&#x200B;***轮询***&#x200B;以通过特定REST API获取设备信息。

### 内容和配置的复制（转发） {#replication-forward-of-content-and-configurations}

标准复制代理用于复制AEM Screens渠道内容、位置配置和设备配置。 此功能允许作者更新渠道的内容，并在发布渠道更新之前，根据需要完成某种审批工作流。 必须为发布场中的每个发布实例创建复制代理。

下图说明了复制过程：

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>必须为发布场中的每个发布实例创建复制代理。

### Screens复制代理和命令 {#screens-replication-agents-and-commands}

可创建自定义Screens特定的复制代理，以将命令从Author实例发送到AEM Screens设备。 AEM Publish实例充当将这些命令转发到设备的中介。

利用此工作流，作者可以继续管理设备，例如，发送设备更新并从创作环境拍摄屏幕快照。 AEM Screens复制代理具有自定义传输配置，如标准复制代理。

### Publish实例之间的消息传递 {#messaging-between-publish-instances}

通常，命令只用于向设备发送一次。 但是，在负载平衡的发布架构中，设备所连接的发布实例未知。

因此，创作实例会将消息发送到所有Publish实例。 但是，只应将单个消息中继到设备。 为确保消息传递正确，发布实例之间必须通信。 此通信是使用&#x200B;*Apache ActiveMQ Artemis*&#x200B;实现的。 使用基于Oak的Sling发现服务，将每个发布实例放置在松耦合的拓扑中。 ActiveMQ已配置为每个发布实例都可以通信并创建单个消息队列。 AEM Screens设备通过负载平衡器轮询AEM发布场，并从队列顶部选取命令。

### 撤消复制 {#reverse-replication}

通常，在命令之后，Screens设备中的某种响应会转发到创作实例。 要实现此AEM ***使用反向复制***。

* 为每个发布实例创建反向复制代理，与标准复制代理和AEM Screens复制代理类似。
* 工作流启动器配置会侦听在AEM发布实例上修改的节点，然后触发工作流以将设备的响应放入AEM发布实例的发件箱中。
* 此上下文中的反向复制仅用于设备提供的二进制数据（例如日志文件和屏幕截图）。 检索非二进制数据的轮询。
* 从AEM创作实例反向复制轮询可检索响应并将其保存到创作实例。

### 轮询Publish实例 {#polling-of-publish-instances}

创作实例必须能够轮询设备以获取心率并了解已连接设备的运行状况。

设备ping负载平衡器并路由到发布实例。 随后，AEM发布实例通过为所有活动设备提供的@ **api/screens-dcc/devices/static**&#x200B;和用于单个设备的&#x200B;**api/screens-dcc/devices/&lt;device_id>/status.json**&#x200B;提供的Publish API公开设备的状态。

创作实例可轮询所有发布实例，并将设备状态响应合并为单个状态。 轮询作者的计划作业为`com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob`，可以基于cron表达式进行配置。

## 注册 {#registration}

注册仍源于AEM创作实例。 AEM Screens设备指向创作实例并完成注册。

在AEM创作环境中注册设备后，设备配置和渠道/计划分配将复制到AEM发布实例。 AEM Screens设备配置随后将更新，以指向AEM发布场前面的负载平衡器。 此安排旨在进行一次性设置。 成功将Screens设备连接到发布环境后，该设备可以继续接收来自创作环境的命令。 无需直接将AEM Screens设备连接到AEM创作环境。

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### 后续步骤 {#the-next-steps}

当您了解AEM Screens中创作和发布设置的架构设计时，请参阅[为AEM Screens配置创作和Publish](author-and-publish.md)以了解更多详细信息。
