---
title: 功能包202109的发行说明
description: 关注此页面以获取2021年9月23日发布的AEM Screens Feature Pack 202109的信息。
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
>建议您升级到最新版本的Adobe Experience Manager (AEM)。 Screens提供对AEM 6.3 Screens平台的维护支持。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包9。

您可以从以下网站下载AEM Screens 6.5.9版本的最新功能包： [软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。 导航到 **Adobe Experience Manager** 选项卡和搜索 **Screens** 获取最新的功能包，标题为 **AEM 6.5屏幕FP9**.

## 发布日期 {#release-date}

AEM Screens功能包202109的发布日期是2021年9月23日。

### 新增功能 {#what-is-new}

* **视频的缩略图支持**

   AEM Screens现在支持视频缩略图。 内容作者可以定义视频的缩略图，以便在适当的团队最终确定实际视频的同时，将图像用作占位符并正确测试内容播放和定位。 在视频播放失败时，也可以使用该图像。
参见 [视频的缩略图支持](/help/user-guide/thumbnail-support.md) 了解更多详细信息。

* **基本回放监控**

   AEM Screens现在支持基本回放监控。 播放器现在将报告每次ping（默认为30秒）的各种播放量度。 基于量度，它提供检测各种边缘情况（卡住体验、空白屏幕、计划问题等）的能力。 此功能允许团队远程监控播放器是否正确播放内容，改善对空白屏幕或现场中断体验的反应性，并降低向最终用户显示中断体验的风险。
参见 [基本回放监控](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/installing-screens-player.html?lang=en#playback-monitoring) 了解更多详细信息。

* **内容分配报告的更新**

   内容分配报表现已通过增强的用户体验得到优化和改进。 可下载的报表在一个电子表格选项卡中显示改进的播放器相关实体（如位置、显示器和设备），并在其他选项卡中显示内容提供商信息（如渠道和资产）。
参见 [内容分配报表](/help/user-guide/content-assignment-report.md) 了解更多详细信息。

* **自适应演绎版**

   自适应呈现版本允许设备根据客户定义的规则自动为设备选择最佳呈现版本。

   作为AEM Screens开发人员，您现在可以将特定于设备的资源演绎版配置为自动下载和播放，而无需手动创建所有内容变体。 参见 [自适应演绎版：架构概述和配置](/help/user-guide/adaptive-renditions.md) 了解更多详细信息。

   此外，作为AEM Screens内容作者，您可以配置资源以使用自适应演绎版，还可以在AEM Screens渠道中为大型网络迁移设备以使用此功能。 参见 [在AEM Screens中使用自适应演绎版](/help/user-guide/using-adaptive-renditions.md) 了解更多详细信息。

* **支持V3清单**

   您现在可以为清单版本v3配置Dispatcher。 要启用v3清单，您需要：

   * 清除创作和已发布中的任何待处理脱机内容作业

      * 在创作和发布中导航到crx/de

      * 单击“工具” — >“查询”

      * 在查询中使用 `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`

      * 这将列出队列中当前正在运行或挂起的任何离线内容作业

      * 等到查询中不再返回离线内容作业为止
   * 在中禁用ContentSync `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`

   * 在中启用SmartSync `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`

   * 更新调度程序

   * 更新自定义组件


   * 参见 [为清单版本v3配置Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) 了解更多详细信息。
   * 如果您在v3清单中使用自定义组件，请参阅 [自定义处理程序的模板](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers).



### 错误修复 {#bug-fixes}

**播放器端**

* 通过将资源替换为演绎版解决了文件缓存错误。

* 播放器现在仅在存在演绎版映射时公开资产演绎版。

* 增强了Ping功能，可在响应无效JSON时重新进行身份验证。

* 数字渠道名称/角色导致出现空白屏幕。

* 通过SmartSync下载优化的演绎版。

* 已将映射转换为演绎版密钥列表。

* 已移除对的访问权限 `cmd.exe` 和 `reg.exe` 在windows player中。

* 播放器需要报告其上一个成功播放事件。

* 播放器需要报告其播放状态。

* 播放器在以下情况下不会重新下载资产： `ALL` 缓存已清除。

* 作为播放器管理员，您现在可以选择播放器名称。

* 从显示区中删除渠道分配不会反映在播放器中。

* 如果在下载渠道更新时重新加载播放器，则播放器会忽略更新。

* 现在，嵌入页面组件会考虑触摸事件。

* 现在支持远程配置Tizen播放器。

**服务器端**

* 目标视频未显示
* 将显示数据广播到子序列的竞争条件。

* 渠道预览不适用于包含视频的渠道。

* 分屏渠道的预览模式显示为空白。

* 启用自适应呈现后，视频缩略图会渲染为空白。

* 如果引用的页面已发布，则自动更新渠道清单。

* 已删除的设备现在不会阻止Screens复制队列。

* 清单中不包含目标内容或站点嵌入页面。 现已修复此问题。

* 新的核心图像组件现已添加到渠道清单中。

* 现在支持通过SmartSync下载优化的演绎版。

* 播放所有资源的优化演绎版。

* 添加了对多种内容提供程序类型的支持

* 嵌入式序列播放策略已损坏，现已修复该问题。

* 使用请求参数的脱机清单 `wcmmode` 对于html条目，使其不可缓存。

* 空的动态嵌入式序列有时会导致空白屏幕。

* 播放器现在报告其播放状态。

* 正在播放视频 `Tiny mode` 而不是作为全屏视频在设备上播放，此问题现已修复。

### 已发布的AEM Screens Players {#released-aem-screens-players}

已为AEM 6.5 Feature Pack 9发布以下AEM Screens Player：

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### AEM Screens播放器下载  {#aem-screens-player-downloads}

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅 **[AEM Screens播放器下载](https://download.macromedia.com/screens/index.html)**.
