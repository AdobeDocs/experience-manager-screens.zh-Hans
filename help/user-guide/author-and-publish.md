---
title: 在AEM Screens中配置作者和发布
seo-title: 在AEM Screens中配置作者和发布
description: AEM Screens架构类似于传统的AEM Sites架构。 内容是在AEM作者实例上创作的，然后转发复制到多个发布实例。 可查看本页以了解如何为AEM Screens配置作者和发布。
seo-description: AEM Screens架构类似于传统的AEM Sites架构。 内容是在AEM作者实例上创作的，然后转发复制到多个发布实例。 可查看本页以了解如何为AEM Screens配置作者和发布。
feature: 管理屏幕
role: 管理员、开发人员
level: 中间
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1910'
ht-degree: 2%

---


# 在AEM Screens{#configuring-author-and-publish-in-aem-screens}中配置作者和发布

本页重点介绍以下主题：

* **配置作者实例和发布实例**
* **设置发布拓扑**
* **管理发布：将内容更新从创作交付到发布到设备**

## 前提条件 {#prerequisites}

在开始使用作者服务器和发布服务器之前，您应事先了解：

* **AEM拓扑**
* **创建和管理AEM Screens项目**
* **设备注册过程**

>[!NOTE]
>
>此AEM Screens功能仅在您安装了AEM 6.4 Screens功能包2时可用。 要获取此功能包，您必须联系 Adobe 支持人员并申请访问权限。您获得权限后，就可以从“包共享”下载它。

