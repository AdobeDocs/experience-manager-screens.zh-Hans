---
title: 环境 [!UICONTROL AEM Screens]
seo-title: Environments for [!UICONTROL AEM Screens]
description: 本页介绍了AEM Screens项目的环境。
seo-description: This page highlights the environments for an AEM Screens project.
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 5%

---


# 环境 {#environments}

提前确定客户端具有和预期您将使用的AEM环境，用于 *开发* 和 *部署*.

>[!NOTE]
>
>AEM Screens需要多个包才能使项目正常运行。 所有环境都应运行相同版本的Adobe Experience Manager。

请遵循以下准则为您的AEM Screens项目设置环境：

1. 为您的Adobe Experience Manager版本运行以下包的最新版本：

   * **AEM 服务包**
   * **Screens功能包**
   * **AEM 累积修订包**

1. 确定所需的任何开发包（例如WCM核心组件）或第三方工具包（例如SAP Hybris）。

1. 在本地开发环境中安装相同的软件包。

1. 指示您的客户端在其所有QA、暂存和生产服务器上采用相同的配置。 服务器配置不匹配将在部署和测试时造成问题。
