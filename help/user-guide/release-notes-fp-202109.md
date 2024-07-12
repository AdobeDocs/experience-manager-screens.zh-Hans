---
title: 功能包202109发行说明
description: 了解2021年9月23日发布的AEM Screens功能包202109。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 1%

---

# 功能包202109发行说明 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe建议您升级到Adobe Experience Manager (AEM)的最新版本。 AEM Screens提供了对AEM 6.3 Screens平台的维护支持。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包9。

您可以使用您的Adobe ID从[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载AEM Screens 6.5.9版本的最新功能包。 导航到&#x200B;**Adobe Experience Manager**&#x200B;选项卡并搜索&#x200B;**Screens**，以获取标题为&#x200B;**AEM 6.5 Screens FP9**&#x200B;的最新功能包。

## 发布日期 {#release-date}

AEM Screens功能包202109的发布日期为2021年9月23日。

### 新增功能 {#what-is-new}

* 视频支持&#x200B;**缩略图**

  AEM Screens现在支持视频缩略图。 内容作者为视频定义缩略图，这样该图像就可以用作占位符。 他们还正确测试内容播放和定位，而相应的团队会最终确定实际视频。 在视频播放失败时，也可以使用该图像。
有关更多详细信息，请参阅[视频的缩略图支持](/help/user-guide/thumbnail-support.md)。

* **基本回放监控**

  AEM Screens现在支持基本回放监控。 播放器现在报告每次ping（默认为30秒）的各种回放指标。 它会根据量度检测各种边缘情况（卡住体验、空白屏幕、计划问题等）。 团队可以使用此功能远程监控播放器是否正确播放内容，并改善对空白屏幕或现场中断体验的反应性。 它还降低了向最终用户显示中断体验的风险。
有关更多详细信息，请参阅[基本回放监控](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/installing-screens-player#playback-monitoring)。

* **内容分配报告的更新**

  内容分配报表现已通过增强的用户体验得到优化和改进。 可下载的报告显示了经过改进的播放器相关实体。 此类实体在一个电子表格选项卡中包括位置、显示器和设备。 它还包括内容提供商信息，例如其他选项卡中的渠道和资产。
有关更多详细信息，请参阅[内容分配报告](/help/user-guide/content-assignment-report.md)。

* **自适应演绎版**

  自适应演绎版允许设备根据客户定义的规则自动单击设备的最佳演绎版。

  作为AEM Screens开发人员，您现在可以将特定于设备的资源呈现配置为自动下载和播放，而无需手动创建所有内容变体。 有关更多详细信息，请参阅[自适应演绎版：架构概述和配置](/help/user-guide/adaptive-renditions.md)。

  此外，作为AEM Screens内容作者，您可以配置资源以使用自适应演绎版。 您还可以为大型网络迁移设备，以便在AEM Screens渠道中使用此功能。 有关详细信息，请参阅[在AEM Screens中使用自适应演绎版](/help/user-guide/using-adaptive-renditions.md)。

* **支持V3清单**

  您现在可以为清单版本v3配置Dispatcher。 要启用v3清单，请执行以下操作：

   * 清除创作和已发布中的任何待处理脱机内容作业。

      * 在创作和Publish中导航到CRXDE Lite。

      * 单击“工具”>“查询”。

      * 在查询中使用`/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`。

      * 这将列出队列中当前正在运行或挂起的脱机内容作业。

      * 请等待，直到不再从查询返回离线内容作业。

   * 在`/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`中禁用ContentSync。

   * 在`/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`中启用SmartSync。

   * 更新Dispatcher。

   * 更新自定义组件。


   * 有关更多详细信息，请参阅[为清单版本v3](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3)配置Dispatcher 。
   * 如果您将自定义组件用作v3清单的一部分，请参阅[自定义处理程序模板](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers)。


### 错误修复 {#bug-fixes}

**播放器端**

* 通过将资源替换为演绎版解决了文件缓存错误。

* 现在，如果存在演绎版映射，则播放器仅公开资产演绎版。

* 增强了ping功能，可在响应无效JSON时重新进行身份验证。

* 数字渠道名称/角色导致屏幕空白。

* 通过SmartSync下载优化的演绎版。

* 已将映射转换为演绎版密钥列表。

* 已删除对Windows Player中`cmd.exe`和`reg.exe`的访问权限。

* 播放器必须报告其上一个成功播放事件。

* 播放器必须报告其播放状态。

* 清除`ALL`缓存后，播放器不会重新下载Assets。

* 作为播放器管理员，您现在可以选择播放器名称。

* 从显示区中删除渠道分配不会反映在播放器中。

* 如果在下载渠道更新时重新加载播放器，则播放器会忽略更新。

* 现在，嵌入的页面组件采用触摸事件。

* 现在支持远程配置Tizen播放器。

**服务器端**

* 目标视频未显示
* 将显示数据广播到子序列的竞争条件。

* 渠道预览不适用于包含视频的渠道。

* 分屏渠道的预览模式显示为空白。

* 启用自适应呈现形式的视频缩略图呈现为空白。

* 如果引用的页面已发布，则自动更新渠道清单。

* 现在，已删除的设备不会阻止Screens复制队列。

* 清单不包含目标内容或站点嵌入页面。 此错误现已修复。

* 现在，新的核心图像组件已添加到渠道清单中。

* 现在支持通过SmartSync下载优化的演绎版。

* 播放所有资源的优化演绎版。

* 添加了对多种内容提供程序类型的支持

* 嵌入式序列播放策略已损坏，此错误现已修复。

* 脱机清单使用用于html条目的请求参数`wcmmode`，使其不可缓存。

* 空的动态嵌入序列有时会导致出现空白屏幕。

* 播放器现在会报告其播放状态。

* 视频已在`Tiny mode`中播放，未作为全屏视频在设备上播放，此问题现已修复。

### 已发布的AEM Screens Players

已为AEM 6.5 Feature Pack 9发布以下AEM Screens Player：

* Chrome OS
* Windows
* Tizen
* Android™
* Linux®

#### AEM Screens播放器下载

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅&#x200B;**[AEM Screens播放器下载](https://download.macromedia.com/screens/index.html)**。
