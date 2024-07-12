---
title: 使用命令同步
description: 详细了解如何使用AEM Screens中的Command Sync。
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 0%

---

# 命令同步 {#command-sync}

以下页面介绍了如何使用“命令同步”。 命令同步允许跨不同播放器同步播放。 播放器可以播放不同的内容，但每个资源必须具有相同的持续时间。

>[!IMPORTANT]
>
>此功能不支持嵌入式序列、动态嵌入式序列、应用程序通道或过渡。

## 概述 {#overview}

数字标牌解决方案必须支持视频墙和同步播放。 如果您尝试支持“新年倒计时”或大视频分段在多个屏幕中播放等场景，则此场景为true。 在这种情况下，命令同步将发挥作用。

要使用命令同步，一个播放器充当&#x200B;*primary*&#x200B;并发送命令，而所有其他播放器充当&#x200B;*客户端*&#x200B;并在收到命令时播放。

*primary*&#x200B;将在即将开始播放项目时向所有注册的客户端发送命令。 此操作的有效负载可以是要播放项目的索引、要播放的元素的外部html或两者。

## 实施命令同步 {#using-command-sync}

以下部分介绍如何在AEM Screens项目中使用Command Sync。

>[!NOTE]
>
>对于同步播放，要求所有硬件设备具有相同的硬件规格并且最好具有相同的操作系统。 不建议在不同硬件和操作系统之间同步。

### 设置项目 {#setting-up}

在使用命令同步功能之前，请确保您有一个项目和一个渠道，其中包含为您的项目设置的内容。

1. 以下示例展示了名为&#x200B;**CommandSyncDemo**&#x200B;的演示项目和序列频道&#x200B;**ChannelLobby**。

   ![图像1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >要了解如何创建渠道或向渠道添加内容，请参阅[创建和管理渠道](/help/user-guide/managing-channels.md)

   该渠道包含以下内容，如下图所示。

   ![图像1](assets/command-sync/command-sync2-1.png)

1. 创建位置&#x200B;**大厅**，然后在&#x200B;**位置**&#x200B;文件夹中创建标题为&#x200B;**大厅显示**的显示，如下图所示。
   ![图像1](assets/command-sync/command-sync3-1.png)

1. 将频道&#x200B;**ChannelLobby**&#x200B;分配给您的&#x200B;**LobbyDisplay**。 您现在可以从显示功能板中查看分配给显示的渠道。
   ![图像1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >要了解如何将渠道分配给显示，请参阅[创建和管理显示](/help/user-guide/managing-displays.md)。

1. 导航到&#x200B;**设备**&#x200B;文件夹。
1. 单击操作栏中的&#x200B;**设备管理器**。

   ![图像1](assets/command-sync5.png)

   >[!NOTE]
   >
   >要了解如何注册设备，请参阅[设备注册](/help/user-guide/device-registration.md)

1. 为了进行演示，此示例将Chrome设备和Windows Player显示为两个单独的设备。 两台设备指向同一个显示器。
   ![图像1](assets/command-sync6.png)

### 更新渠道设置

1. 导航到&#x200B;**ChannelLobby**。
1. 单击操作栏中的&#x200B;**编辑**。
1. 单击整个通道，如下图所示。
   ![图像1](assets/command-sync/command-sync7-1.png)

1. 单击扳手图标。
   ![图像1](assets/command-sync/command-sync8-1.png)

1. 在&#x200B;**页面**&#x200B;对话框中，在&#x200B;**策略**&#x200B;字段中输入&#x200B;*已同步*关键字。
   ![图像1](assets/command-sync/command-sync9-1.png)


### 设置主要播放器 {#setting-up-primary}

1. 从&#x200B;**CommandSyncDemo** > **位置** > **大厅** > **大厅显示**&#x200B;导航到显示仪表板。 然后单击操作栏中的&#x200B;**仪表板**。
请注意**设备**面板中的两台设备(Chrome和Windows Player)，如以下所示：
   ![图像1](assets/command-sync/command-sync10-1.png)

1. 在&#x200B;**设备**&#x200B;面板中，单击要设置为主设备的设备。 以下示例演示了如何将Chrome设备设置为主设备。 单击&#x200B;**设置为主设备**。

   ![图像1](assets/command-sync/command-sync11-1.png)

1. 在&#x200B;**设置为主设备**&#x200B;中输入IP地址，然后单击&#x200B;**保存**。

   ![图像1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>您可以将多个设备设置为主设备。

### 正在与主要播放器同步 {#sync-up-primary}

1. 将Chrome设备设置为主设备后，将另一设备（在本例中为Windows Player）同步到主设备。
单击**设备**&#x200B;面板中的其他设备（在本例中为Windows Player），然后单击&#x200B;**同步到主设备**。

   ![图像1](assets/command-sync/command-sync13-1.png)

1. 单击列表中的设备，然后单击&#x200B;**保存**。

   >[注释：]
   > **同步到主设备**&#x200B;对话框显示主设备列表。 选择首选的。

1. 当设备(Windows Player)同步到主设备(Chrome Player)时，您可以在&#x200B;**设备**&#x200B;面板中看到已同步的设备。

   ![图像1](assets/command-sync/command-sync14-1.png)

### 正在与主要播放器取消同步 {#desync-up-primary}

将一个或多个设备同步到主设备后，可以从该设备取消同步分配。

>[!NOTE]
>
>如果取消同步主设备，它还将取消与该主设备关联的所有客户端设备的链接。

要从主设备删除同步，请执行以下步骤：

1. 导航到&#x200B;**设备**&#x200B;面板，然后单击该设备。

1. 单击&#x200B;**取消同步设备**，以便从主设备取消同步客户端。

   ![图像1](assets/command-sync/command-sync15-1.png)

1. 单击&#x200B;**确认**&#x200B;将所选设备从主设备取消同步。

   >[注释：]
   > 如果单击主设备并使用de-sync选项，则所有连接到主设备的设备将一步骤中取消同步。
