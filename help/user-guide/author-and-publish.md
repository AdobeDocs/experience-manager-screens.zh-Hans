---
title: 在AEM Screens中配置作者和发布
seo-title: 在AEM Screens中配置作者和发布
description: AEM Screens建筑类似于传统的AEM Sites建筑。 内容是在AEM作者实例上创作的，然后转发复制到多个发布实例。 可查看本页以了解如何为AEM Screens配置创作和发布。
seo-description: AEM Screens建筑类似于传统的AEM Sites建筑。 内容是在AEM作者实例上创作的，然后转发复制到多个发布实例。 可查看本页以了解如何为AEM Screens配置创作和发布。
uuid: 0a6e87e7-0018-42ef-b484-9a3da61c636a
contentOwner: jsyal
content-type: reference
topic-tags: authoring
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: f2397d11-a18b-4779-b77b-5f99b797f40c
docset: aem65
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '1893'
ht-degree: 3%

---


# 在AEM Screens中配置作者和发布 {#configuring-author-and-publish-in-aem-screens}

本页重点介绍以下主题：

* **配置作者实例和发布实例**
* **设置发布拓扑**
* **管理发布： 将内容更新从作者交付到发布到设备**

## 前提条件 {#prerequisites}

在开始使用作者服务器和发布服务器之前，您应事先了解：

* **AEM拓扑**
* **创建和管理AEM Screens项目**
* **设备注册过程**

>[!NOTE]
>
>此AEM Screens功能仅在您安装了AEM 6.4 Screens功能包2时可用。 要获取此功能包，您必须联系 Adobe 支持人员并申请访问权限。您获得权限后，就可以从“包共享”下载它。

## 配置作者和发布实例 {#configuring-author-and-publish-instances}

>[!NOTE]
>
>要进一步了解作者和发布体系结构概述，以及如何在AEM作者实例上创作内容，然后将其转发复制到多个发布实例，请参阅作 [者和发布体系结构概述](author-publish-architecture-overview.md)。

以下部分介绍如何在创作和发布拓扑上设置复制代理。

您可以设置一个简单的示例，其中承载一个作者和两个发布实例：

* 作者—> localhost:4502
* 发布1(pub1)—> localhost:4503
* Publish 2(pub2)—> localhost:4504

## 在作者上设置复制代理 {#setting-replication-agents}

要创建复制代理，您必须学习如何创建标准复制代理。

有3个复制代理需要用于Screens:

1. **默认复制代&#x200B;***理(指定为***“标准复制代理**”)
1. **屏幕复制代理**
1. **反向复制代理**

### 第1步： 创建默认复制代理 {#step-creating-a-default-replication-agent}

请按照以下步骤创建默认复制代理：

1. 导航到AEM实例—>锤子图标—> **操作** —> **配置**。

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 从左侧 **导航** 树中选择复制。

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. 从“复 **制”文件夹** 中选择创作 **代理** ，然后单 **击“新建** ”以创建新的标准复制代理。

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. 输入标 **题** 和名 **称** 以创建复制代理，然后单 **击创建**。

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. 右键单击复制代理，然后单 **击打** 开以编辑设置。

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. 单击 **编辑** ，打开代理 **设置对** 话框，输入详细信息。

   >[!NOTE]
   >
   >用户需要选中“ **已启用** ”以启用复制代理。 必须在“默认”、“屏幕”和“反向复制代理”上选中此选项。

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. 导航到“ **传输** ”选项卡， **然后输入** URI **、** User **** and Password 。

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >您还可以复制和重命名现有的默认复制代理。


#### 创建标准复制代理  {#creating-standard-replication-agents}

