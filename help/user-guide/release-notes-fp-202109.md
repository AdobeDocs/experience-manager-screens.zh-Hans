---
title: 功能包202109的发行说明
description: “请阅读本页以了解2021年9月22日发布的AEM Screens功能包202105的相关信息。”
feature: Feature Pack
role: Developer
level: Intermediate
index: false
source-git-commit: 33e71d5d9b02036aa91db093274dcb058769f288
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 4%

---

# 功能包202109的发行说明 {#release-notes-for-feature-pack}

>[!CAUTION]
>建议您升级到最新版本的Adobe Experience Manager(AEM)。 Screens为AEM 6.3 Screens平台提供维护支持。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包9。

您可以使用Adobe ID从[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载AEM Screens 6.5.9版的最新功能包。 导航到&#x200B;**Adobe Experience Manager**&#x200B;选项卡并搜索&#x200B;**Screens**&#x200B;以获取标题为&#x200B;**AEM 6.5 Screens FP9**&#x200B;的最新功能包。

## 发布日期 {#release-date}

AEM Screens功能包202109的发行日期是2021年9月9日。

### 新增功能 {#what-is-new}

* **视频的缩略图支持**

   AEM Screens现在支持缩略图支持中的视频。 内容作者可以为视频定义缩略图，以便图像可用作占位符，并在相应团队最终确定实际视频时，正确测试内容播放和定位。 在视频播放失败时，也可以使用图像。
有关更多详细信息，请参阅视频的缩略图支持。

* **基本播放监控**

   AEM Screens现在支持基本的播放监控。 现在，播放器将报告各种播放量度，并且每次ping（默认为30秒）。 根据这些量度，它能够检测各种边缘情况（体验卡住、空白屏幕、计划问题等）。 此功能允许团队远程监控播放器是否正确播放了内容，提高对空白屏幕或现场中已损坏体验的反应性，并降低向最终用户显示已损坏体验的风险。
有关更多详细信息，请参阅基本播放监控。

* **内容分配报表的更新**

* **支持V3舱单**

   现在，您可以为清单版本v3配置Dispatcher。 有关更多详细信息，请参阅[为清单版本配置Dispatcher v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) 。
此外，如果您将自定义组件用作v3清单的一部分，请参阅[自定义处理程序的模板](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers)。


### 错误修复 {#bug-fixes}



### 已发布AEM Screens播放器 {#released-aem-screens-players}

为AEM 6.5功能包8发布了以下AEM Screens播放器：

* ChromeOS
* Windows
* 蒂岑
* Android
* Linux

#### AEM Screens Player下载  {#aem-screens-player-downloads}

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅&#x200B;**[AEM Screens播放器下载](https://download.macromedia.com/screens/index.html)**。
