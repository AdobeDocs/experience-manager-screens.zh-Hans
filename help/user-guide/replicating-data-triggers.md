---
title: 将数据触发器复制到发布服务器
seo-title: 将数据触发器复制到发布服务器
description: 将数据触发器复制到发布服务器。
seo-description: 将数据触发器复制到发布服务器。
translation-type: tm+mt
source-git-commit: 081db31efda17ac12cdc88f79ed2f4e1fbfc7edf
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 2%

---


# 将数据触发器复制到发布服务器 {#replicating-data-triggers}

在创作／发布设置中使用ContextHub和AEM Targeting Engine根据数据触发器自定义内容时，所有与ContextHub和Personalization相关的配置在发布时不会自动与渠道复制。

可查看本页以了解单独发布这些配置所需的手册步骤。

这主要归结于手动发布：

1. ContextHub存储和UI模块配置
1. 个性化受众
1. 个性化活动

## 将数据触发器复制到发布服务器的步骤 {#replicating-data-triggers-publish}

请按照以下步骤将数据触发器复制到发布服务器。

### 第1步：复制ContextHub配置 {#replicating-contexthub-configurations}

1. 导航到 **工具** >部 **署** >分发 **>** 分发 **>发布代理** ，然后单击发布代理以配置您的设置。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >或者，也可以使用 `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` 直接导航到屏幕来配置和测试连接。

1. 单击 **操作栏** 中的“测试连接”，验证作者与发布实例的通信，如下图所示。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >如果测试失败，您需要在作者实例和发布实例之间修复复制代理配置。 有关更多详 [细信息，请参阅](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) “Troubleshooting Test Connection（测试连接疑难解答）”。

1. 从 **Distribution Agent****屏幕树中选择** “添加”，然后选择项目的配置路径，例如 `/conf/screens/settings/cloudsettings/configuration`。

1. 单击 **提交**。

### 复制受众 {#replicating-audiences}

1. 导航到AEM实例>个性 **化** > **受众** ，或 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` 用于直接导航。

1. 进入您的项目文件夹，例如 `/conf/screens/`。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 从用户界面中选择所有受众和区段。

1. 单击 **操作栏** 中的管理发布。

1. 单击 **下一** 步 **和发布**。

### 复制活动  {#replicating-activities}

1. 导航到AEM实例>个性 **化** > **活动** ，或 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` 用于直接导航。

1. 进入您的项目文件夹，即 `/content/campaigns/screens/…`。

1. 从用户界面中选择所有活动。

1. 单击 **操作栏** 中的管理发布。

1. 单击 **下一** 步 **和发布**。

>[!IMPORTANT]
>
>复制ContextHub配置和受众是在项目设置期间完成的，同时复制活动，每次在渠道内更改目标时都需要复制这些配置和。

#### 结果 {#result}

如果复制成功，您应在发布实例上视图以下结构（或类似于您的项目）:

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 测试连接疑难解答 {#troubleshoot-test}

如果复制ContextHub配置时测试连接失败，请按照以下部分排除问题：

1. 导航到工具> **部署** > **分发** > **发**&#x200B;布代理。

1. 单击 **操作栏** 中的编辑，并确保导入程序端点字段 **中的端点URL** 也指向分发代理中的发布服务器URL。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 如果您未使用默认管理员凭据，则需要使用不同的用户名和密码配置分发代理。

   应遵循以下步骤：

   1. 导航到工具> **操作** > **Web控制台** , `http://localhost:4502/system/console/configMgr`以打开 **Adobe Experience ManagerWeb控制台屏幕**。
   1. 搜索Apache **Sling分发传输凭据——基于用户凭据的DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 通过填充Name **、User** name **** and **password**(例如， *slingTransportSecretProvider)*&#x200B;创建配置。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Click **Save**
   1. 使用 `Cmd +F` 搜索Apache **Sling Distribution Agent - Forward Agent Factory** ，打开配置并搜索传 **输机密提供程序**。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. 更新 `(name=default)` 为 `(name=slingTransportSecretProvider)`。
   1. 单击 **保存** ，再次从AEM实例的 **Distribution Agent屏幕中** 运行测试连接。
