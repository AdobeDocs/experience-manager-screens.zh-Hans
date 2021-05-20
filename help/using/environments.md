---
title: '[!UICONTROL AEM Screens]的环境'
seo-title: '[!UICONTROL AEM Screens]的环境'
description: 本页介绍AEM Screens项目的环境。
seo-description: 本页重点介绍AEM Screens项目的环境。
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 4%

---


# 环境 {#environments}

预先确定客户端拥有并将希望您使用的AEM环境，包括&#x200B;*development*&#x200B;和&#x200B;*deployment*。

>[!NOTE]
>
>AEM Screens需要多个包才能使项目正常运行。 所有环境都应运行相同版本的Adobe Experience Manager。

请按照以下准则为AEM Screens项目设置环境：

1. 为您的Adobe Experience Manager版本运行以下包的最新版本：

   * **AEM Service Pack**
   * **Screens功能包**
   * **AEM 累积修补程序包**

1. 识别所需的任何开发包（例如，WCM核心组件）或第三方工具包（例如，SAP Hybris）。

1. 在本地开发环境中安装相同的软件包。

1. 指示您的客户端在其所有QA、暂存和生产服务器上采用相同的配置。 不匹配的服务器配置在部署和测试时会出现问题。
