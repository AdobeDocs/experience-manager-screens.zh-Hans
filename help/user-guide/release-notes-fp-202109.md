---
title: 功能包202109的发行说明
description: 请阅读本页以了解2021年9月23日发布的AEM Screens功能包202105的信息。
feature: Feature Pack
role: Developer
level: Intermediate
index: false
source-git-commit: c6506ca62e806ec11d3380d6ac7670bcfcf13adb
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 2%

---

# 功能包202109的发行说明 {#release-notes-for-feature-pack}

>[!CAUTION]
>建议您升级到最新版本的Adobe Experience Manager(AEM)。 Screens为AEM 6.3 Screens平台提供维护支持。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包9。

您可以使用Adobe ID从[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载AEM Screens 6.5.9版的最新功能包。 导航到&#x200B;**Adobe Experience Manager**&#x200B;选项卡并搜索&#x200B;**Screens**&#x200B;以获取标题为&#x200B;**AEM 6.5 Screens FP9**&#x200B;的最新功能包。

## 发布日期 {#release-date}

AEM Screens功能包202109的发行日期是2021年9月23日。

### 新增功能 {#what-is-new}

* **视频的缩略图支持**

   AEM Screens现在支持缩略图支持中的视频。 内容作者可以为视频定义缩略图，以便图像可用作占位符，并在相应团队最终确定实际视频时，正确测试内容播放和定位。 在视频播放失败时，也可以使用图像。
有关更多详细信息，请参阅视频的缩略图支持。

* **基本播放监控**

   AEM Screens现在支持基本的播放监控。 现在，播放器将报告各种播放量度，并且每次ping（默认为30秒）。 根据这些量度，它能够检测各种边缘情况（体验卡住、空白屏幕、计划问题等）。 此功能允许团队远程监控播放器是否正确播放了内容，提高对空白屏幕或现场中已损坏体验的反应性，并降低向最终用户显示已损坏体验的风险。
有关更多详细信息，请参阅基本播放监控。

* **内容分配报表的更新**

   内容分配报表现在已通过增强的用户体验进行优化和改进。 可下载的报表在一个电子表格选项卡中显示经过改进的播放器相关实体（如位置、显示屏和设备），以及内容提供商信息（如渠道）和其他选项卡中的资产。

* **支持V3舱单**

   现在，您可以为清单版本v3配置Dispatcher。 有关更多详细信息，请参阅[为清单版本配置Dispatcher v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) 。
此外，如果您将自定义组件用作v3清单的一部分，请参阅[自定义处理程序的模板](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers)。


### 错误修复 {#bug-fixes}

**播放器端**

* 通过将资产替换为演绎版，解决了文件缓存错误。

* 现在，如果存在演绎版映射，则播放器仅显示资产演绎版。

* 您现在可以根据Splunk日志设置Slack警报。

* 增强ping功能，以便在响应无效的JSON时重新进行身份验证。

* 数字渠道名称/角色会导致屏幕空白。

* 通过SmartSync下载优化的演绎版。

* 将映射转换为演绎版键值列表。

* 删除对Windows播放器中cmd.exe和reg.exe的访问权限。

* 限制csrf令牌调用。

* 播放器需要报告其上次成功播放事件。

* 播放器需要报告其播放状态。

* 清除`ALL`缓存后，播放器不会重新下载资产。

* 作为播放器管理员，您现在可以选择播放器名称。

* 从显示中删除渠道分配不会反映在播放器上。

* 如果在下载渠道更新时重新加载播放器，则播放器会忽略更新。

* 嵌入的页面组件不考虑接触事件。

* 现在支持远程配置Tizen播放器。

**服务器端**

* Target视频未显示
* 向子序列广播显示数据时的争用条件。

* 渠道预览不适用于包含视频的渠道。

* 预览模式显示为空，用于分屏渠道。

* 视频缩略图在启用的自适应演绎版中呈现为空白。

* 如果已发布引用的页面，则会自动更新渠道清单。

* 渠道JSON不包括自定义渠道(#942)

* 现在，已删除的设备不会阻止Screens复制队列。

* 清单不包含目标内容或站点嵌入页面。

* 未将新的核心图像组件添加到渠道清单。

* 现在支持通过SmartSync下载优化的演绎版。

* 为所有资产播放优化的演绎版。

* 添加了对多种内容提供程序类型的支持

* 嵌入式序列播放策略已损坏，现已修复该问题。

* 使用请求参数`wcmmode`获取html条目的脱机清单，使其无法执行。

* 空的动态嵌入式序列有时会导致空白屏幕。

* 播放器需要报告其播放状态。

* 视频在`Tiny mode`中播放，而不在设备上以全屏视频形式播放。

* OSGi密码显示为纯文本。


### 已发布AEM Screens播放器 {#released-aem-screens-players}

AEM 6.5功能包9发布了以下AEM Screens播放器：

* ChromeOS
* Windows
* 蒂岑
* Android
* Linux

#### AEM Screens Player下载  {#aem-screens-player-downloads}

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅&#x200B;**[AEM Screens播放器下载](https://download.macromedia.com/screens/index.html)**。
