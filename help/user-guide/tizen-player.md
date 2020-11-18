---
title: Tizen Player
description: 本页介绍Tizen Player的安装和工作。
translation-type: tm+mt
source-git-commit: b439cfab068dcbbfab602ad8d31aaa2781bde805
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# 实施Tizen Player {#tizen-player}

## 安装Tizen Player {#installing-tizen-player}

请按照以下步骤为AEM Screens实施Tizen Player:

1. 导航到AEM [**6.5 Player下载页**](https://download.macromedia.com/screens/) ，下载Tizen Player。

1. 从本地计算机安装Tizen播放器(.zip)文件。

1. 获取本地计算机的IP地址。

   >[!NOTE]
   >对于 **终端** 中 **的Mac** 和Windows `ifconfig` 类型命令。

1. 从终端，导航到解压缩的安装程序文件夹的同一目录，并验证localhost是否正在工作。

   >[!NOTE]
   >对 **于Mac**，键入 `http://localhost` 并验证服务器 `http` 是否正在运行。

1. Tizen播放器将从本地服务器下载安装程序。

1. 将两个解压文件 `AEMScreensPlayer.wgt` 复制 `sssp_config.xml` 到 `/Library/WebServer/Documents`。

### SamSung设备上的配置更新 {#config-updates}

按照Samsung设备上的以下步骤在设备上完成AEM Screens播放器的安装：

1. 单击Samsung **Remote** 中的“主页”按钮。
1. 从“ **设置** ”中选择 **URL启动器**。
1. 从“开 **发人员** ”模式中选择“远程”。
1. 安装Web应用程序并输入计算机的IP地址。
AEM Screens播放器应自动安装在Samsung设备上。


