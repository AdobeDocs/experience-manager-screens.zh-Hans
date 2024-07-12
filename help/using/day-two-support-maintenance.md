---
title: 第二天支持和维护
description: 了解AEM Screens的第二天支持和维护。
exl-id: 2b5511ff-c8f4-4ea3-8a65-f17f3a1ec39b
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---

# Day Two平台支持和维护 {#day-two-support-maintenance}

AEM Screens需要多个包才能使项目正常运行。 所有环境都必须运行相同版本的Adobe Experience Manager。

遵循项目开发阶段第二天的支持和维护准则：

1. 为您的Adobe Experience Manager版本运行以下包的最新版本：

   * **AEM Service Pack**
   * **Screens功能包**
   * **AEM累积修补程序包**

1. 确定所需的任何开发包（例如WCM核心组件）或第三方工具包（例如SAP Hybris）。

1. 将相同的软件包安装到本地开发环境中。

1. 指示您的客户端在其所有QA、暂存和生产服务器上采用相同的配置。 服务器配置不匹配会在部署和测试时造成问题。
