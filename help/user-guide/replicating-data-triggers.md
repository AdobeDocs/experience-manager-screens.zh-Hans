---
title: 将数据触发器复制到发布服务器
seo-title: 将数据触发器复制到发布服务器
description: 将数据触发器复制到发布服务器。
seo-description: 将数据触发器复制到发布服务器。
translation-type: tm+mt
source-git-commit: 47e0204ea734a1348385ddd3c7108038c88d1933

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
   >或者，您也可以使用链 [接](http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish) ，直接导航到屏幕以配置和测试连接。

1. 单击 **操作栏中的“Test Connection** ”，验证作者与发布实例的通信，如下图所示。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!Note]
   >如果测试失败，您需要修复作者实例和发布实例之间的复制代理配置。 有关更多详 [细信息，请参阅Test Connection](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) 疑难解答。

1. 从上 **面的屏幕中单击****** “编辑”，确保“导入程序端点”字段中的端点URL也指向Distribution agent中的发布服务器URL。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers3.png)

1. 从 **** Distribution Agent **屏幕树中选择添加** ，然后为项目选择配置路径，即 `/conf/screens/settings/cloudsettings/configuration)`。

1. 单击“提 **交”**

### 复制受众 {#replicating-audiences}

1. 导航到工 **具** > **个性化** >受众 **，或直接**[](http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html) 使用链接导航。

1. 进入您的项目文件夹，即 `/conf/screens/`。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers5.png)

1. 从用户界面中选择所有受众和区段。

1. 单击 **操作栏中的** “管理发布”。

1. 单击“ **下一步** ”和 **“发布**”。

### 复制活动 {#replicating-activities}

1. 导航到工 **具** > **Personalization** >活动，或使 **用链接直**[](http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html) 接导航。

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

1. 导航到导 **入程序端点字段** ，并确保端点URL指向Distribution agent中的发布服务器URL。

1. 如果未使用默认凭据，则需要使用其他管理员密码配置分发代理。
按照以下步骤操作：

   1. 导航到“工具”>“ **操作** ”>“Web控制台”**, `http://localhost:4502/system/console/configMgr`以打开 **Adobe Experience Manager web控制台屏幕**。

   1. 搜索 **Apache Sling Distribution Transport Credentials —— 基于用户凭据的DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 通过填充Name **、** User name **** and **password（例如，slingTransportSecretProvider）来创建****&#x200B;配置。.
   1. Click **Save**

   1. 使用搜索您的分发代理的名称 `Cmd +F`。

   1. 单击以打开分发代理OSGI配置。

   1. 在osgi配置中查找传输机密提供者，并将其更新为 `"(name=slingTransportSecretProvider)"`。

   1. 单击 **保存** ，然后运行测试连接。

