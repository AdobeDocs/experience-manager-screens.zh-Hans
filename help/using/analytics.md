---
title: AEM Screens分析
seo-title: AEM Screens分析
description: 本页介绍Analytics与AEM Screens
seo-description: 本页描述了与AEM Screens的分析
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# AEM Screens分析{#analytics-screens}

>[!NOTE]
>
>本活动的典型利益相关方是营销／业务策略师。

AEM Screens优惠能够本地捕获每个播放器设备执行的每个可跟踪事件。 此数据将本地存储，直到可上传到云进行处理。 除了所有事件数据之外，还添加了deviceID和时间戳。 这确保来自一个播放器的数据可以与另一个播放器区分开来，并且如果需要，可以单独评估在一天的不同时间执行的数据。

我们可能希望捕获此数据有两个基本原因。

第一个涉及&#x200B;**反馈循环和机器学习**，第二个涉及创建用于人类消费的图形、仪表板和报告&#x200B;**。**

在反馈循环用例中，我们不关心可视报告或仪表板，而是想定义AEM可执行的规则以进行内容修改。 通过使用和处理某个时间段内所有Screens播放器的事件数据，我们可以定义一个规则来评估image1与image2的有效性。 通过将销售数据与回放数据相结合，AEM可确定image1对销售的影响要大得多，并自动指示所有玩家使用image1。

第二个使用分析的用例是通过报告和仪表板处理回放事件和使用数据以供人类使用。
我们可能会使用这些数据创建交互式体验的热点地图，从而确定通过我们的应用程序的首选旅程地图。 我们还可以选择创建仪表板，以图形方式解释消费者与我们的应用程序交互的次数。

