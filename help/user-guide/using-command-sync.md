---
title: 使用命令同步
seo-title: 使用命令同步
description: 可查看本页以了解如何使用命令同步。
seo-description: 可查看本页以了解如何使用命令同步。
translation-type: tm+mt
source-git-commit: d25c45d6362a5f8ffac84e07dacb30c0b7c64493
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 2%

---


# 命令同步{#command-sync}

下页介绍如何使用命令同步。 命令同步允许在不同播放器之间同步播放。 玩家可以播放不同的内容，但每个资产需要具有相同的持续时间。

>[!IMPORTANT]
>
>此功能不支持嵌入式序列、动态嵌入式序列、应用程序渠道或过渡。

## 概述 {#overview}

数字标牌解决方案需要支持视频墙和同步播放，以支持诸如新年倒计时或大视频等场景在多个屏幕上播放，这就是开始使用命令同步的地方。

要使用命令同步，一个播放器充当&#x200B;*主控*&#x200B;并发送命令，而所有其他播放器充当&#x200B;*客户端* ，并在他们收到命令时播放。

当&#x200B;*主控*&#x200B;要开始项回放时，该命令会发送给所有注册的客户端。 此项的有效负荷可以是要播放的项的索引和／或要播放的元素的外部html。

## 实现命令同步{#using-command-sync}

下节介绍如何在AEM Screens项目中使用命令同步。

>[!NOTE]
>
>对于同步播放，要求所有硬件设备具有相同的硬件规范，最好具有相同的操作系统。 不建议在不同硬件和操作系统之间同步。

### 设置项目{#setting-up}

在使用命令同步功能之前，请确保您有一个项目和一个渠道，其中为项目设置了内容。

1. 以下示例展示了名为&#x200B;**CommandSyncDemo**&#x200B;的演示项目和序列渠道&#x200B;**ChannelLobby**。

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >要了解如何创建渠道或向渠道添加内容，请参阅[创建和管理渠道](/help/user-guide/managing-channels.md)

   渠道包含以下内容，如下图所示。

   ![image1](assets/command-sync/command-sync2-1.png)

1. 创建位置&#x200B;**Lobby**，然后在&#x200B;**Locations**&#x200B;文件夹中创建标题为&#x200B;**LobbyDisplay**的显示，如下图所示。
   ![image1](assets/command-sync/command-sync3-1.png)

1. 将渠道&#x200B;**ChannelLobby**&#x200B;分配给&#x200B;**LobbyDisplay**。 您现在可以从显示视图将分配的渠道仪表板到显示屏。
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >要了解如何将渠道分配给显示屏，请参阅[创建和管理显示屏](/help/user-guide/managing-displays.md)。

1. 导航到&#x200B;**设备**&#x200B;文件夹，然后单击操作栏中的&#x200B;**设备管理器**&#x200B;以注册设备。

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >要了解如何注册设备，请参阅[设备注册](/help/user-guide/device-registration.md)

1. 为便于演示，此示例将铬黄设备和windows播放器作为两个单独的设备进行展示。 这两个设备指向同一个显示屏。
   ![image1](assets/command-sync6.png)

### 更新渠道设置

1. 导航到&#x200B;**ChannelLobby**&#x200B;并单击操作栏中的&#x200B;**编辑**&#x200B;以更新渠道设置。

1. 选择整个渠道，如下图所示。
   ![image1](assets/command-sync/command-sync7-1.png)

1. 单击扳手图标以打开&#x200B;**Page**对话框。
   ![image1](assets/command-sync/command-sync8-1.png)

1. 在&#x200B;**策略**&#x200B;字段中输入&#x200B;*synced*&#x200B;关键字。

   ![image1](assets/command-sync/command-sync9-1.png)


### 设置主控{#setting-up-master}

1. 从&#x200B;**CommandSyncDemo** —> **位置** —> **休息室** —> **休息室显示**&#x200B;导航到显示仪表板，然后单击操作栏中的&#x200B;**仪表板**。
您将在**DEVICES**面板中看到两个设备（chrome和windows播放器），如下图所示。
   ![image1](assets/command-sync/command-sync10-1.png)

1. 从&#x200B;**设备**&#x200B;面板中，选择要设置为主控的设备。 以下示例演示如何将Chrome设备设置为主控。 单击&#x200B;**设置为主控设备**。

   ![image1](assets/command-sync/command-sync11-1.png)

1. 在&#x200B;**设置为主控设备**&#x200B;中输入IP地址，然后单击&#x200B;**保存**。

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>您可以将多个设备设置为主控。

### 与主控{#sync-up-master}同步

1. 将Chrome设备设置为主控后，可以同步其他设备（本例中为windows播放器）以与主控同步。
从**设备**&#x200B;面板中选择其他设备（本例中为windows播放器），然后单击&#x200B;**同步到主控设备**，如下图所示。

   ![image1](assets/command-sync/command-sync13-1.png)

1. 从列表中选择设备，然后单击&#x200B;**保存**。

   >[注意:]
   > **同步到主控设备**&#x200B;对话框将显示主控设备的列表。 您可以选择所需的首选项之一。

1. 设备（Windows播放器）同步到主控（Chrome播放器）后，您将在&#x200B;**DEVICES**&#x200B;面板中看到同步的设备。

   ![image1](assets/command-sync/command-sync14-1.png)

### 与主控{#desync-up-master}取消同步

将设备或设备同步到主控后，即可从该设备取消分配同步。

>[!NOTE]
>
>如果取消主控设备的同步，它还会取消与该主控设备关联的所有客户端设备的链接。

要从主控设备中删除同步，请执行以下步骤：

1. 导航到&#x200B;**DEVICES**&#x200B;面板并选择设备。

1. 单击&#x200B;**取消同步设备**&#x200B;以取消客户端与主控设备的同步。

   ![image1](assets/command-sync/command-sync15-1.png)

1. 单击&#x200B;**确认**&#x200B;以从主控中取消选定设备的同步。

   >[注意:]
   > 如果您选择主控设备并使用取消同步选项，则连接到主控的所有设备将通过一个步骤取消同步。
