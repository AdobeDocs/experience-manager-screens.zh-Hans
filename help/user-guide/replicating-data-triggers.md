---
title: 将数据触发器复制到发布服务器
seo-title: 将数据触发器复制到发布服务器
description: 将数据触发器复制到发布服务器。
seo-description: 将数据触发器复制到发布服务器。
translation-type: tm+mt
source-git-commit: a8ded0c15e0e3cbaf0999da796789991b20d24cb

---


# 将数据触发器复制到发布服务器 {#replicating-data-triggers}

当使用ContextHub和AEM Targeting engine根据创作／发布设置中的数据触发器自定义内容时，所有与ContextHub和Personalization相关的配置在渠道发布后不会自动与渠道复制。

可查看本页以了解单独发布这些配置所需的手册步骤。

这主要归结于手动发布：

1. ContextHub存储和UI模块配置
1. 个性化受众
1. 个性化活动

## 将数据触发器复制到发布服务器的步骤 {#replicating-data-triggers-publish}

按照以下步骤将数据触发器复制到发布服务器：

### 复制ContextHub配置 {#replicating-contexthub-configurations}

1. 导航到“ **部署** ” > “ **部署** ” > “分发 **”** > “发布代理工 ****&#x200B;具” http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish
1. 单击“Test Connection”按钮验证作者是否可以与发布实例正确通信
1. 如果测试失败，您需要修复创作和发布之间的复制代理配置
1. 确保端点URL也指向Distribution agent中的发布服务器URL
1. “编辑”>“导入程序端点”
1. 单击“分发”选项卡
1. 选择“添加树”单选按钮
1. 在路径浏览器中，选择项目的配置路径(即/conf/screens/settings/cloudsettings/configuration)
1. 单击提交

### 复制受众 {#replicating-audiences}

1. 导航到工具>个性化>受众http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html
1. 进入您的项目文件夹(即/conf/screens/)
1. 在UI中选择所有受众／区段
1. 单击“管理发布”
1. 单击“下一步”
1. 单击“发布”

### 复制活动 {#replicating-activities}

1. 导航到工具>个性化>活动http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html
1. 进入您的项目文件夹(即/content/campaigns/screens/...)
1. 在UI中选择所有活动
1. 单击“管理发布”
1. 单击“下一步”
1. 单击“发布”

> [!Note]
>复制ContextHub配置和受众是在项目设置期间完成的，同时复制活动，并且每次在渠道内更改目标时都需要复制这些配置和受众。

#### 结果 {#result}

如果复制成功，您应查看发布实例的以下结构（或项目的类似结构）:

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`