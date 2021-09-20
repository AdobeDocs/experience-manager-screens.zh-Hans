---
title: 安装Screens播放器
seo-title: Installing Screens Player
description: 请阅读本页，了解如何安装可用的AEM Screens Player。
seo-description: Installing Screens Player
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: c6506ca62e806ec11d3380d6ac7670bcfcf13adb
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# 安装AEM Screens Player {#installing-player}

本页介绍如何安装AEM Screens播放器。

## 可用屏幕播放器 {#available-players}

AEM Screens播放器适用于Android、Chrome OS和Windows。

要下载&#x200B;**AEM Screens Player**，请访问[AEM 6.5 Player下载](https://download.macromedia.com/screens/)页面。

>[!NOTE]
>
>下载最新的播放器(*.exe*)后，请按照播放器中的步骤完成临时安装：
>
>1. 长按左上角以打开管理面板。
>1. 从左侧操作菜单导航到&#x200B;**Configuration** ，在&#x200B;**Server**&#x200B;中输入AEM实例的位置地址，然后单击&#x200B;**Save**。
>1. 单击左侧操作菜单中的&#x200B;**Registration**&#x200B;链接和以下步骤以完成设备注册过程。


## 基本播放监控 {#playback-monitoring}

播放器会报告各种播放量度，每个量度的默认值为30秒。 `ping`根据这些量度，我们可以检测各种边缘情况，如体验卡住、空白屏幕和计划问题。 这样，我们便可以了解设备上的问题并排除其故障，从而加快调查和纠正措施的实施。

AEM Screens播放器中的基本播放监控允许我们：

* 如果播放器正确播放了内容，则进行远程监视。

* 提高对字段中空白屏幕或损坏体验的反应性。

* 降低向最终用户显示损坏的体验的风险。

### 了解属性 {#understand-properties}

每个`ping`中包含以下属性：

| 属性 | 描述 |
|---|---|
| id {string} | 播放器标识符 |
| activeChannel {string} | 当前正在播放渠道路径；或者，如果没有计划，则为空 |
| activeElements {string} | 以逗号分隔的字符串，所有播放序列渠道中的当前可见元素（多区域布局中存在多个元素） |
| isDefaultContent {boolean} | 如果播放渠道被视为默认或回退渠道（即，具有优先级1且无计划），则为true |
| hasContentChanged {boolean} | 如果内容在过去5分钟内发生更改，则为true；否则为false |
| lastContentChange {string} | 上次内容更改的时间戳 |

>[!NOTE]
>或者，也可以从播放器首选项（启用播放监控）中启用更高级的属性，该属性为：
>|属性|描述|
>|—|—|
>|isContentRendering {boolean}|true(如果GPU能确认它正在播放实际内容（基于像素分析）|

### 限制 {#limitations}

下面列出了基本播放监控的一些限制：

* 播放器会向服务器报告其自身的播放状态，因此需要活动连接。

* 默认情况下，用于检查GPU的`isContentRendering`属性当前占用的资源过多，无法启用，并且需要从播放器首选项中明确选择加入。 建议不要将其与生产中的视频结合使用。

* 此功能仅支持序列渠道，尚不涵盖交互式渠道(SPA)用例。

* 这些量度尚未完全向我们的客户公开，我们正在努力在不久的将来启用类似功能板的报告和警报机制。

### 其他资源 {#additional-resources}

有关详细信息，请参阅以下主题：

* 要下载Android播放器，请访问&#x200B;**Google Play**。 要了解有关实施Android监视程序的信息，请参阅[实施Android播放器](implementing-android-player.md)。

* 要实施Chrome OS播放器，请参阅[Chrome管理控制台](implementing-chrome-os-player.md)以获取更多信息。

* 要配置AEM Screens Windows Player，请参阅[实施Windows Player](implementing-windows-player.md)。
