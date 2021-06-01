---
title: Analytics与AEM Screens
seo-title: Analytics与AEM Screens
description: 本页介绍Analytics与AEM Screens
seo-description: 本页介绍使用AEM Screens分析
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# 具有AEM Screens的Analytics {#analytics-screens}

>[!NOTE]
>
>此活动的典型利益相关方是营销/业务策略师。

AEM Screens提供在本地捕获每个播放器设备执行的每个可跟踪事件的功能。 此数据将存储在本地，直到其上传到云进行处理。 除了所有事件数据之外，还添加了deviceID和时间戳。 这可确保将一个播放器中的数据与另一个播放器进行区分，并且如果需要，可以单独评估一天中不同时间执行的数据。

可能需要捕获此数据有两个基本原因。

第一个包括&#x200B;**反馈循环和机器学习**，第二个包括&#x200B;**创建图形、功能板和报表**，供人们使用。

在反馈循环用例中，我们并不关心可视报表或功能板，而是希望定义AEM可对其执行的规则以进行修改内容。 通过使用和处理特定时间段内的所有Screens播放器事件数据，我们可以定义一个规则来评估image1与image2的有效性。 通过将销售数据与播放数据相结合，AEM可能会确定image1对销售的影响要大得多，并会自动指示所有播放器使用image1。

使用分析的第二个用例是通过报表和功能板处理播放事件和使用数据，以供人们使用。
我们可以使用此数据创建交互式体验的热图，以确定通过我们的应用程序的首选历程图。 我们还可以选择创建一个功能板，以图形方式解释消费者与我们的应用程序交互的次数。

