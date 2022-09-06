---
title: 使用命令同步
seo-title: Using Command Sync
description: 请阅读本页，了解如何使用命令同步。
seo-description: Follow this page to learn about how to use Command Sync.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: 43ac19cf7ef63ec17611cf19ca357f791dca6e87
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 2%

---

# 命令同步 {#command-sync}

以下页介绍如何使用命令同步。 命令同步允许在不同播放器之间同步播放。 播放器可以播放不同的内容，但每个资产需要具有相同的持续时间。

>[!IMPORTANT]
>
>此功能不支持嵌入式序列、动态嵌入式序列、应用程序渠道或过渡。

## 概述 {#overview}

数字标牌解决方案需要支持视频墙和同步播放，以支持诸如新年倒计时或大视频被切片在多个屏幕中播放等场景，这正是命令同步发挥作用的地方。

要使用命令同步，一个播放器充当 *主要* 发出命令，其他所有的玩家 *客户* 并在收到命令时播放。

的 *主要* 将要开始播放项目时，会向所有注册的客户端发送命令。 其有效负荷可以是要播放的项目的索引和/或要播放的元素的外部html。

## 实现命令同步 {#using-command-sync}

以下部分介绍如何在AEM Screens项目中使用命令同步。

>[!NOTE]
>
>对于同步播放，要求所有硬件设备具有相同的硬件规范，最好是相同的操作系统。 不建议在不同硬件和操作系统之间进行同步。

### 设置项目 {#setting-up}

在使用命令同步功能之前，请确保您有一个项目和一个渠道，该渠道已为您的项目设置内容。

1. 以下示例展示了一个名为 **CommandSyncDemo** 和序列频道 **ChannelLobby**.

   ![图像1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >要了解如何创建渠道或向渠道添加内容，请参阅 [创建和管理渠道](/help/user-guide/managing-channels.md)

   渠道包含以下内容，如下图所示。

   ![图像1](assets/command-sync/command-sync2-1.png)

1. 创建位置 **大堂** 和标题为 **LobbyDisplay** 在 **位置** 文件夹中，如下图所示。
   ![图像1](assets/command-sync/command-sync3-1.png)

1. 分配渠道， **ChannelLobby** 至 **LobbyDisplay**. 您现在可以从显示功能板中查看为显示屏分配的渠道。
   ![图像1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >要了解如何将渠道分配给显示屏，请参阅 [创建和管理显示屏](/help/user-guide/managing-displays.md).

1. 导航到 **设备** 文件夹，单击 **设备管理器** 来注册设备。

   ![图像1](assets/command-sync5.png)

   >[!NOTE]
   >
   >要了解如何注册设备，请参阅 [设备注册](/help/user-guide/device-registration.md)

1. 出于演示目的，此示例将Chrome设备和Windows播放器作为两个单独的设备显示。 两个设备指向同一显示屏。
   ![图像1](assets/command-sync6.png)

### 更新渠道设置

1. 导航到 **ChannelLobby** 单击 **编辑** 来更新渠道设置。

1. 选择整个渠道，如下图所示。
   ![图像1](assets/command-sync/command-sync7-1.png)

1. 单击扳手图标以打开 **页面** 对话框。
   ![图像1](assets/command-sync/command-sync8-1.png)

1. 输入 *同步* 关键词 **策略** 字段。

   ![图像1](assets/command-sync/command-sync9-1.png)


### 设置主 {#setting-up-primary}

1. 从导航到显示功能板 **CommandSyncDemo** —> **位置**  —> **大堂** —> **LobbyDisplay** 单击 **功能板** 中。
您将在 **设备** 面板，如下图所示。
   ![图像1](assets/command-sync/command-sync10-1.png)

1. 从 **设备** 面板中，选择要设置为主设备的设备。 以下示例演示了如何将Chrome设备设置为主设备。 单击 **设置为主设备**.

   ![图像1](assets/command-sync/command-sync11-1.png)

1. 在 **设置为主设备** 单击 **保存**.

   ![图像1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>您可以将多个设备设置为主设备。

### 与主同步 {#sync-up-primary}

1. 将Chrome设备设置为主设备后，可以同步其他设备（在本例中为Windows播放器）以与主设备同步。
从 **设备** 面板，单击 **同步到主设备**，如下图所示。

   ![图像1](assets/command-sync/command-sync13-1.png)

1. 从列表中选择设备，然后单击 **保存**.

   >[注意:]
   > 的 **同步到主设备** 对话框将显示主设备列表。 您可以选择所需的首选项之一。

1. 将设备（Windows播放器）同步到主设备（Chrome播放器）后，您将在 **设备** 的上界。

   ![图像1](assets/command-sync/command-sync14-1.png)

### 取消与主同步 {#desync-up-primary}

将设备或设备同步到主设备后，即可从该设备中取消同步分配。

>[!NOTE]
>
>如果取消主设备同步，则它还会取消与该主设备关联的所有客户端设备的链接。

要从主设备删除同步，请执行以下步骤：

1. 导航到 **设备** 面板，然后选择设备。

1. 单击 **取消同步设备** 从主设备中取消同步客户端。

   ![图像1](assets/command-sync/command-sync15-1.png)

1. 单击 **确认** 从主设备中取消同步选定设备。

   >[注意:]
   > 如果选择主设备并使用取消同步选项，则所有连接到主设备的设备都将在一个步骤中取消同步。
