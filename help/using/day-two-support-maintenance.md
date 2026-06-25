---
title: 第二天支持和维护
description: 了解AEM Screens的第二天支持和维护。
exl-id: 2b5511ff-c8f4-4ea3-8a65-f17f3a1ec39b
TQID: https://experienceleague.adobe.com/IMuRCxE7v8DyK-T4Q3lehhclfgGtu0VIHyIsODOpEzA
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 186
ht-degree: 1%

---

# Day Two平台支持和维护 {#day-two-support-maintenance}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

AEM Screens需要多个包才能使项目正常运行。 所有环境都必须运行相同版本的Adobe Experience Manager。

遵循项目开发阶段第二天的支持和维护准则：

1. 为您的Adobe Experience Manager版本运行以下包的最新版本：

   * **AEM 服务包**
   * **Screens功能包**
   * **AEM累积修补程序包**

1. 确定所需的任何开发包（例如WCM核心组件）或第三方工具包（例如SAP Hybris）。

1. 将相同的软件包安装到本地开发环境中。

1. 指示您的客户端在其所有QA、暂存和生产服务器上采用相同的配置。 服务器配置不匹配会在部署和测试时造成问题。
