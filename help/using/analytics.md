---
title: Analytics与AEM Screens
description: 了解带Adobe Experience Manager Screens的Adobe Analytics。
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Analytics与AEM Screens {#analytics-screens}

>[!NOTE]
>
>此活动的典型利益相关者是营销/业务策略师。

AEM Screens可以在本地捕获每个播放器设备运行的每个可跟踪事件。 此数据存储在本地，直到可以上传到云以供处理。 除了所有事件数据外，还会添加设备ID和时间戳。 此功能确保能够区分来自一个播放器的数据与来自另一个播放器的数据。 如果需要，可以单独评估在一天中不同时间运行的数据。

您可能希望捕获此数据有两个基本原因。

第一个涉及&#x200B;**反馈循环和机器学习**，而第二个涉及&#x200B;**创建供人类使用的图形、仪表板和报告**。

在反馈循环用例中，您无需关注可视化报表或功能板，而是希望定义AEM可以执行以进行内容修改的规则。 通过消费和处理特定时间段的所有Screens播放器事件数据，您可以定义一个规则来评估image1与image2的有效性。 通过将销售数据与播放数据相结合，AEM可以确定image1对销售的影响更大，并自动指示所有播放器使用image1。

使用Analytics的第二个用例是通过报表和仪表板处理播放事件和使用数据以供人类使用。
您可以使用此数据创建交互式体验的热图，以确定通过应用程序的首选旅程图。 您还可以选择创建一个仪表板，以图形方式解释使用者与应用程序交互的次数。
