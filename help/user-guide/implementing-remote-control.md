---
title: 实现远程控制
seo-title: Impementing the Remote Control
description: 按照本页了解Screens远程控制功能。
seo-description: Follow  this page to learn about using the Screens Remote Control Feature.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 6cb2705e-83e6-46f3-bd71-6688d7edc11f
source-git-commit: 6cd68194bf3128464ec368f3e7fd69d20925c3d6
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# 使用Screens遥控器  {#implementing-remote-control}

利用远程控制功能，可以更轻松地访问管理员UI、渠道切换器或清除缓存和重新加载等功能。 此外，它还提供了一种查看播放器上的本地固件版本和系统信息的方法。 这尤其有用，因为连接鼠标和操作超出范围的生产设备可能会很困难，如果播放器已断开与AEM的连接，则更是如此。 在使用Samsung RMS时，这也很有用，因为分辨率的差异可能会使查找和使用鼠标打开管理员UI变得非常困难。

## 常用遥控器按键组合 {#using-common-remote-control}

在所有播放器上，您可以在Screens遥控器中使用以下按键组合：

1. 切换管理员UI - CTRL + 1
1. 切换渠道切换器 — CTRL + 2
1. 清除缓存 — CTRL + ALT + 3
1. 重新加载播放器 — CTRL + 4

## 对特定的远程控制按键组合进行初始化 {#using-tizen-remote-control}

特定于Tizen播放器，您可以使用Samsung RMS中提供的硬件远程或软件远程访问以下功能：

1. A — 切换管理员UI
1. B — 切换渠道切换器
1. C — 清除缓存
1. D — 重新加载播放器

## 其他使用说明 {#using-additional-remote-control}

1. 在管理UI打开的情况下，您可以使用向上和向下箭头来导航选项卡，以查看选项卡中的信息。
1. 打开频道切换器后，您可以使用向上和向下箭头键来导航频道，也可以按Enter键（或遥控器箭头中央的按钮）来切换频道。

下图说明了Samsung远程服务器上的主要用法：
![图像](assets/tizen/remote.png)

>[!NOTE]
>如果您将enableAdminUI和/或enableOSD的设备配置值设置为false，则远程设备不会切换管理UI和渠道切换器。 您也无法使用箭头键在管理员UI或渠道中导航。 但是，您仍然可以清除缓存并重新加载播放器。 如果有任何键盘组合与使用以下代码的交互式内容冲突，则可以禁用远程控制功能：

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