1. 为pub1创建标准复制代理（应已配置现成默认代理）(例如， *https://&lt;hostname>:4503/bin/receive?sling:authRequestLogin=1*)
1. 为pub2创建标准复制代理。 您可以复制pub1的rep代理，并通过更改传输配置中的端口来更新要用于pub2的传输。 (例如， *https://&lt;hostname>:4504/bin/receive?sling:authRequestLogin=1*)

#### 创建Screens复制代理 {#creating-screens-replication-agents}

1. 为pub1创建AEM Screens复制代理。 现成，有一个名为Screens复制代理，它指向端口4503。 需要启用此项。
1. 为pub2创建AEM Screens复制代理。 复制pub1的Screens复制代理，并将pub2的端口更改为指向4504。

#### 创建屏幕反向复制代理 {#creating-screens-reverse-replication-agents}

1. 为pub1创建标准反向复制代理。
1. 为pub2创建标准反向复制代理。 您可以复制pub1的反向rep代理，并通过更改传输配置中的端口来更新要用于pub2的传输。

## 设置发布拓扑 {#setting-up-publish-topology}

### 第1步： 配置基于Apache Sling Oak的发现 {#step-configure-apache-sling-oak-based-discovery}

为拓扑中的所有Publish实例设置Apache Sling Oak-Based Discovery

对于每个发布实例：

1. 导航至 `https://<host>:<port>/system/console/configMgr`
1. 选 **择Apache Sling Oak-Based Discovery Service** Configuration。
1. 更新拓扑连接器URL: 添加以下所有参与发布实例的URL:
   * `https://localhost:4503/libs/sling/topology/connector`
   * `https://localhost:4504/libs/sling/topology/connector`
1. **拓扑连接器白名单列表**: 适应包含参与发布实例的IP或子网
1. 启 **用自动停止本地循环**

每个发布实例的配置应相同，自动停止本地循环将阻止无限循环。

#### 第2步： 验证发布拓扑 {#step-verify-publish-topology}

对于任何发布实例，导航到 `https://:/system/console/topology`。 应在“传出拓扑连接器”下看到拓扑中表 **示的每个发布实例**。

#### 第3步： 设置ActiveMQ Artemis群集 {#step-setup-activemq-artemis-cluster}

此步骤允许您为ActiveMQ Artemis群集创建加密密码。
拓扑中所有发布实例的群集用户和口令必须相同。 需要加密ActiveMQ Artemis配置的口令。 由于每个实例都有其自己的加密密钥，因此必须使用加密支持来创建加密的密码字符串。 然后，加密密码将用于ActiveMQ的OSGi配置。

在每个Publish实例上：

1. 在OSGi控制台中， **导航到** MAIN —> **加密支** 持&#x200B;*(* https://&lt;host>:&lt;port>/system/console/crypto)。
1. 在纯文本中键入所需的纯文本口令(对于所有实例均 **相同)**
1. 单击 **保护**。
1. 将值“受保护 **文本** ”复制到记事本或文本编辑器。 此值将用于ActiveMQ的OSGi配置。

由于每个发布实例默认具有唯一加密密钥，因此您需要对每个发布实例执行此步骤，并保存下一个配置的唯一密钥。

>[!NOTE]
>
>密码应开始，并以大括号结束。 例如：
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### 第4步： 激活ActiveMQ Artemis群集 {#step-activate-activemq-artemis-cluster}

在每个发布实例上：

1. 导航到OSGi配置 *管理器https://&lt;host>:&lt;port>/system/console/configMgr*
1. 选 **择Apache ActiveMQ Artemis JMS提供程序配置**
1. 更新以下内容：

* ***群集密码***: （为每个实例使用上一步中的加密值）
* ***主题***: {名称： &#39;commands&#39;，地址： &#39;com.adobe.cq.screens.commands&#39;, maxConsumers: 50}

#### 验证ActiveMQ Artemis群集 {#verify-activemq-artemis-cluster}

对每个Publish实例执行以下步骤：

1. 导航到OSGi控制台->主> ActiveMQ Artemis `[https://localhost:4505/system/console/mq`。
1. 验证并检查以视图群集信息>拓扑>节点=2，成员=2下其他实例的端口。
1. 发送测试消息(“Broker Information（代理信息）”下屏幕顶部)
1. 在字段中输入以下更改：

   1. **目标**: /com.adobe.cq.screens/devTestTopic
   1. **文本**: Hello World
   1. 视图每个实例的error.log，以查看消息是通过群集发送和接收的

>[!NOTE]
>
>在前一步中保存配置后，导航到OSGI控制台可能需要几秒钟的时间。 您还可以检查error.log以了解更多详细信息。

例如，成功配置ActiveMQ Artemis Server时，将显示以下图像。

如果未从/system/console/mq看到以 *下配置*，请导航到 */system/console/mq，然后单击“重新启* 动 **** ”以重新启动代理。

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### 删除推荐人标题要求 {#remove-referrer-header-requirement}

按照每个发布实例上的步骤操作：

1. 导航到OSGi **控制台** >配 **置管理器**
1. 选择 **Apache Sling推荐人过滤器**
1. 更新配置并选 **中允许空**

### 配置作者和发布实例 {#configuring-author-and-publish-instance}

设置发布主题后，您需要配置作者实例和发布实例，以视图实施的实际结果：

>[!NOTE]
>
>**前提条件**
>
>要开始使用此示例，请新建一个AEM Screens项目，然后在项目中创建位置、显示和渠道。 向渠道添加内容，并将渠道分配给显示屏。

#### 第1步： 启动AEM Screens播放器（设备） {#step-starting-an-aem-screens-player-device}

1. 启动一个单独的浏览器窗口。
1. Go to Screens player using the *web browser*, that is,`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` or launch the AEM Screens app. 在打开设备时，您会注意到设备的状态为未注册。

>[!NOTE]
>
>您可以使用您下载的AEM Screens应用程序或Web浏览器打开AEM Screens播放器。

#### 第2步： 在作者上注册设备 {#step-registering-a-device-on-author}

1. 转到或选 `https://localhost:4502/screens.html/content/screens/we-retail` 择您的项目，然后导航到设备>设备管理器。
1. 选择 **注册设备**。
1. 单击 **设备注册** ，以视图设备。
1. Select the device you want to register and click **Register Device**.
1. 验证注册代码，然后单击“ **验证**”。
1. 输入设备的标题，然后单击“ **注册**”。

#### 第3步： 将设备分配给显示 {#step-assigning-the-device-to-display}

1. 在上 **一步中** ，单击对话框中的“指定显示”。
1. 从“位置”文件夹中选择渠道的显 **示路** 径。
1. Click **Assign**.
1. Click **Finish** to complete the process, and now the device is assigned.

检查您的播放器，您将看到您在渠道中添加的内容。

#### 第4步： 将设备配置发布到发布实例 {#step-publishing-device-configuration-to-publish-instances}

**验证设备**

之前，请执行以下步骤，确保验证设备ID。 要进行验证，请在CRXDELite中搜索设备id，路径 *为/home/users/screens/we-retail/devices*。

请按照以下步骤复制设备用户：

1. 导航到用户管理页面(例如： `https://localhost:4502/useradmin`
1. 搜索屏幕 **-设备-主控组**
1. 右键单击用户组，然后单击激活 **。**

>[!CAUTION]
>
>请勿激活作者——发布——屏幕——服务，因为它是系统用户，由作者作业使用。

您还可以从设备管理控制台激活设备。 应遵循以下步骤：

1. 导航到您的Screens项目—> **设备**。
1. Click **Device Manager** from the action bar.
1. 选择设备，然 **后** ，单击操作栏中的激活，如下图所示。

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>或者，在激活设备后，您还可以通过单击操作栏中的 **编辑服务器** URL来编辑或更新服务器URL，如下图所示，您所做的更改将传播到AEM Screens播放器。

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### 发布检查列表 {#publishing-check-list}

以下要点概括了Publishing Check列表:

* *Screens设备用户* -它存储为AEM用户，并从“工具”>“安 **全** ”> **“用** 户”激活 ****。 用户将在前面加上带有长序列号字符串的“screens”。

* *项目* -AEM Screens项目。
* *位置* -设备所连接的位置。
* *渠道* -在位置显示的一个或多个渠道
* *计划* -如果使用计划，请确保已发布
* *位置、计划和渠道文件夹* -如果相应的资源位于某个文件夹中。

请按照以下步骤验证作者／发布行为：

1. 更新创作实例上的一些渠道内容
1. 执行 **管理发布** ，以将新更改发布到所有发布实例
1. 按 **激活** ，以从设备管理器 **激活设备**
1. **编辑从作** 者实例URL到某个发布实例URL的URL
1. 验证更新的渠道内容是否显示在AEM Screens播放器上
1. 使用其他发布实例重复这些步骤


#### 第5步： 在“管理面板”中将设备指向发布实例 {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. 从Screens播放器视图管理员UI，长按左上角以打开“管理员”菜单、启用触屏的AEM Screens播放器或使用鼠标。
1. 单击侧 **面板** 中的“配置”选项。
1. 将创作实例更改为在服务器中发 **布实例**。

视图AEM Screens播放器中的更改。

或者，您也可以通过设备管理控制台使用以下步骤更新／编辑服务器URL:

1. 导航到您的AEM Screens项目，然后选择 **设备** 文件夹。
1. Click **Device Manager** from the action bar.
1. 选择设备，然 **后单击操作栏** 中的编辑服务器URL，如下图所示，您所做的更改将传播到AEM Screens播放器。

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

通过 **管理发布** ，您可以将内容更新从作者发布到设备。 您可以发布／取消发布整个AEM Screens项目或仅发布渠道、位置、设备、应用程序或计划的内容。 要进一步了解此功能，请参 [阅点播内容更新](on-demand-content.md)。


