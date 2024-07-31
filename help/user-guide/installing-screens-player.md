---
title: 安装 Screens 播放器
description: 了解如何正确安装AEM Screens Player。
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: 33c469477fc38e79e0364411378c9a3a30a1eda3
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 1%

---

# 安装AEM Screens Player {#installing-player}

本页介绍如何安装AEM Screens Player。

## 可用的Screens Player {#available-players}

AEM Screens Player适用于Android™、Chrome操作系统和Windows。

要下载&#x200B;**AEM Screens播放器**，请访问[AEM 6.5播放器下载](https://download.macromedia.com/screens/)页面。

>[!NOTE]
>
>下载最新的播放器(*.exe*)后，请按照播放器上的步骤操作，以便完成临时安装：
>
>1. 长按左上角以打开管理面板。
>1. 从左侧操作菜单中导航到&#x200B;**配置**，输入&#x200B;**服务器**&#x200B;中AEM实例的位置地址，然后单击&#x200B;**保存**。
>1. 单击左侧操作菜单中的&#x200B;**注册**&#x200B;链接及以下步骤以完成设备注册过程。

## 基本回放监控 {#playback-monitoring}

播放器报告每个`ping`的各种回放指标，其默认值为30秒。 基于这些量度，它可以检测各种边缘情况，例如卡住体验、空白屏幕和计划问题。 它让我们能够了解并排除设备上的问题，从而为您加快调查和纠正措施。

AEM Screens Player中的基本回放监控允许您执行以下操作：

* 远程监控（如果播放器正在正确播放内容）。

* 改善对空白屏幕或现场中断体验的反应性。

* 降低向最终用户显示中断体验的风险。

### 了解属性 {#understand-properties}

每个`ping`中包含以下属性：

| 属性 | 描述 |
|---|---|
| ID {string} | 播放器标识符 |
| activeChannel {string} | 当前播放渠道路径，如果未计划任何内容，则返回null |
| activeElements {string} | 以逗号分隔的字符串，当前在所有播放序列渠道中可见的元素（多区域布局） |
| isDefaultContent {boolean} | 如果播放频道被视为默认或备用频道（即，优先级为1且无计划），则返回true |
| hasContentChanged {boolean} | 如果内容在过去5分钟内发生更改，则返回true；否则返回false |
| lastContentChange {string} | 上次内容更改的时间戳 |

>[!NOTE]
>
>或者，也可以从播放器首选项（启用回放监控）启用更高级的属性，即：
>
>| 属性 | 描述 |
>|---|---|
>| isContentRendering {boolean} | 如果GPU可以确认它正在播放实际内容（基于像素分析），则为true |

### 限制 {#limitations}

下面列出了基本回放监视的一些限制：

* 播放器会向服务器报告自身的播放状态，因此需要活动连接。

* 检查GPU的`isContentRendering`属性在默认情况下要启用更多的资源消耗，并且需要从播放器首选项中明确选择加入。 Adobe建议您不要将其用于生产中的视频。

* 仅序列渠道支持此功能，并且尚不涵盖交互式渠道(SPA)用例。

* 这些量度尚未完全向客户公开，但Adobe正在努力尽快启用类似功能板的报告和警报机制。

### 其他资源 {#additional-resources}

有关深入信息，请参阅以下主题：

* 要下载Android™ Player，请访问&#x200B;**Google Play**。 要了解如何实施Android™ Watchdog，请参阅[实施Android™播放器](implementing-android-player.md)。

* 要实施Chrome OS Player，请参阅[Chrome管理控制台](implementing-chrome-os-player.md)以了解更多信息。

* 要配置AEM Screens Windows Player，请参阅[实施Windows Player](implementing-windows-player.md)。
