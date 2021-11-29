---
title: 功能包202105的发行说明
description: “请阅读本页以了解2021年6月4日发布的AEM Screens功能包202105的信息。”
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 02bc399d61f5666918caad9fce3d69d63f0782d7
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 11%

---

# 功能包202105的发行说明 {#release-notes-for-feature-pack}

>[!CAUTION]
>建议您升级到最新版本的Adobe Experience Manager(AEM)。 Screens为AEM 6.3 Screens平台提供维护支持。

## 可用性 {#availability}

AEM Screens发布了AEM 6.5功能包8。

您可以从下载适用于AEM Screens 6.5.8版的最新功能包 [软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 用你的Adobe ID。 导航到 **Adobe Experience Manager** 选项卡和搜索 **Screens** 获取最新功能包的标题为 **AEM 6.5 Screens FP8**.

>[!IMPORTANT]
>安装包后，必须安装AMS连接器的最低版本AEM 6.5 Feature Pack 8才能正常工作 `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16` 和 `screens core bundles`.

## 发布日期 {#release-date}

AEM Screens功能包202105的发布日期是2021年6月4日。

### 新增功能 {#what-is-new}

* **锁定AEM Screens渠道中的页面**

   AEM Screens现在支持 *锁定页面*，已在AEM Sites中实施。 Adobe Experience Manager(AEM)允许您锁定页面，这样其他人就无法修改页面内容。 当您要对某个特定页面做出大量编辑，或者需要冻结页面一段时间时，此功能非常有用。

* **命名AEM Screens播放器设备**

   AEM Screens播放器现在包含向Adobe Experience Manager(AEM)发送设备名称的功能。
默认情况下，使用批量注册注册来注册设备时，系统会在标题字段中输入系统生成的用户名。 作为替代方法，客户可能使用资产标记或其他友好名称，以便在AEM中可见资产标记，并且更便于分配相应内容。

   请参阅以下文档，了解如何在每个受支持的操作系统中配置名称：

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [蒂岑](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome OS](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **清单生成**

   更快地生成通道清单，并改善性能，例如在服务器上分配更少的资源。

### 错误修复 {#bug-fixes}

* 播放器在切换到包含动态嵌入式序列的渠道时显示黑屏。
* Screens播放器现在会阻止切换到任何损坏的渠道，从而进一步避免404错误或出现错误消息的页面。

### 已发布AEM Screens播放器 {#released-aem-screens-players}

为AEM 6.5功能包8发布了以下AEM Screens播放器：

* ChromeOS
* Windows
* 蒂岑
* Android
* Linux

#### AEM Screens Player下载  {#aem-screens-player-downloads}

要下载最新的AEM Screens播放器并了解有关错误修复的更多信息，请参阅 **[AEM Screens Player下载](https://download.macromedia.com/screens/index.html)**.
