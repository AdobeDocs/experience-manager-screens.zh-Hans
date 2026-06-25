---
title: 数据触发器
description: 了解AEM Screens中的数据触发器。
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
TQID: https://experienceleague.adobe.com/oeJ7C6Rt8-Z9sFnEP1S1tn0VW4PuiKkXkeDYaz8Vd4s
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 307
ht-degree: 0%

---

# 动态Creative优化 {#dynamic-creative}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

>[!NOTE]
>
>此活动的典型利益相关者是AEM实施者。

**Dynamic Creative Optimization**&#x200B;或DCO用于创建数字标牌体验，以反映任何给定位置在任何给定时间以及任何给定用户的独特环境。

此用法也称为内容的客户端拼合。

推理是为了保证每个播放器设备或端点都能够基于各种不同的因素使用数据集来确定要自动播放的最佳内容。

此功能消除了在内容创作时不断人工干预的需求。 它还有助于降低运营网络的总拥有成本，并使数字体验更相关、更符合情境且更有效。

示例包括：

* 使用功能产品的当前库存级别
* 外部温度或天气
* 本地媒体广告活动的存在
* 网络流量，甚至包括本地事件（例如，客户何时拿起产品进行检查）

所有这些示例及更多示例可用于提供更高级别的上下文和个性化。

采用包括DCO的可视化促销策略可以显着增加网络收视率。

有两种主要类型的数据触发器：

* **本地数据触发器**：这些数据触发器是设备上的本地触发器。 例如，如果触摸屏幕，将激活一个传感器，触发本地数据资产或通道开关。
* **远程数据触发器**：这涉及数据触发的通道切换或基于Web服务API返回值的资产切换。
