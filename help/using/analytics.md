---
title: Analytics与AEM Screens
description: 了解带Adobe Experience Manager Screens的Adobe Analytics。
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
TQID: https://experienceleague.adobe.com/i7B7E5Kyno2U-ZTxEOPfhrr9W7fqYTWTV5vvcteRicY
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: eb30f47f-d87a-400f-8f78-63ce7979ff56
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 335
ht-degree: 0%

---

# Analytics与AEM Screens {#analytics-screens}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

>[!NOTE]
>
>此活动的典型利益相关者是营销/业务策略师。

AEM Screens可以在本地捕获每个播放器设备运行的每个可跟踪事件。 此数据存储在本地，直到可以上传到云以供处理。 除了所有事件数据外，还会添加设备ID和时间戳。 此功能确保能够区分来自一个播放器的数据与来自另一个播放器的数据。 如果需要，可以单独评估在一天中不同时间运行的数据。

您可能希望捕获此数据有两个基本原因。

第一个涉及&#x200B;**反馈循环和机器学习**，而第二个涉及&#x200B;**创建供人类使用的图形、仪表板和报告**。

在反馈循环用例中，您无需关注可视化报表或功能板，而是希望定义AEM可以执行以进行内容修改的规则。 通过消费和处理特定时间段的所有Screens播放器事件数据，您可以定义一个规则来评估image1与image2的有效性。 通过将销售数据与播放数据相结合，AEM可以确定image1对销售额的影响更大，并自动指示所有播放器使用image1。

使用Analytics的第二个用例是通过报表和仪表板处理播放事件和使用数据以供人类使用。您可以使用此数据创建交互式体验的热图，以确定通过应用程序的首选旅程图。 您还可以选择创建一个仪表板，以图形方式解释使用者与应用程序交互的次数。

