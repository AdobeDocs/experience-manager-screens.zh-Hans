---
title: 安装 Screens 播放器
description: 了解如何正确安装AEM Screens Player。
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 1%

---

# 安装AEM Screens Player {#installing-player}

本页介绍如何安装AEM Screens播放器。

## 可用的Screens播放器 {#available-players}

AEM Screens播放器适用于Android™、Chrome OS和Windows。

下载 **AEM Screens Player**，请访问 [AEM 6.5播放器下载](https://download.macromedia.com/screens/) 页面。

>[!NOTE]
>
>下载最新播放器后(*.exe*)，按照播放器上的步骤操作，以完成临时安装：
>
>1. 长按左上角以打开管理面板。
>1. 导航到 **配置** 从左侧操作菜单中，输入AEM实例的位置地址 **服务器** 并选择 **保存**.
>1. 选择 **注册** 左侧操作菜单中的链接以及完成设备注册过程的以下步骤。

## 基本回放监控 {#playback-monitoring}

播放器报告各种回放量度，每种 `ping` 默认为30秒。 基于这些量度，它可以检测各种边缘情况，例如卡住体验、空白屏幕和计划问题。 这有助于我们了解并排除设备上的问题，从而加快与您开展的调查和纠正措施。

AEM Screens播放器中的基本回放监控允许您执行以下操作：

* 远程监控（如果播放器正在正确播放内容）。

* 改善对空白屏幕或现场中断体验的反应性。

* 降低向最终用户显示中断体验的风险。

### 了解属性 {#understand-properties}

每个报表包中包含以下属性 `ping`：

| 属性 | 描述 |
|---|---|
| id {string} | 播放器标识符 |
| activeChannel {string} | 当前播放渠道路径，如果未计划任何内容，则返回null |
| activeElements {string} | 以逗号分隔的字符串，当前在所有播放序列渠道中可见的元素（多区域布局） |
| isDefaultContent {boolean} | 如果播放频道被视为默认或备用频道（即，优先级为1且无计划），则返回true |
| hasContentChange {boolean} | 如果内容在过去5分钟内发生更改，则返回true；否则返回false |
| lastContentChange {string} | 上次内容更改的时间戳 |

>[!NOTE]
>或者，也可以从播放器首选项（启用回放监控）启用更高级的属性，即：
>
>| 属性 | 描述 |
>|---|---|
>| isContentRendering {boolean} | 如果GPU可以确认它正在播放实际内容（基于像素分析），则为true |

### 限制 {#limitations}

下面列出了基本回放监视的一些限制：

* 播放器会向服务器报告自身的播放状态，因此需要活动连接。

* 此 `isContentRendering` 用于检查GPU的属性占用太多资源，默认情况下无法启用，并且需要从播放器首选项中明确选择加入。 Adobe建议您不要将其用于生产中的视频。

* 仅序列渠道支持此功能，并且尚不涵盖交互式渠道(SPA)用例。

* 这些量度尚未完全向客户公开，Adobe正在努力尽快启用类似功能板的报告和警报机制。

### 其他资源 {#additional-resources}

有关深入信息，请参阅以下主题：

* 要下载Android™ Player，请访问 **Google Play**. 要了解如何实施Android™ Watchdog，请参阅 [实施Android™播放器](implementing-android-player.md).

* 要实施Chrome操作系统播放器，请参阅 [Chrome管理控制台](implementing-chrome-os-player.md) 以了解更多信息。

* 要配置AEM Screens Windows Player，请参阅 [实施Windows Player](implementing-windows-player.md).
