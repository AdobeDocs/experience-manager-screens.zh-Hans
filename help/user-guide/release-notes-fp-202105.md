---
title: 功能包202105发行说明
description: 了解2021年6月4日发布的AEM Screens功能包202105。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 3%

---

# 功能包202105发行说明 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe建议您升级到Adobe Experience Manager (AEM)的最新版本。 AEM Screens提供了对AEM 6.3 Screens平台的维护支持。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包8。

您可以使用您的Adobe ID从[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载AEM Screens 6.5.8版本的最新功能包。 导航到&#x200B;**Adobe Experience Manager**&#x200B;选项卡并搜索&#x200B;**Screens**，以获取标题为&#x200B;**AEM 6.5 Screens FP8**&#x200B;的最新功能包。

>[!IMPORTANT]
>安装AEM 6.5 Feature Pack 8的最低版本，以便在安装包`screens-cloud-ams-pkg-0.0.20`、`screens-cloud-ams-pkg-0.0.16`和`screens core bundles`之后使AMS连接器正常工作。

## 发布日期 {#release-date}

AEM Screens功能包202105的发布日期是2021年6月4日。

### 新增功能 {#what-is-new}

* **在AEM Screens渠道中锁定页面**

  AEM Screens现在支持&#x200B;*锁定页面*，如已在AEM Sites中实施的那样。 Adobe Experience Manager (AEM)允许您锁定页面，这样其他人就无法编辑其内容。 当您对一个特定页面进行大量编辑时，或者当您必须冻结页面一段时间时，此功能非常有用。

* **命名AEM Screens Player设备**

  AEM Screens播放器现在包括向Adobe Experience Manager (AEM)发送设备名称的功能。
默认情况下，当使用批量注册来注册设备时，系统生成的用户名会输入到标题字段中。 作为替代方法，客户可以使用资源标记或其他友好名称，以便在AEM中可见且更易于分配适当的内容。

  有关如何在每个支持的操作系统中配置名称的信息，请参阅以下文档：

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome操作系统](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **清单生成**

  通过改进的性能（如在服务器上分配更少的资源）加快通道清单的生成。

### 错误修复 {#bug-fixes}

* 当切换到包含动态嵌入序列的频道时，播放器显示黑屏。
* Screens播放器现在阻止切换到任何中断的频道，这进一步避免了404错误或带有错误消息的页面。

### 已发布的AEM Screens Players

已为AEM 6.5 Feature Pack 8发布以下AEM Screens Player：

* Chrome OS
* Windows
* Tizen
* Android™
* Linux®

#### AEM Screens播放器下载

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅&#x200B;**[AEM Screens播放器下载](https://download.macromedia.com/screens/index.html)**。
