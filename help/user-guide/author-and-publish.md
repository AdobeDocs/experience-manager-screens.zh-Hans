---
title: 在AEM Screens中配置创作和发布
description: AEM Screens架构类似于传统的AEM Sites架构。 在AEM创作实例上创作内容，然后将其转发复制到多个发布实例。 可查看本页以了解如何为AEM Screens配置创作和发布。
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: ab959584c01c10f76c231ab89b574886ad7346c5
workflow-type: tm+mt
source-wordcount: '1988'
ht-degree: 2%

---


# 在AEM Screens中配置创作和发布 {#configuring-author-and-publish-in-aem-screens}

本页重点介绍以下主题：

* **配置创作实例和发布实例**
* **设置发布拓扑**
* **管理发布：将内容更新从创作交付到发布到设备**

## 前提条件 {#prerequisites}

在开始使用创作和发布服务器之前，您应该事先了解：

* **AEM拓扑**
* **创建和管理AEM Screens项目**
* **设备注册过程**

>[!NOTE]
>
>仅当您安装了AEM 6.4 Screens功能包2时，才提供此AEM Screens功能。 要获取此功能包，您必须联系 Adobe 支持人员并申请访问权限。您获得权限后，就可以从“包共享”下载它。

>[!IMPORTANT]
>
>如果要与Dispatcher一起使用多个发布实例，则必须更新Dispatcher中的dispatcher.any文件。 请参阅 [启用置顶会话](dispatcher-configurations-aem-screens.md#enable-sticky-session) 以了解更多详细信息。

## 配置创作实例和发布实例 {#configuring-author-and-publish-instances}

>[!NOTE]
>
>要进一步了解作者和发布架构概述，以及如何在AEM创作实例上创作内容，然后将其转发复制到多个发布实例，请参阅 [创作和发布架构概述](author-publish-architecture-overview.md).

以下部分介绍如何在创作拓扑和发布拓扑上设置复制代理。

您可以设置一个简单的示例，其中托管一个作者和两个发布实例：

* 作者 — > localhost:4502
* 发布1(pub1)—> localhost:4503
* 发布2(pub2)—> localhost:4504

## 在作者上设置复制代理 {#setting-replication-agents}

要创建复制代理，您必须了解如何创建标准的复制代理。

Screens需要3个复制代理：

1. **默认复制代理 ***(指定为*** 标准复制代理**)
1. **Screens复制代理**
1. **反向复制代理**

### 步骤1:创建默认复制代理 {#step-creating-a-default-replication-agent}

按照以下步骤创建默认复制代理：

1. 导航到AEM实例 — >锤子图标 — > **操作** —> **配置**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 选择 **复制** 从左侧导航树中。

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. 选择 **作者代理** 从 **复制** 文件夹，单击 **新建** 创建新的标准复制代理。

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. 输入 **标题** 和 **名称** 要创建复制代理，请单击 **创建**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. 右键单击复制代理，然后单击 **打开** 以编辑设置。

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. 单击 **编辑** 打开 **代理设置** 对话框以输入详细信息。

   >[!NOTE]
   >
   >用户需要检查 **已启用** 启用复制代理。 您必须在默认、屏幕和反向复制代理中选中此选项。

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. 导航到 **运输** ，然后输入 **URI**, **用户** 和 **密码**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >您还可以复制和重命名现有的默认复制代理。


#### 创建标准复制代理  {#creating-standard-replication-agents}

1. 为pub1创建标准复制代理（应已配置现成的默认代理）(例如， *https://&lt;hostname>:4503/bin/receive?sling:authRequestLogin=1*)
1. 为pub2创建标准复制代理。 您可以复制pub1的复制代理，并通过更改传输配置中的端口来更新要用于pub2的传输。 (例如， *https://&lt;hostname>:4504/bin/receive?sling:authRequestLogin=1*)

#### 创建Screens复制代理 {#creating-screens-replication-agents}

1. 为pub1创建屏幕复制代理。 现成，有一个名为Screens复制代理的端口指向4503。 需要启用此功能。
1. 为pub2创建屏幕复制代理。 复制pub1的Screens复制代理，并将pub2的端口更改为4504。

   >[!NOTE]
   >要了解如何配置Screens复制代理，请参阅 [配置Screens复制代理](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/configure-screens-replication.html?lang=en).

#### 创建Screens反向复制代理 {#creating-screens-reverse-replication-agents}

1. 为pub1创建反向复制代理。
1. 为pub2创建反向复制代理。 您可以复制pub1的反向复制代理，并通过更改传输配置中的端口来更新要用于pub2的传输。

## 设置发布拓扑 {#setting-up-publish-topology}

### 步骤1:配置Apache Sling Oak-Based Discovery {#step-configure-apache-sling-oak-based-discovery}

为拓扑中的所有Publish实例设置Apache Sling Oak-Based Discovery

对于每个发布实例：

1. 导航至 `https://<host>:<port>/system/console/configMgr`
1. 选择 **Apache Sling Oak-Based Discovery Service** 配置。
1. 更新拓扑连接器URL:添加所有参与的发布实例的URL，这些实例为：
   * `https://publish:4503/libs/sling/topology/connector`
   * `https://publish:4504/libs/sling/topology/connector`
1. **拓扑连接器白名单**:适应涵盖所有发布实例的IP或子网。 确保将所有发布实例的IP/主机名列入白名单，但不带端口号。

1. 启用 **自动停止局部循环**

每个发布实例的配置应相同，并且自动停止本地循环可防止无限循环。

#### 步骤2:验证发布拓扑 {#step-verify-publish-topology}

对于任何发布实例，导航到 `https://:/system/console/topology`. 您应会在 **传出拓扑连接器**.

#### 步骤3:设置ActiveMQ Artemis群集 {#step-setup-activemq-artemis-cluster}

此步骤允许您为ActiveMQ Artemis群集创建加密密码。
拓扑中所有发布实例的群集用户和密码必须相同。 需要加密ActiveMQ Artemis配置的密码。 由于每个实例都有其自己的加密密钥，因此必须使用加密支持来创建加密的密码字符串。 然后，在ActiveMQ的OSGi配置中使用加密的密码。

在每个发布实例上：

1. 在OSGi控制台中，导航到 **主要** —> **加密支持** (`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`)。
1. 在 **纯文本**
1. 单击 **Protect**.
1. 复制值 **受保护文本** 到记事本或文本编辑器。 此值将用在ActiveMQ的OSGi配置中。

由于每个发布实例默认具有唯一的加密密钥，因此您需要对每个发布实例执行此步骤，并保存唯一密钥以进行下一次配置。

>[!NOTE]
>
>密码应以大括号开始和结束。 例如：
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### 步骤4:激活ActiveMQ Artemis群集 {#step-activate-activemq-artemis-cluster}

在每个发布实例上：

1. 导航到OSGi配置管理器 `https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. 选择 **Apache ActiveMQ目标JMS提供程序** 配置
1. 更新以下内容：

   * ***群集密码***:对每个实例使用上一步中的加密值
   * ***主题***: `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### 验证ActiveMQ Artemis群集 {#verify-activemq-artemis-cluster}

对每个Publish实例执行以下步骤：

1. 导航到OSGi控制台 — >主> ActiveMQ Artemis `https://localhost:4505/system/console/mq`.
1. 验证并检查群集信息>拓扑>节点=2，成员=2下的其他实例的端口。
1. 发送测试消息(屏幕顶部的“Broker Information（代理信息）”下)
1. 在字段中输入以下更改：

   1. **目标**:/com.adobe.cq.screens/devTestTopic
   1. **文本**:《你好世界》
   1. 查看每个实例的error.log ，以查看消息是否在群集中发送和接收

>[!NOTE]
>
>在上一步中保存配置后，导航到OSGi控制台可能需要几秒钟的时间。 您还可以查看error.log ，了解更多详细信息。

例如，在成功配置ActiveMQ Artemis Server时，会显示以下图像。

如果您在 */system/console/mq*，然后导航到 */system/console/mq* 单击 **重新启动** 以重新启动代理。

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### 删除反向链接标题要求 {#remove-referrer-header-requirement}

按照每个Publish实例上的步骤操作：

1. 导航到 **OSGi控制台** > **配置管理器**
1. 选择 **Apache Sling反向链接过滤器**
1. 更新配置和 **选中允许为空**

### 配置创作和发布实例 {#configuring-author-and-publish-instance}

设置发布拓扑后，您需要配置创作实例和发布实例，以查看实施的实际结果：

>[!NOTE]
>
>**前提条件**
>
>要开始使用此示例，请新建一个AEM Screens项目，然后在项目中创建位置、显示屏和渠道。 向渠道添加内容并将渠道分配给显示屏。

#### 步骤1:启动AEM Screens播放器（设备） {#step-starting-an-aem-screens-player-device}

1. 启动一个单独的浏览器窗口。
1. 使用 *Web浏览器*，即`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` 或启动AEM Screens应用程序。 在打开设备时，您会注意到设备的状态为未注册。

>[!NOTE]
>
>您可以使用您下载的AEM Screens应用程序或使用Web浏览器打开AEM Screens播放器。

#### 步骤2:在创作中注册设备 {#step-registering-a-device-on-author}

1. 转到 `https://localhost:4502/screens.html/content/screens/we-retail` 或选择您的项目，然后导航到“设备”>“设备管理器”。
1. 选择 **注册设备**.
1. 单击 **设备注册** 查看设备。
1. 选择要注册的设备，然后单击 **注册设备**.
1. 验证注册代码并单击 **验证**.
1. 输入设备的标题并单击 **注册**.

#### 步骤3:将设备分配给显示器 {#step-assigning-the-device-to-display}

1. 单击 **分配显示** 中，将其排除在以下位置。
1. 从 **位置** 文件夹。
1. 单击 **分配**.
1. 单击 **完成** 完成该过程，现在已分配设备。

查看您的播放器，您将看到您在渠道中添加的内容。

#### 步骤4:将设备配置发布到发布实例 {#step-publishing-device-configuration-to-publish-instances}

**验证设备**

按照以下步骤复制设备用户：

1. 导航到用户管理页面(例如： `https://localhost:4502/useradmin`
1. 搜索 **screens-devices-主控** 群组
1. 右键单击群组，然后单击 **激活**

>[!CAUTION]
>
>请勿激活author-publish-screens-service，因为它是创作作业使用的系统用户。

您还可以从设备管理控制台激活设备。 应遵循以下步骤：

1. 导航到您的Screens项目 — > **设备**.
1. 单击 **设备管理器** 中。
1. 选择设备并单击 **激活** ，如下图所示。

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>或者，激活设备后，您还可以通过单击 **编辑服务器URL** ，如下图所示，您所做的更改将会传播到AEM Screens播放器。

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### 发布检查列表 {#publishing-check-list}

以下几点汇总了“发布检查”列表：

* *Screens设备用户*  — 此ID将存储为AEM用户，并从 **工具** > **安全性** > **用户**. 用户将带有带有长序列化字符串的“screens”前缀。

* *项目* -AEM Screens项目。
* *位置*  — 设备连接到的位置。
* *渠道*  — 在位置显示的一个或多个渠道
* *计划*  — 如果使用计划，请确保已发布
* *位置、计划和渠道文件夹*  — 如果相应的资源位于文件夹中。

请按照以下步骤验证作者/发布行为：

1. 在创作实例上更新一些渠道内容
1. 执行 **管理发布** 发布对所有发布实例的新更改
1. 按 **激活** 从激活设备 **设备管理器**
1. **编辑URL** 从创作实例URL到其中一个发布实例URL
1. 验证更新的渠道内容是否显示在AEM Screens播放器上
1. 使用其他发布实例重复这些步骤


#### 步骤5:在“管理面板”中将设备指向发布实例 {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. 从Screens播放器中查看管理员UI，长按左上角以打开“管理员”菜单、触屏AEM Screens播放器，或使用鼠标。
1. 单击 **配置** 选项。
1. 将创作实例更改为在中发布实例 **服务器**.

查看AEM Screens播放器中的更改。

或者，您也可以通过设备管理控制台通过以下步骤更新/编辑服务器URL:

1. 导航到您的AEM Screens项目，然后选择 **设备** 文件夹。
1. 单击 **设备管理器** 中。
1. 选择设备并单击 **编辑服务器URL** ，如下图所示，您所做的更改将会传播到AEM Screens播放器。

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

的 **管理发布** 功能允许您将内容更新从创作交付到发布到设备。 您可以发布/取消发布整个AEM Screens项目的内容，也只能发布/取消发布渠道、位置、设备、应用程序或计划中的一个内容。 要了解有关此功能的更多信息，请参阅 [按需内容更新](on-demand-content.md).

## 疑难解答提示 {#troubleshoot-tips}

请按照以下部分获取与创作/发布设置相关的常见问题解答。

### 如何在初始注册和分配后将重定向从https添加到http ? {#add-redirect}

**解决方案**
设置启用 `Proxy/Load Balancer Connection in the Jetty configuration` to `true`.

### 如何更新外部资产的离线内容和播放器下载问题 `/content/dam/projects/<project>`? {#update-offline-content}

**解决方案**
为批量脱机更新屏幕服务用户和屏幕设备主控组授予读取权限，以便所有用户 `/content/dam` 或者，如果您希望对资产设置更多限制，也可以选择要使用的特定资产。

### 如何解决Screens复制代理错误？ {#replication-agent}

**解决方案**
请确保您未在代理配置中选中使用进行反向复制选项。 Screens复制代理不能用作反向复制代理，此功能的范围是将设备命令从创作转发到发布。