>[!IMPORTANT]
>
>如果要与调度程序一起使用多个发布实例，则必须更新调度程序中的dispatcher.any文件。 有关详细信息，请参阅[启用粘性会话](dispatcher-configurations-aem-screens.md#enable-sticky-session)。

## 配置作者实例和发布实例{#configuring-author-and-publish-instances}

>[!NOTE]
>
>要进一步了解作者和发布体系结构概述，以及如何在AEM作者实例上创作内容，然后将内容转发复制到多个发布实例，请参阅[创作和发布体系结构概述](author-publish-architecture-overview.md)。

以下部分介绍如何在创作和发布拓扑上设置复制代理。

您可以设置一个简单的示例，其中您托管一个作者实例和两个发布实例：

* 作者 — > localhost:4502
* 发布1(pub1)—> localhost:4503
* 发布2(pub2)—> localhost:4504

## 在作者{#setting-replication-agents}上设置复制代理

要创建复制代理，您必须学习如何创建标准复制代理。

有3个复制代理是Screens所需的：

1. **默认复制代 ***理(指*** 定为标准复制代理**)
1. **Screens复制代理**
1. **反向复制代理**

### 第1步：创建默认复制代理{#step-creating-a-default-replication-agent}

请按照以下步骤创建默认复制代理：

1. 导航到AEM实例 — >锤子图标 — > **Operations** —> **Configuration**。

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 从左侧导航树中选择&#x200B;**复制**。

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. 从&#x200B;**Replication**&#x200B;文件夹中选择&#x200B;**作者**&#x200B;上的代理，然后单击&#x200B;**新建**&#x200B;以创建新的标准复制代理。

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. 输入&#x200B;**标题**&#x200B;和&#x200B;**名称**&#x200B;以创建复制代理，然后单击&#x200B;**创建**。

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. 右键单击复制代理，然后单击&#x200B;**打开**&#x200B;以编辑设置。

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. 单击&#x200B;**编辑**&#x200B;以打开&#x200B;**代理设置**&#x200B;对话框以输入详细信息。

   >[!NOTE]
   >
   >用户需要检查&#x200B;**已启用**&#x200B;以启用复制代理。 必须在“默认”、“屏幕”和“反向复制代理”上选中此选项。

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. 导航到&#x200B;**传输**&#x200B;选项卡并输入&#x200B;**URI**、**用户**&#x200B;和&#x200B;**密码**。

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >您还可以复制和重命名现有的默认复制代理。


#### 创建标准复制代理{#creating-standard-replication-agents}

1. 为pub1创建标准复制代理（应已配置现成默认代理）(例如，*https://&lt;hostname>:4503/bin/receive?sling:authRequestLogin=1*)
1. 为pub2创建标准复制代理。 您可以复制pub1的rep代理，并通过更改传输配置中的端口来更新要用于pub2的传输。 (例如，*https://&lt;hostname>:4504/bin/receive?sling:authRequestLogin=1*)

#### 创建Screens复制代理{#creating-screens-replication-agents}

1. 为pub1创建AEM Screens复制代理。 开箱即用，有一个名为Screens Replication Agent的代理，它指向端口4503。 需要启用此功能。
1. 为pub2创建AEM Screens复制代理。 复制pub1的Screens复制代理，并将pub2的端口更改为4504。

#### 创建Screens反向复制代理{#creating-screens-reverse-replication-agents}

1. 为pub1创建标准反向复制代理。
1. 为pub2创建标准反向复制代理。 您可以复制pub1的反向rep代理，并通过更改传输配置中的端口来更新要用于pub2的传输。

## 设置发布拓扑{#setting-up-publish-topology}

### 第1步：配置Apache Sling Oak-Based Discovery {#step-configure-apache-sling-oak-based-discovery}

为拓扑中的所有Publish实例设置Apache Sling Oak基于Discovery

对于每个发布实例：

1. 导航至 `https://<host>:<port>/system/console/configMgr`
1. 选择“**Apache Sling Oak-Based Discovery Service**&#x200B;配置”。
1. 更新拓扑连接器URL:添加以下所有参与发布实例的URL:
   * `https://localhost:4503/libs/sling/topology/connector`
   * `https://localhost:4504/libs/sling/topology/connector`
1. **拓扑连接器白名单列表**:适应包含参与发布实例的IP或子网
1. 启用&#x200B;**自动停止本地循环**

每个发布实例的配置应相同，自动停止本地循环可防止无限循环。

#### 第2步：验证发布拓扑{#step-verify-publish-topology}

对于任何发布实例，导航到`https://:/system/console/topology`。 应在&#x200B;**传出拓扑连接器**&#x200B;下看到拓扑中表示的每个发布实例。

#### 第3步：设置ActiveMQ Artemis群集{#step-setup-activemq-artemis-cluster}

此步骤允许您为ActiveMQ Artemis群集创建加密密码。
拓扑中所有发布实例的群集用户和口令必须相同。 需要加密ActiveMQ Artemis配置的密码。 由于每个实例都有其自己的加密密钥，因此必须使用加密支持创建加密的密码字符串。 然后，加密密码将用于ActiveMQ的OSGi配置。

在每个Publish实例上：

1. 在OSGi控制台中，导航到&#x200B;**MAIN** —> **Crypto Support**(`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`)。
1. 在&#x200B;**纯文本**&#x200B;中键入所需的纯文本密码（对于所有实例都相同）
1. 单击&#x200B;**Protect**。
1. 将值&#x200B;**受保护文本**&#x200B;复制到记事本或文本编辑器。 此值将用于ActiveMQ的OSGi配置。

由于默认情况下，每个发布实例都具有唯一的加密密钥，因此您需要对每个发布实例执行此步骤，并保存下一配置的唯一密钥。

>[!NOTE]
>
>密码应开始并以大括号结尾。 例如：
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### 第4步：激活ActiveMQ Artemis群集{#step-activate-activemq-artemis-cluster}

在每个发布实例上：

1. 导航到OSGi配置管理器`https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. 选择&#x200B;**Apache ActiveMQ Artemis JMS Provider**&#x200B;配置
1. 更新以下内容：

   * ***群集密码***:根据每个实例使用上一步中的加密值
   * ***主题***:  `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### 验证ActiveMQ Artemis群集{#verify-activemq-artemis-cluster}

对每个Publish实例执行以下步骤：

1. 导航到OSGi控制台 — >主> ActiveMQ Artemis `https://localhost:4505/system/console/mq`。
1. 验证并检查以视图群集信息>拓扑>节点=2，成员=2下其他实例的端口。
1. 发送测试消息（屏幕顶部的“Broker Information”下）
1. 在字段中输入以下更改：

   1. **目标**:/com.adobe.cq.screens/devTestTopic
   1. **文本**:《你好世界》
   1. 视图每个实例的error.log，以查看消息是在群集中发送和接收的

>[!NOTE]
>
>在上一步中保存配置后，导航到OSGi控制台可能需要几秒钟的时间。 您还可以查看error.log以了解更多详细信息。

例如，成功配置ActiveMQ Artemis Server时，将显示以下图像。

如果未在&#x200B;*/system/console/mq*&#x200B;中看到以下配置，请导航到&#x200B;*/system/console/mq*&#x200B;并单击&#x200B;**重新启动**&#x200B;以重新启动该代理。

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### 删除推荐人标头要求{#remove-referrer-header-requirement}

按照每个Publish实例上的步骤操作：

1. 导航到&#x200B;**OSGi Console** > **Configuration Manager**
1. 选择&#x200B;**Apache Sling推荐人过滤器**
1. 更新配置和&#x200B;**选中“允许空**”

### 配置作者实例和发布实例{#configuring-author-and-publish-instance}

设置发布拓扑后，您需要配置作者实例和发布实例，以视图实施的实际结果：

>[!NOTE]
>
>**前提条件**
>
>要开始使用此示例，请新建一个AEM Screens项目，然后在项目中创建位置、显示和渠道。 将内容添加到渠道，并将渠道分配给显示屏。

#### 第1步：启动AEM Screens Player（设备）{#step-starting-an-aem-screens-player-device}

1. 启动一个单独的浏览器窗口。
1. 使用&#x200B;*Web浏览器*（即`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html`）转到Screens播放器，或启动AEM Screens应用程序。 在打开设备时，您会注意到设备的状态为未注册。

>[!NOTE]
>
>您可以使用您下载的AEM Screens应用程序或使用Web浏览器打开AEM Screens播放器。

#### 第2步：在作者上注册设备{#step-registering-a-device-on-author}

1. 转到`https://localhost:4502/screens.html/content/screens/we-retail`或选择您的项目，然后导航到设备>设备管理器。
1. 选择&#x200B;**注册设备**。
1. 单击&#x200B;**设备注册**&#x200B;以视图设备。
1. 选择要注册的设备，然后单击&#x200B;**注册设备**。
1. 验证注册代码，然后单击&#x200B;**验证**。
1. 输入设备标题，然后单击&#x200B;**注册**。

#### 第3步：将设备分配给显示{#step-assigning-the-device-to-display}

1. 从上一步的对话框中单击&#x200B;**指定显示**。
1. 从&#x200B;**位置**&#x200B;文件夹中选择渠道的显示路径。
1. 单击&#x200B;**分配**。
1. 单击&#x200B;**完成**&#x200B;以完成该过程，现在已分配设备。

检查您的播放器，您会看到您在渠道中添加的内容。

#### 第4步：将设备配置发布到发布实例{#step-publishing-device-configuration-to-publish-instances}

**验证设备**

之前，请执行以下步骤，确保验证设备ID。 要进行验证，请在CRXDE Lite中搜索设备id，路径为&#x200B;*/home/users/screens/we-retail/devices*。

请按照以下步骤复制设备用户：

1. 导航到用户管理页面(例如：`https://localhost:4502/useradmin`
1. 搜索&#x200B;**screens-devices-主控**&#x200B;组
1. 右键单击该组，然后单击&#x200B;**激活**

>[!CAUTION]
>
>请勿激活作者 — 发布 — screens-service，因为它是系统用户，由作者作业使用。

您还可以从设备管理控制台激活设备。 应遵循以下步骤：

1. 导航到您的Screens项目 — > **设备**。
1. 单击操作栏中的&#x200B;**设备管理器**。
1. 选择设备，然后单击操作栏中的&#x200B;**激活**，如下图所示。

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>或者，在激活设备后，您也可以通过单击操作栏中的&#x200B;**编辑服务器URL**&#x200B;来编辑或更新服务器URL，如下图所示，您所做的更改将传播到AEM Screens播放器。

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### 发布检查列表{#publishing-check-list}

以下几点概括了“发布检查”列表:

* *Screens设备用户*  — 它存储为AEM用户，并从工具>安全>用 **户** > **安全** >用 **户激活**。用户将在前缀为“screens”，前缀为一个长序列化字符串。

* *项目* -AEM Screens项目。
* *位置*  — 设备连接到的位置。
* *渠道*  — 在位置显示的一个或多个渠道
* *计划*  — 如果使用计划，请确保已发布
* *位置、计划和渠道文件夹*  — 如果相应的资源位于某个文件夹中。

请按照以下步骤验证作者/发布行为：

1. 在创作实例上更新一些渠道内容
1. 执行&#x200B;**管理发布**&#x200B;以将所有发布实例发布新更改
1. 按&#x200B;**激活**&#x200B;以从&#x200B;**设备管理器**&#x200B;激活设备
1. **编** 辑从作者实例URL到某个发布实例URL的URL
1. 验证更新的渠道内容是否显示在AEM Screens播放器上
1. 使用其他发布实例重复这些步骤


#### 第5步：在管理面板{#step-pointing-the-device-to-publish-instance-in-the-admin-panel}中指向设备以发布实例

1. 从Screens播放器中视图管理员UI，长按左上角以打开“管理员”菜单，在启用触摸的AEM Screens播放器上，或使用鼠标。
1. 单击侧面板中的&#x200B;**配置**&#x200B;选项。
1. 将作者实例更改为在&#x200B;**Server**&#x200B;中发布实例。

视图AEM Screens播放器中的更改。

或者，您也可以通过以下步骤从设备管理控制台更新/编辑服务器URL:

1. 导航到您的AEM Screens项目并选择&#x200B;**Devices**&#x200B;文件夹。
1. 单击操作栏中的&#x200B;**设备管理器**。
1. 选择设备，然后单击操作栏中的&#x200B;**编辑服务器URL**，如下图所示，您所做的更改将传播到AEM Screens播放器。

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

**管理发布**&#x200B;功能允许您将内容更新从作者传送到发布到设备。 您可以发布/取消发布整个AEM Screens项目的内容，或仅发布到您的某个渠道、位置、设备、应用程序或计划的内容。 要进一步了解此功能，请参阅[点播内容更新](on-demand-content.md)。


