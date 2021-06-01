---
title: 将数据触发器复制到发布服务器
seo-title: 将数据触发器复制到发布服务器
description: 可查看本页以了解如何将数据触发器复制到发布服务器。
seo-description: 将数据触发器复制到发布服务器。
feature: 管理屏幕、数据触发器
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 2%

---


# 将数据触发器复制到发布服务器{#replicating-data-triggers}

使用ContextHub和AEM定位引擎根据创作/发布设置中的数据触发器自定义内容时，所有与ContextHub和个性化相关的配置在发布时不会自动与渠道复制。

请阅读本页，了解单独发布这些配置所需的手册步骤。

这基本上可以归结为手动发布：

1. ContextHub存储和UI模块配置
1. 个性化受众
1. 个性化活动

## 将数据触发器复制到发布服务器{#replicating-data-triggers-publish}的步骤

请按照以下步骤将数据触发器复制到发布服务器。

### 步骤1:复制ContextHub配置{#replicating-contexthub-configurations}

1. 导航至&#x200B;**工具** > **部署** > **分发** > **发布代理** ，然后单击发布代理以配置您的设置。

   ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >或者，您也可以使用`http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish`直接导航到屏幕以配置和测试连接。

1. 单击操作栏中的&#x200B;**测试连接**&#x200B;以验证作者与发布实例的通信，如下图所示。

   ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >如果测试失败，您需要修复创作实例和发布实例之间的复制代理配置。 有关更多详细信息，请参阅[测试连接疑难解答](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) 。

1. 从&#x200B;**Distribution Agent**&#x200B;屏幕树中选择&#x200B;**Add**，然后选择项目的配置路径，例如`/conf/screens/settings/cloudsettings/configuration`。

1. 单击&#x200B;**Submit**。

### 复制受众{#replicating-audiences}

1. 导航到AEM实例> **Personalization** > **Audiences**&#x200B;或使用`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html`直接导航。

1. 深入到您的项目文件夹，例如`/conf/screens/`。

   ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 从用户界面中选择所有受众和区段。

1. 单击操作栏中的&#x200B;**管理发布** 。

1. 单击&#x200B;**Next**&#x200B;和&#x200B;**Publish**。

### 复制活动{#replicating-activities}

1. 导航到AEM实例> **Personalization** > **活动**&#x200B;或使用`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html`直接导航。

1. 深入到您的项目文件夹，即`/content/campaigns/screens/…`。

1. 从用户界面中选择所有活动。

1. 单击操作栏中的&#x200B;**管理发布** 。

1. 单击&#x200B;**Next**&#x200B;和&#x200B;**Publish**。

>[!IMPORTANT]
>
>复制ContextHub配置和受众在项目设置期间完成，同时复制活动，每次在渠道中更改定位时都需要复制和。

#### 结果 {#result}

如果复制成功，您应该在发布实例上查看以下结构（或者与您的项目类似）：

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 测试连接疑难解答{#troubleshoot-test}

如果在复制ContextHub配置时测试连接失败，请按照以下部分对问题进行故障诊断：

1. 导航到工具> **部署** > **分发** > **发布代理**。

1. 单击操作栏中的&#x200B;**编辑** ，并确保&#x200B;**导入程序端点**字段中的端点URL也指向Distribution Agent中的发布服务器URL。
   ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 如果您没有使用默认的管理员凭据，则需要使用不同的用户名和密码配置分发代理。

   应遵循以下步骤：

   1. 导航至工具> **操作** > **Web控制台** `http://localhost:4502/system/console/configMgr`以打开&#x200B;**Adobe Experience Manager Web Console屏幕**。
   1. 搜索&#x200B;**Apache Sling Distribution Transport凭据 — 基于用户凭据的DistributionTransportSecretProvider**

      ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 通过填充&#x200B;**Name**、**User name**&#x200B;和&#x200B;**password**&#x200B;来创建配置，例如&#x200B;*slingTransportSecretProvider*。

      ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. 单击&#x200B;**Save**
   1. 使用`Cmd +F`搜索&#x200B;**Apache Sling Distribution Agent - Forward Agents Factory**&#x200B;以打开配置并搜索&#x200B;**传输密钥提供程序**。

      ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. 使用`(name=slingTransportSecretProvider)`更新`(name=default)`。
   1. 单击&#x200B;**Save**，然后再次从AEM实例的&#x200B;**Distribution Agent**&#x200B;屏幕中运行测试连接。
