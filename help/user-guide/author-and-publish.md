---
title: 在AEM Screens中配置“创作”和“发布”
description: AEM Screens架构类似于传统的AEM Sites架构。 内容在AEM创作实例上创作，然后转发到多个发布实例。 关注此页面，了解如何为AEM Screens配置创作和发布。
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: ab959584c01c10f76c231ab89b574886ad7346c5
workflow-type: tm+mt
source-wordcount: '1988'
ht-degree: 0%

---


# 在AEM Screens中配置“创作”和“发布” {#configuring-author-and-publish-in-aem-screens}

本页重点介绍以下主题：

* **配置作者和发布实例**
* **设置发布拓扑**
* **管理发布：将内容更新从作者发布到设备**

## 前提条件 {#prerequisites}

在开始使用创作和发布服务器之前，您应该事先了解以下知识：

* **AEM拓扑**
* **创建和管理AEM Screens项目**
* **设备注册流程**

>[!NOTE]
>
>此AEM Screens功能仅在安装了AEM 6.4 Screens Feature Pack 2时才可用。 要访问此功能包，您必须联系Adobe支持部门并请求获取访问权限。 一旦您拥有权限，就可以从包共享下载它。

>[!IMPORTANT]
>
>如果要对Dispatcher使用多个发布实例，则必须更新Dispatcher中的dispatcher.any文件。 参见 [启用粘性会话](dispatcher-configurations-aem-screens.md#enable-sticky-session) 了解更多详细信息。

## 配置作者和发布实例 {#configuring-author-and-publish-instances}

>[!NOTE]
>
>要了解有关创作和发布架构概述以及如何在AEM创作实例上创作内容然后将其转发到多个发布实例的更多信息，请参阅 [创作和发布架构概述](author-publish-architecture-overview.md).

以下部分介绍了如何在创作和发布拓扑上设置复制代理。

您可以设置一个简单示例，其中托管一个创作实例和两个发布实例：

* 作者 — > localhost：4502
* 发布1 (pub1) —> localhost：4503
* 发布2 (pub2) —> localhost：4504

## 在创作实例上设置复制代理 {#setting-replication-agents}

要创建复制代理，您必须了解如何创建标准复制代理。

Screens需要3个复制代理：

1. **默认复制代理 ***(指定为*** 标准复制代理**)
1. **Screens复制代理**
1. **反向复制代理**

### 步骤1：创建默认复制代理 {#step-creating-a-default-replication-agent}

请按照以下步骤创建默认复制代理：

1. 导航到您的AEM实例 — >锤子图标 — > **操作** —> **配置**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 选择 **复制** 从左侧导航树中。

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. 选择 **作者代理** 从 **复制** 文件夹并单击 **新** 创建新的标准复制代理。

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. 输入 **标题** 和 **名称** 要创建复制代理，请单击 **创建**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. 右键单击复制代理，然后单击 **打开** 以编辑设置。

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. 单击 **编辑** 以打开 **代理设置** 对话框输入详细信息。

   >[!NOTE]
   >
   >用户需要检查 **已启用** 启用复制代理。 必须在Default 、 Screens和Reverse Replication Agents上选中此选项。

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. 导航到 **传输** 选项卡，并输入 **URI**， **用户** 和 **密码**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >您还可以复制和重命名现有的默认复制代理。


#### 创建标准复制代理  {#creating-standard-replication-agents}

1. 为pub1创建标准复制代理（应已配置现成的默认代理）(例如， *https://&lt;hostname>：4503/bin/receive？sling：authRequestLogin=1*)
1. 为pub2创建标准复制代理。 您可以复制pub1的复制代理，并通过更改传输配置中的端口来更新要用于pub2的传输。 (例如， *https://&lt;hostname>：4504/bin/receive？sling：authRequestLogin=1*)

#### 创建Screens复制代理 {#creating-screens-replication-agents}

1. 为pub1创建screens复制代理。 开箱即用，有一个名为Screens的复制代理指向端口4503。 需要启用此功能。
1. 为pub2创建一个screens复制代理。 复制pub1的Screens复制代理，并将端口更改为pub2的4504。

   >[!NOTE]
   >要了解如何配置Screens复制代理，请参阅 [配置Screens复制代理](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/configure-screens-replication.html?lang=en).

#### 创建Screens反向复制代理 {#creating-screens-reverse-replication-agents}

1. 为pub1创建反向复制代理。
1. 为pub2创建反向复制代理。 您可以复制pub1的反向复制代理，并通过更改传输配置中的端口来更新要用于pub2的传输。

## 设置发布拓扑 {#setting-up-publish-topology}

### 步骤1：配置基于Oak的Apache Sling发现 {#step-configure-apache-sling-oak-based-discovery}

为拓扑中的所有发布实例设置基于Apache Sling Oak的发现

对于每个发布实例：

1. 导航至 `https://<host>:<port>/system/console/configMgr`
1. 选择 **基于Apache Sling Oak的发现服务** 配置。
1. 更新拓扑连接器URL：添加以下所有参与发布实例的URL：
   * `https://publish:4503/libs/sling/topology/connector`
   * `https://publish:4504/libs/sling/topology/connector`
1. **拓扑连接器白名单**：适应覆盖所有发布实例的IP或子网。 请确保将所有没有端口号的发布实例的IP/主机名列入白名单。

1. 启用 **自动停止本地环路**

每个发布实例的配置应该相同，并且自动停止本地循环可防止无限循环。

#### 步骤2：验证发布拓扑 {#step-verify-publish-topology}

对于任何发布实例，导航到 `https://:/system/console/topology`. 您应该会在下看到拓扑中表示的每个发布实例 **传出拓扑连接器**.

#### 步骤3：设置ActiveMQ Artemis群集 {#step-setup-activemq-artemis-cluster}

此步骤允许您为ActiveMQ Artemis群集创建加密密码。
拓扑中所有发布实例的群集用户和密码必须相同。 ActiveMQ Artemis配置的密码需要加密。 由于每个实例都有自己的加密密钥，因此有必要使用加密支持来创建加密的密码字符串。 然后，加密的密码将用于ActiveMQ的OSGi配置。

在每个发布实例上：

1. 在OSGi控制台中，导航到 **主要** —> **加密支持** (`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`)。
1. 在中键入所需的纯文本密码（所有实例均相同） **纯文本**
1. 单击 **Protect**.
1. 复制值 **受保护的文本** 记事本或文本编辑器。 此值将用于ActiveMQ的OSGi配置。

由于每个发布实例在默认情况下都有唯一的加密密钥，因此您需要在每个发布实例上执行此步骤，并保存唯一密钥以供下一个配置使用。

>[!NOTE]
>
>密码应该以大括号开始和结束。 例如：
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### 步骤4：激活ActiveMQ Artemis群集 {#step-activate-activemq-artemis-cluster}

在每个发布实例上：

1. 导航到OSGi配置管理器 `https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. 选择 **Apache ActiveMQ Artemis JMS提供程序** 配置
1. 更新以下内容：

   * ***群集密码***：对每个实例使用上一步中的加密值
   * ***主题***： `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### 验证ActiveMQ Artemis群集 {#verify-activemq-artemis-cluster}

在每个发布实例上执行以下步骤：

1. 导航到OSGi控制台 — >主页> ActiveMQ Artemis `https://localhost:4505/system/console/mq`.
1. 验证并检查以查看“Cluster Information”（群集信息）>“Topology”（拓扑）>“nodes”（节点）=2， members”（成员）=2下的其它实例的端口。
1. 发送测试消息（屏幕顶部“代理信息”下）
1. 在字段中输入以下更改：

   1. **目标**： /com.adobe.cq.screens/devTestTopic
   1. **文本**： Hello World
   1. 查看每个实例的error.log以查看消息是否在整个群集中发送和接收

>[!NOTE]
>
>导航到OSGi控制台可能需要几秒钟时间，才能在上一步中保存配置。 您还可以查看error.log以了解更多详细信息。

例如，成功配置ActiveMQ Artemis服务器时将显示以下图像。

如果您没有从看到以下配置 */system/console/mq*，然后导航到 */system/console/mq* 并单击 **重新启动** 以重新启动经纪人。

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### 删除反向链接标头要求 {#remove-referrer-header-requirement}

按照每个发布实例上的步骤操作：

1. 导航到 **OSGi控制台** > **配置管理器**
1. 选择 **Apache Sling引用过滤器**
1. 更新配置和 **选中允许为空**

### 配置创作和发布实例 {#configuring-author-and-publish-instance}

设置发布拓扑后，您需要配置创作实例和发布实例，以查看实施的实际结果：

>[!NOTE]
>
>**前提条件**
>
>要开始使用此示例，请创建一个新的AEM Screens项目，然后在您的项目中创建位置、显示和渠道。 向渠道添加内容并分配渠道以显示内容。

#### 步骤1：启动AEM Screens Player（设备） {#step-starting-an-aem-screens-player-device}

1. 启动单独的浏览器窗口。
1. 使用转到Screens播放器 *Web浏览器*，即，`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` 或启动AEM Screens应用程序。 打开设备时，您会注意到该设备的状态为未注册。

>[!NOTE]
>
>您可以使用下载的AEM Screens应用程序或Web浏览器打开AEM Screens播放器。

#### 步骤2：在创作实例上注册设备 {#step-registering-a-device-on-author}

1. 转到 `https://localhost:4502/screens.html/content/screens/we-retail` 或选择您的项目，然后导航到“设备”>“设备管理器”。
1. 选择 **注册设备**.
1. 单击 **设备注册** 查看设备。
1. 选择要注册的设备，然后单击 **注册设备**.
1. 验证注册码并单击 **验证**.
1. 输入设备的标题，然后单击 **注册**.

#### 步骤3：指定要显示的设备 {#step-assigning-the-device-to-display}

1. 单击 **分配显示区** 从上一步骤的对话框中。
1. 从中选择渠道的显示路径 **位置** 文件夹。
1. 单击 **分配**.
1. 单击 **完成** 以完成该过程，现在已分配设备。

查看您的播放器，您将看到在渠道中添加的内容。

#### 步骤4：将设备配置发布到发布实例 {#step-publishing-device-configuration-to-publish-instances}

**验证设备**

按照以下步骤复制设备用户：

1. 导航到用户管理页面(例如： `https://localhost:4502/useradmin`
1. 搜索 **screens-devices-主控** 群组
1. 右键单击该组，然后单击 **激活**

>[!CAUTION]
>
>请勿激活author-publish-screens-service，因为它是作者作业使用的系统用户。

您还可以从设备管理控制台激活该设备。 应遵循以下步骤：

1. 导航到屏幕项目 — > **设备**.
1. 单击 **设备管理器** 操作栏中的。
1. 选择设备并单击 **激活** 从操作栏中，如下图所示。

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>或者，在激活设备后，您还可以通过单击来编辑或更新服务器URL **编辑服务器URL** ，如下图所示，并且您的更改将传播到AEM Screens播放器。

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### 发布检查列表 {#publishing-check-list}

以下几点总结了Publishing Check列表：

* *屏幕设备用户*  — 将其存储为AEM用户，并从以下位置激活： **工具** > **安全性** > **用户**. 该用户将使用长序列化字符串作为前缀“screens”。

* *项目* - AEM Screens项目。
* *位置*  — 设备连接到的位置。
* *渠道*  — 该位置显示的一个或多个渠道
* *计划*  — 如果使用计划，请确保已发布计划
* *位置、计划和渠道文件夹*  — 如果相应的资源位于文件夹中。

执行以下步骤以验证创作/发布行为：

1. 在创作实例上更新某些渠道内容
1. 执行 **管理发布** 将新更改发布到所有发布实例
1. 按 **激活** 以激活设备 **设备管理器**
1. **编辑URL** 从创作实例URL到其中一个发布实例URL
1. 验证更新的渠道内容是否显示在AEM Screens播放器上
1. 使用其他发布实例重复这些步骤


#### 步骤5：在“管理”面板中将设备指向发布实例 {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. 从Screens播放器查看管理UI，长按左上角的以打开“管理”菜单，也可以在支持触摸的AEM Screens播放器上或者使用鼠标来打开。
1. 单击 **配置** 选项。
1. 在中将创作实例更改为发布实例 **服务器**.

在AEM Screens播放器中查看更改。

或者，您还可以使用以下步骤从设备管理控制台更新/编辑服务器URL：

1. 导航到您的AEM Screens项目，然后选择 **设备** 文件夹。
1. 单击 **设备管理器** 操作栏中的。
1. 选择设备并单击 **编辑服务器URL** ，如下图所示，并且您的更改将传播到AEM Screens播放器。

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

此 **管理发布** 利用功能，可将内容更新从作者发布到设备。 您可以为整个AEM Screens项目或仅为渠道、位置、设备、应用程序或计划之一发布/取消发布内容。 要了解有关此功能的更多信息，请参阅 [按需内容更新](on-demand-content.md).

## 疑难解答提示 {#troubleshoot-tips}

请阅读以下章节，以获取与创作/发布设置相关的常见问题解答。

### 如何在初始注册和分配后添加从https到http的重定向？ {#add-redirect}

**解决方案**
设置启用 `Proxy/Load Balancer Connection in the Jetty configuration` 到 `true`.

### 如何更新离线内容和播放器下载问题与外部资源有关 `/content/dam/projects/<project>`？ {#update-offline-content}

**解决方案**
为所有bulk-offline-update-screens-service用户和screens-devices-主控组授予读取权限 `/content/dam` 或您希望使用的特定资源（如果您希望使用更严格的限制）。

### 如何解决Screens复制代理错误？ {#replication-agent}

**解决方案**
确保未在代理配置中选中使用反向复制选项。 Screens复制代理不能用作反向复制代理，此功能的作用范围是将设备命令从创作转发到发布。