---
title: 功能包202109的发行说明
description: 请阅读本页以了解2021年9月23日发布的AEM Screens功能包202109的信息。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: b56844c66bfa980013b610523842c7ac0c30f44d
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 2%

---

# 功能包202109的发行说明 {#release-notes-for-feature-pack}

>[!CAUTION]
>建议您升级到最新版本的Adobe Experience Manager(AEM)。 Screens为AEM 6.3 Screens平台提供维护支持。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包9。

您可以从下载适用于AEM Screens 6.5.9版的最新功能包 [软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 用你的Adobe ID。 导航到 **Adobe Experience Manager** 选项卡和搜索 **Screens** 获取最新功能包的标题为 **AEM 6.5 Screens FP9**.

## 发布日期 {#release-date}

AEM Screens功能包202109的发行日期是2021年9月23日。

### 新增功能 {#what-is-new}

* **视频的缩略图支持**

   AEM Screens现在支持缩略图支持中的视频。 内容作者可以为视频定义缩略图，以便图像可用作占位符，并在相应团队最终确定实际视频时，正确测试内容播放和定位。 在视频播放失败时，也可以使用图像。
请参阅 [视频的缩略图支持](/help/user-guide/thumbnail-support.md) 以了解更多详细信息。

* **基本播放监控**

   AEM Screens现在支持基本的播放监控。 现在，播放器将报告各种播放量度，并且每次ping（默认为30秒）。 根据这些量度，它能够检测各种边缘情况（体验卡住、空白屏幕、计划问题等）。 此功能允许团队远程监控播放器是否正确播放了内容，提高对空白屏幕或现场中已损坏体验的反应性，并降低向最终用户显示已损坏体验的风险。
请参阅 [基本播放监控](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/installing-screens-player.html?lang=en#playback-monitoring) 以了解更多详细信息。

* **内容分配报表的更新**

   内容分配报表现在已通过增强的用户体验进行优化和改进。 可下载的报表在一个电子表格选项卡中显示经过改进的播放器相关实体（如位置、显示屏和设备），以及内容提供商信息（如渠道）和其他选项卡中的资产。
请参阅 [内容分配报表](/help/user-guide/content-assignment-report.md) 以了解更多详细信息。

* **自适应演绎版**

   自适应演绎版允许设备根据客户定义的规则自动为设备选择最佳演绎版。

   作为AEM Screens开发人员，您现在可以将特定于设备的资产演绎版配置为自动下载和播放，而无需手动创建所有内容变体。 请参阅 [自适应演绎版：体系结构概述和配置](/help/user-guide/adaptive-renditions.md) 以了解更多详细信息。

   此外，作为AEM Screens内容作者，您还可以在AEM Screens渠道中将资产配置为使用自适应演绎版，并为大型网络迁移设备以使用此功能。 请参阅 [在AEM Screens中使用自适应演绎版](/help/user-guide/using-adaptive-renditions.md) 以了解更多详细信息。

* **支持V3舱单**

   现在，您可以为清单版本v3配置Dispatcher。 要启用v3清单，您需要：

   * 清除作者和已发布中的任何待处理脱机内容作业

      * 在创作和发布中导航到crx/de

      * 单击“工具” — >“查询”

      * 在查询中使用 `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`

      * 这将列出队列中当前正在运行或处于待处理状态的任何脱机内容作业

      * 等待查询不再返回离线内容作业
   * 在 `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`

   * 在 `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`

   * 更新调度程序

   * 更新自定义组件


   * 请参阅 [为清单版本v3配置Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) 以了解更多详细信息。
   * 如果您将自定义组件用作v3清单的一部分，请参阅 [自定义处理程序模板](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers).



### 错误修复 {#bug-fixes}

**播放器端**

* 通过将资产替换为演绎版，解决了文件缓存错误。

* 现在，如果存在演绎版映射，则播放器仅显示资产演绎版。

* 增强了ping功能，以便在响应无效时重新进行身份验证。

* 数字渠道名称/角色会导致屏幕空白。

* 通过SmartSync下载优化的演绎版。

* 将映射转换为演绎版键值列表。

* 删除了对 `cmd.exe` 和 `reg.exe` 在windows播放器中。

* 播放器需要报告其上次成功播放事件。

* 播放器需要报告其播放状态。

* 当 `ALL` 缓存已清除。

* 作为播放器管理员，您现在可以选择播放器名称。

* 从显示中删除渠道分配不会反映在播放器上。

* 如果在下载渠道更新时重新加载播放器，则播放器会忽略更新。

* 嵌入式页面组件现在考虑接触事件。

* 现在支持远程配置Tizen播放器。

**服务器端**

* Target视频未显示
* 向子序列广播显示数据时的争用条件。

* 渠道预览不适用于包含视频的渠道。

* 预览模式显示为空，用于分屏渠道。

* 视频缩略图在启用的自适应演绎版中呈现为空白。

* 如果已发布引用的页面，则会自动更新渠道清单。

* 现在，已删除的设备不会阻止Screens复制队列。

* 清单既不包含目标内容，也不包含嵌入的站点页面。 此问题现已修复。

* 新的核心图像组件现已添加到渠道清单中。

* 现在支持通过SmartSync下载优化的演绎版。

* 为所有资产播放优化的演绎版。

* 添加了对多种内容提供程序类型的支持

* 嵌入式序列播放策略已损坏，现已修复该问题。

* 使用请求参数的脱机清单 `wcmmode` 用于html条目，使其无法执行。

* 空的动态嵌入式序列有时会导致空白屏幕。

* 播放器现在会报告其播放状态。

* 视频正在播放 `Tiny mode` 和不会作为全屏视频在设备上播放，此问题现已修复。

### 已发布AEM Screens播放器 {#released-aem-screens-players}

AEM 6.5功能包9发布了以下AEM Screens播放器：

* ChromeOS
* Windows
* 蒂岑
* Android
* Linux

#### AEM Screens Player下载  {#aem-screens-player-downloads}

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅 **[AEM Screens Player下载](https://download.macromedia.com/screens/index.html)**.
