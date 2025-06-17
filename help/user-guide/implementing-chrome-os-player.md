---
title: 实施Chrome操作系统播放器
description: 了解如何使用Chrome Management Console实施Chrome OS Player。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---

# 实施Chrome操作系统播放器 {#implementing-chrome-os-player}

本节介绍如何使用Chrome Management Console实施Chrome OS Player。

## 使用Chrome Management Console {#using-chrome-management-console}

请按照以下步骤设置Chrome管理控制台：

1. 注册Chrome管理控制台。 您必须获取Chrome管理控制台的许可证。 有关详细信息，请与[Google支持](https://support.google.com/chrome/a/answer/1375678?hl=en&ref_topic=2935995)联系以管理Chrome设备设置。
1. 将Chrome操作系统设备注册到域，并等待15分钟以使设备与Chrome管理控制台同步。 要了解有关注册Chrome设备的更多信息，请单击[此处](https://support.google.com/chrome/a/answer/1360534?hl=en)。
1. Chrome Player位于Chrome Web Store中。

>[!NOTE]
>
>建议使用设备管理解决方案(例如Chrome管理控制台)来部署和管理Chrome操作系统设备。 尽管本文档提供了Chrome管理控制台的实施，但其他供应商也声称提供了类似功能。 请与设备管理软件的供应商联系。

## 命名Chrome OS Player {#name-chrome}

您可以为Chrome播放器分配一个用户友好的设备名称，然后将分配的设备名称发送到Adobe Experience Manager (AEM)。 此功能不仅允许您为Chrome播放器命名，还允许您轻松分配适当的内容。

>[!NOTE]
>您只能在注册之前选择播放器名称。 注册播放器后，无法再更改播放器名称。

请按照以下步骤在Chrome Player中配置名称：

1. 您可以选择允许音频视频集成商或IT管理员在企业注册过程中设置资产ID和位置。

   ![图像](/help/user-guide/assets/chrome-device/chrome1.png)

1. 在注册设备时，您会看到相应的选项。

   ![图像](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. 您可以将资产ID设置为企业注册的一部分，也可以在Chrome Management Console中进行设置。

   ![图像](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >必须在企业注册中注册Chrome播放器，并且必须通过Chrome Management Console部署Chrome播放器，否则资产ID将返回空白(例如，将Chrome作为扩展)。 设备名称仅在注册时记录。 Adobe Experience Manager (AEM)不会接受将来的更改。

### 启用Kiosk模式 {#enabling-kiosk-mode}

按照以下步骤启用Kiosk模式：

1. 登录到Chrome Developer Console。

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. 浏览到&#x200B;**设备管理** > **Chrome管理** > **设备设置**。
1. 向下滚动至&#x200B;**网亭设置**，然后单击&#x200B;**管理网亭应用程序**。

   ![信息亭](assets/kiosk.png)

1. 单击Chrome Web Store中的AEM Screens Player 。

   >[!NOTE]
   >
   >最近发布的应用程序可能需要大约15分钟才能显示在此列表中。

1. 从&#x200B;**自动启动信息亭应用**&#x200B;下拉菜单中单击&#x200B;**AEM Screens Player**。

   根据网络的不同，更改可能需要几分钟才会生效。 建议重新引导。

#### 正在检查远程设备状态 {#checking-remote-device-status}

1. 登录到Chrome Developer Console。
1. 浏览到&#x200B;**设备管理** > **Chrome设备**，然后单击要控制的设备。
1. 单击&#x200B;**系统活动和疑难解答**。
1. 检查设备的&#x200B;**重新启动设备**&#x200B;和&#x200B;**屏幕捕获**&#x200B;属性。 您还可以检查设备状态和运行状况信息。

>[!NOTE]
>
>这些设置可在设备注册后几分钟启用。 随着时间的推移，每个选项都可以启用。

### 配置Chrome OS播放器的远程配置 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player是一个支持Kiosk的应用程序，它还为Chrome OS播放器启用了远程策略配置。

请按照以下步骤配置播放器的各种选项：

1. 登录到Chrome管理控制台。
1. 单击&#x200B;**设备管理** > **Chrome管理** > **应用程序管理**。 AEM Screens播放器将显示在列表中。
1. 单击应用程序&#x200B;**AEM Screens Player**。
1. 单击&#x200B;**网亭设置**，然后单击您的组织（*如果使用测试环境*）。
1. 单击&#x200B;**上载配置文件**&#x200B;并上载配置策略（*JSon文件*）。
1. 单击&#x200B;**保存**。重新启动设备，以便同步策略。

>[!NOTE]
>
>重新启动设备，以便同步策略更改。

#### 示例策略JSON文件 {#example-policy-json-file}

```java
{
  "server": {
    "Value": "https://aemscreensdemo.adobeitc.com"
  },
  "resolution": {
    "Value": "auto"
  },
  "rebootSchedule": {
    "Value": "at 4:00am"
  },
  "enableAdminUI": {
    "Value": true
  },
  "enableOSD": {
    "Value": true
  },
  "enableActivityUI": {
    "Value": true
  }
}
```

### 策略属性和目的 {#policy-attributes-and-purpose}

下表总结了策略及其功能。

| **策略名称** | **用途** |
|---|---|
| 服务器 | Adobe Experience Manager (AEM)服务器的URL。 |
| 注册密钥 | 用于使用预共享密钥批量注册设备。 |
| 分辨率 | 设备的分辨率。 |
| rebootSchedule | 重新启动播放器的计划。 |
| enableAdminUI | 启用管理UI以在站点上配置设备。 在完全配置并投入生产后，设置为false。 |
| enableOSD | 为用户启用通道切换器UI以在设备上切换通道。 在完全配置并投入生产后，请考虑将其设置为false 。 |
| enableActivityUI | 启用，以便显示活动的进度，例如下载和同步。 在完全配置并投入生产后，启用以进行故障排除并禁用。 |
| 云模式 | 如果希望Chrome Player连接到Screens as a Cloud Service，则设置为true。 设置为false以连接到AMS或本地AEM。 |
| cloudToken | 注册令牌以针对Screens as a Cloud Service进行注册。 |

>[!NOTE]
>
>策略配置是严格强制实施的，播放器的管理UI不会手动覆盖。 若要允许手动配置特定策略，请勿在&#x200B;***策略配置***&#x200B;中指定该策略。 例如，如果要允许手动配置重新启动计划，请不要在策略配置中指定键&#x200B;***rebootSchedule***。

### 使用Screens远程控制 {#using-remote-control}

AEM Screens提供远程控制功能。 在此处了解有关此功能的更多信息：[Screens远程控制](implementing-remote-control.md)
