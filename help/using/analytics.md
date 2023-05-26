---
title: Analytics与AEM Screens
seo-title: Analytics with AEM Screens
description: 本页介绍了Analytics与AEM Screens
seo-description: The page describes the analytics with AEM Screens
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Analytics与AEM Screens {#analytics-screens}

>[!NOTE]
>
>此活动的典型利益相关者是营销/业务策略专家。

AEM Screens提供在本地捕获每个播放器设备执行的每个可跟踪事件的功能。 此数据将存储在本地，直到可以上传到云进行处理。 除了所有事件数据外，还添加了deviceID和时间戳。 这样可以确保来自一个播放器的数据能够与来自另一个播放器的数据区分开，并且可以根据需要单独评估在一天中不同时间执行的数据。

我们可能希望捕获此数据有两个基本原因。

第一个涉及 **反馈循环和机器学习** 第二个涉及 **创建图形、仪表板和报告** 供人类食用。

在反馈循环用例中，我们并不关心可视化报表或功能板，而是希望定义AEM可以执行以进行内容修改的规则。 通过消费和处理特定时间段的所有Screens播放器事件数据，我们可以定义一个规则来评估image1与image2的有效性。 通过将销售数据与播放数据相结合，AEM可以确定image1对销售的影响更大，并自动指示所有播放器使用image1。

使用Analytics的第二个用例是通过报表和仪表板处理播放事件和使用数据以供人类使用。
我们可能会使用此数据来创建交互式体验的热图，以确定通过我们的应用程序的首选旅程图。 我们还可以选择创建一个功能板，该功能板以图形方式呈现用户与我们的应用程序进行交互的次数。
