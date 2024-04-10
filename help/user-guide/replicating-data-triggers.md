---
title: 将数据触发器复制到发布服务器
description: 了解如何将数据触发器复制到AEM Screens的发布服务器。
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 1%

---

# 将数据触发器复制到发布服务器 {#replicating-data-triggers}

使用ContextHub和AEM定位引擎根据创作/发布设置中的数据触发器自定义内容时，所有ContextHub和个性化相关配置在发布时不会自动与渠道一起复制。

本页可帮助您了解单独发布这些配置所需的手动步骤。

这基本上归结为手动发布：

1. ContextHub存储和UI模块配置
1. 个性化受众
1. 个性化活动

## 将数据触发器复制到发布服务器的步骤 {#replicating-data-triggers-publish}

按照以下步骤将数据触发器复制到发布服务器。

### 步骤1：复制ContextHub配置 {#replicating-contexthub-configurations}

1. 导航到 **工具** > **部署** > **分布** > **发布代理** ，然后单击发布代理，以便您配置设置。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >或者，您可以使用 `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` 直接导航到屏幕以配置和测试连接。

1. 单击 **测试连接** 从操作栏中，验证作者与发布实例的通信，如下所示：

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >如果测试失败，请修复创作实例和发布实例之间的复制代理配置。 请参阅 [测试连接疑难解答](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) 以了解更多详细信息。

1. 选择 **添加** 从 **分发代理** 屏幕树并选择项目的配置路径，例如， `/conf/screens/settings/cloudsettings/configuration`.

1. 单击&#x200B;**“提交”。**

### 复制受众 {#replicating-audiences}

1. 导航到您的AEM实例> **个性化** > **受众** 或使用 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` 以直接导航。

1. 向下钻取到您的项目文件夹，例如， `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 从用户界面中选择所有受众和区段。

1. 单击 **管理发布** 从操作栏中。

1. 单击 **下一个** 和 **Publish**.

### 复制活动  {#replicating-activities}

1. 导航到您的AEM实例> **个性化** > **活动** 或使用 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` 以直接导航。

1. 深入到您的项目文件夹，即， `/content/campaigns/screens/…`.

1. 从用户界面中选择所有活动。

1. 单击 **管理发布** 从操作栏中。

1. 单击 **下一个** 和 **Publish**.

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

1. 导航到工具> **部署** > **分布** > **发布代理**.

1. 单击 **编辑** 并确保中的端点URL **导入程序终端** 字段还指向分发代理中的发布服务器URL。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 如果不使用默认管理员凭据，则必须使用其他用户名和密码配置分发代理。

   应遵循以下步骤：

   1. 导航到工具> **操作** > **Web控制台** `http://localhost:4502/system/console/configMgr`这样您就可以打开 **Adobe Experience Manager Web控制台屏幕**.
   1. 搜索 **Apache Sling分发传输凭据 — 基于用户凭据的DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 通过填充以下内容创建配置 **名称**， **用户名**、和 **密码**&#x200B;例如， *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. 单击 **保存**
   1. 使用 `Cmd +F` 以搜索 **Apache Sling分发代理 — 转发代理工厂** 打开配置并搜索 **传输密钥提供程序**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. 更新 `(name=default)` 替换为 `(name=slingTransportSecretProvider)`.
   1. 单击 **保存** 并从重新运行测试连接 **分发代理** 从AEM实例中再次筛选。
