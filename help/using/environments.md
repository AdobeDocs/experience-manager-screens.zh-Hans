---
title: 环境 [!UICONTROL AEM Screens]
description: 了解有关AEM Screens项目环境的更多信息。
source-git-commit: 3c4b37b3b9f268b500562fa4ce3782b7be1e7d74
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# 环境 {#environments}

提前确定客户端具有和期望您使用的AEM环境，两者都用于 *开发* 和 *部署*.

>[!NOTE]
>
>AEM Screens需要多个包才能使项目正常运行。 所有环境都应运行相同版本的Adobe Experience Manager。

请遵循以下准则为您的AEM Screens项目设置环境：

1. 为您的Adobe Experience Manager版本运行以下包的最新版本：

   * **AEM Service Pack**
   * **屏幕功能包**
   * **AEM累积修补程序包**

1. 确定所需的任何开发包（例如WCM核心组件）或第三方工具包（例如SAP Hybris）。

1. 在本地开发环境中安装相同的软件包。

1. 指示您的客户端在其所有QA、暂存和生产服务器上采用相同的配置。 服务器配置不匹配会在部署和测试时造成问题。
