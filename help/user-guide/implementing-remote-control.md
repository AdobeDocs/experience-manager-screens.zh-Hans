---
title: 实施远程控制
description: 了解AEM Screens中的Screens远程控制功能。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 6cb2705e-83e6-46f3-bd71-6688d7edc11f
source-git-commit: e82cfee5ecc6b639b7b2b65553d1635943b356ea
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 使用Screens远程控制 {#implementing-remote-control}

利用远程控制功能，可以更轻松地访问管理员UI、渠道切换器或清除缓存和重新加载等功能。 此外，它还为您提供了查看播放器上的本地固件版本和系统信息的方法。 此功能特别有用，因为连接鼠标可能会很困难。 或者，在无法访问的生产设备上操作，如果播放器已断开与AEM的连接，则更是如此。 它在使用Samsung RMS时也很有用，因为分辨率的差异使得查找和使用鼠标打开管理员UI变得困难。

## 通用遥控器按键组合 {#using-common-remote-control}

在所有播放器上，您可以在Screens远程控制中使用以下组合键：

1. 切换管理员UI - CTRL + 1
1. 切换渠道切换器 — CTRL + 2
1. 清除缓存 — CTRL + ALT + 3
1. 重新加载播放器 — CTRL + 4

## 启用特定的远程控制按键组合 {#using-tizen-remote-control}

特定于Tizen播放器，您可以使用Samsung RMS中提供的硬件远程或软件远程来访问这些功能：

1. A — 切换管理员UI
1. B — 切换渠道切换器
1. C — 清除缓存
1. D — 重新加载播放器

## 更多使用说明 {#using-additional-remote-control}

1. 在管理UI打开的情况下，您可以使用向上和向下箭头来导航选项卡，以跨选项卡查看信息。
1. 打开渠道切换器后，您可以使用向上和向下箭头键导航渠道。 您还可以按`Enter`键（或遥控器箭头中央的按钮）来切换频道。

下图说明了Samsung远程服务器上的主要用法：
![图像](assets/tizen/remote.png)

>[!NOTE]
>如果将enableAdminUI和/或enableOSD的设备配置值设置为false，则远程设备不会切换管理员UI和渠道切换器。 无法使用箭头键在管理员UI或渠道中导航。 但是，您仍然可以清除缓存并重新加载播放器。 如果有任何键盘组合与使用此代码的交互式内容冲突，则可以禁用远程控制功能：

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
