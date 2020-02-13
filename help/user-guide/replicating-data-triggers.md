---
title: 将数据触发器复制到发布服务器
seo-title: 将数据触发器复制到发布服务器
description: 将数据触发器复制到发布服务器。
seo-description: 将数据触发器复制到发布服务器。
translation-type: tm+mt
source-git-commit: 8e5ad12efe53a9a9f4dcdde62be07fb9341dbb84

---


# 将数据触发器复制到发布服务器 {#replicating-data-triggers}

当使用ContextHub和AEM Targeting engine根据创作／发布设置中的数据触发器自定义内容时，所有与ContextHub和Personalization相关的配置在渠道发布后不会自动与渠道复制。

可查看本页以了解单独发布这些配置所需的手册步骤。

这主要归结于手动发布：

1. ContextHub存储和UI模块配置
1. 个性化受众
1. 个性化活动

## 将数据触发器复制到发布服务器的步骤 {#replicating-data-triggers-publish}

按照以下步骤将数据触发器复制到发布服务器。

### 第1步：复制ContextHub配置 {#replicating-contexthub-configurations}

1. 导航到“ **Publish Agent”(** 部署 **)>“** Deployment **”（部署）** >“Distribution **”（分发）** >“Publish Agent”（发布代理），然后单击以配置发布代理的设置。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!Note]
   >或者，您也可以使用 `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` 导航到屏幕来配置和测试连接。

1. 单击 **操作栏中的“Test Connection** ”，验证作者与发布实例的通信，如下图所示。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!Note]
   >如果测试失败，您需要修复作者实例和发布实例之间的复制代理配置。 有关更多详 [细信息，请参阅Test Connection](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) 疑难解答。

1. 从 **** Distribution Agent **（分发代理）屏幕树中选择** Add（添加），然后选择项目的配置路径，例如 `/conf/screens/settings/cloudsettings/configuration`。

1. 单击“提 **交”**

### 复制受众 {#replicating-audiences}

1. 导航到您的AEM实例> **Personalization** > **Audiences** ，或用于 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` 直接导航。

1. 进入项目文件夹，例如 `/conf/screens/`。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 从用户界面中选择所有受众和区段。

1. 单击 **操作栏中的** “管理发布”。

1. 单击“ **下一步** ”和 **“发布**”。

### 复制活动 {#replicating-activities}

1. 导航到您的AEM实例> **Personalization** > **Activities** ，或使用 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` 直接导航。

1. 进入您的项目文件夹，即 `/content/campaigns/screens/…`。

1. 从用户界面中选择所有活动。

1. 单击 **操作栏中的** “管理发布”。

1. 单击“ **下一步** ”和 **“发布**”。

   > [!Note]
   >复制ContextHub配置和受众是在项目设置期间完成的，同时复制活动，并且每次在渠道内更改目标时都需要复制这些配置和受众。

#### 结果 {#result}

如果复制成功，您应查看发布实例的以下结构（或项目的类似结构）:

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 测试连接疑难解答 {#troubleshoot-test}

如果复制ContextHub配置时测试连接失败，请按照以下部分对问题进行疑难解答：

1. 导航到工具>部 **署** >分 **发** >发 **布代理**。

1. 单击 **操作栏中的编辑****** ，并确保导入程序端点字段中的端点URL也指向Distribution agent中的发布服务器URL。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 如果您没有使用默认管理员凭据，则需要使用其他用户名和密码配置分发代理。
按照以下步骤操作：

   1. 导航到工具> **操作** > **Web控制台** , `http://localhost:4502/system/console/configMgr`以打开 **Adobe Experience Manager Web Console屏幕**。

   1. 搜索 **Apache Sling Distribution Transport Credentials —— 基于用户凭据的DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 通过填充Name **、** User name **** and **password（例如，slingTransportSecretProvider）来创建****&#x200B;配置。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Click **Save**

   1. 使用 `Cmd +F` 搜索 **Apache Sling Distribution Agent - Forward Agents Factory** ，打开配置并搜索传输机密提 **供者**。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. 使用更 `(name=default)` 新 `(name=slingTransportSecretProvider)`。

   1. 单击 **保存** ，然后再次从AEM实例的Distribution Agent屏幕中 **运行测试连接** 。

   1. 用户需要从AEM实例重新访问 **Distribution Agent** （分发代理）页面，以将默认URL从更新／替换 `localhost:4503` 到其自己的发布URL。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)
