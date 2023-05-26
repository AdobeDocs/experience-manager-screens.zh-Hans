---
title: 第二天支持和维护
seo-title: Day Two Support and Maintenance for AEM Screens
description: 本页介绍了第二天支持和维护
seo-description: The page describes Day Two Support and Maintenance
exl-id: 2b5511ff-c8f4-4ea3-8a65-f17f3a1ec39b
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 9%

---

# Day Two 平台支持和维护 {#day-two-support-maintenance}

AEM Screens需要多个包才能使项目正常运行。 所有环境都应运行相同版本的Adobe Experience Manager。

在项目开发阶段的第二天遵循作为支持和维护的准则：

1. 为您的Adobe Experience Manager版本运行以下包的最新版本：

   * **AEM 服务包**
   * **Screens功能包**
   * **AEM 累积修订包**

1. 确定所需的任何开发包（例如WCM核心组件）或第三方工具包（例如SAP Hybris）。

1. 在本地开发环境中安装相同的软件包。

1. 指示您的客户端在其所有QA、暂存和生产服务器上采用相同的配置。 服务器配置不匹配将在部署和测试时造成问题。
