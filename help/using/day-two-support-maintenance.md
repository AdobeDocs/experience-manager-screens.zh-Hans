---
title: 第二天支持和维护
description: 了解AEM Screens的第二天支持和维护。
exl-id: 2b5511ff-c8f4-4ea3-8a65-f17f3a1ec39b
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Day Two平台支持和维护 {#day-two-support-maintenance}

AEM Screens需要多个包才能使项目正常运行。 所有环境都必须运行相同版本的Adobe Experience Manager。

在项目开发阶段的第二天遵循支持和维护准则：

1. 为您的Adobe Experience Manager版本运行以下包的最新版本：

   * **AEM Service Pack**
   * **屏幕功能包**
   * **AEM累积修补程序包**

1. 确定所需的任何开发包（例如WCM核心组件）或第三方工具包（例如SAP Hybris）。

1. 在本地开发环境中安装相同的软件包。

1. 指示您的客户端在其所有QA、暂存和生产服务器上采用相同的配置。 服务器配置不匹配会在部署和测试时造成问题。
