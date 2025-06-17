---
title: 将数据触发器复制到发布服务器
description: 了解如何将数据触发器复制到AEM Screens的发布服务器。
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 1%

---

# 将数据触发器复制到发布服务器 {#replicating-data-triggers}

在创作/发布设置中使用ContextHub和AEM定位引擎根据数据触发器自定义内容时，在发布时所有与ContextHub和Personalization相关的配置都不会自动与渠道一起复制。

本页可帮助您了解单独发布这些配置所需的手动步骤。

此过程基本上归结为手动发布以下内容：

1. ContextHub存储和UI模块配置
1. Personalization受众
1. Personalization活动

## 将数据触发器复制到发布服务器的步骤 {#replicating-data-triggers-publish}

按照以下步骤将数据触发器复制到发布服务器。

### 步骤1：复制ContextHub配置 {#replicating-contexthub-configurations}

1. 导航到&#x200B;**工具** > **部署** > **分发** > **发布代理**，然后单击发布代理，以便您可以配置设置。

   ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >或者，您可以使用`http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish`直接导航到屏幕以配置和测试连接。

1. 单击操作栏中的&#x200B;**测试连接**，以便验证作者与发布实例的通信，如下所示：

   ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >如果测试失败，请修复创作实例和发布实例之间的复制代理配置。 有关详细信息，请参阅[测试连接疑难解答](/help/user-guide/replicating-data-triggers.md#troubleshoot-test)。

1. 从&#x200B;**分发代理**&#x200B;屏幕树中单击&#x200B;**添加**，然后单击项目的配置路径，例如`/conf/screens/settings/cloudsettings/configuration`。

1. 单击&#x200B;**“提交”。**

### 复制受众 {#replicating-audiences}

1. 导航到您的AEM实例> **Personalization** > **受众**，或使用`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html`直接导航。

1. 深入到您的项目文件夹，例如`/conf/screens/`。

   ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 单击用户界面中的所有受众和区段。

1. 单击操作栏中的&#x200B;**管理发布**。

1. 单击&#x200B;**下一步**&#x200B;和&#x200B;**发布**。

### 复制活动 {#replicating-activities}

1. 导航到您的AEM实例> **Personalization** > **活动**，或使用`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html`直接导航。

1. 深入到您的项目文件夹，即`/content/campaigns/screens/…`。

1. 单击用户界面中的所有活动。

1. 单击操作栏中的&#x200B;**管理发布**。

1. 单击&#x200B;**下一步**&#x200B;和&#x200B;**发布**。

>[!IMPORTANT]
>
>复制ContextHub配置和受众是在项目设置期间在复制活动时完成的，每次在渠道内更改定位时都需要这样做。

#### 结果 {#result}

如果复制成功，您应在发布实例上查看以下结构（或项目中的类似结构）：

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 测试连接疑难解答 {#troubleshoot-test}

如果复制ContextHub配置时测试连接失败，请按照以下部分解决此问题：

1. 导航到&#x200B;**工具** > **部署** > **分发** > **发布代理**。

1. 单击操作栏中的&#x200B;**编辑**，并确保&#x200B;**导入程序端点**&#x200B;字段中的端点URL也指向分发代理中的发布服务器URL。
   ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 如果不使用默认管理员凭据，则必须使用其他用户名和密码配置分发代理。

   应遵循以下步骤：

   1. 导航到“工具”>“**操作**”>“**Web控制台**”`http://localhost:4502/system/console/configMgr`，以便打开&#x200B;**Adobe Experience Manager Web控制台屏幕**。
   1. 搜索&#x200B;**`Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider`**

      ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 通过填充&#x200B;**Name**、**User name**&#x200B;和&#x200B;**password**&#x200B;创建配置，例如&#x200B;*slingTransportSecretProvider*。

      ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. 单击&#x200B;**保存**
   1. 使用`Cmd +F`搜索&#x200B;**Apache Sling分发代理 — 转发代理工厂**&#x200B;以打开配置并搜索&#x200B;**传输密钥提供程序**。

      ![图像1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. 使用`(name=slingTransportSecretProvider)`更新`(name=default)`。
   1. 单击&#x200B;**保存**，然后再次从AEM实例的&#x200B;**分发代理**&#x200B;屏幕运行测试连接。
