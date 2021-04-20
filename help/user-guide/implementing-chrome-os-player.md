---
title: 实施Chrome OS Player
seo-title: 实施Chrome OS Player
description: 可查看本页以了解如何使用Chrome管理控制台实施Chrome OS Player。
seo-description: 可查看本页以了解如何使用Chrome管理控制台实施Chrome OS Player。
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---


# 实施Chrome OS Player {#implementing-chrome-os-player}

本节介绍如何使用Chrome管理控制台实施Chrome OS Player。

## 使用Chrome管理控制台{#using-chrome-management-console}

请按照以下步骤设置Chrome管理控制台：

1. 注册Chrome管理控制台。 您需要获得Chrome Management Console的许可证。 有关详细信息，请与[Google Support](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995)联系以管理Chrome设备设置。
1. 将您的Chrome OS设备注册到域，等待15分钟，设备将与Chrome管理控制台同步。 要了解有关登记Chrome设备的更多信息，请单击[此处](https://support.google.com/chrome/a/answer/1360534?hl=en)。
1. Chrome Player将在Chrome Web商店中提供。

>[!NOTE]
>
>建议使用诸如Chrome管理控制台之类的设备管理解决方案来部署和管理Chrome OS设备。 尽管此文档为Chrome管理控制台提供了实施，但也有其他供应商声称提供类似功能。 请联系设备管理软件的供应商。

### 启用Kiosk模式{#enabling-kiosk-mode}

请按照以下步骤启用Kiosk模式：

1. 登录到Chrome Developer控制台。

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. 浏览至&#x200B;**设备管理** > **Chrome管理** > **设备设置**。
1. 向下滚动到&#x200B;**Kiosk Settings**&#x200B;并单击&#x200B;**Manage Kiosk Applications**。

   ![自助](assets/kiosk.png)

1. 从Chrome Web Store中选择AEM Screens Player。

   >[!NOTE]
   >
   >最近发布的应用程序可能需要大约15分钟才能显示在此列表中。

1. 从&#x200B;**自动启动自助终端应用程序**&#x200B;下拉菜单中选择&#x200B;**AEM Screens Player**。

   更改可能需要几分钟时间才能生效，具体取决于网络。 建议重新启动。

#### 正在检查远程设备状态{#checking-remote-device-status}

1. 登录到Chrome Developer控制台。
1. 浏览至&#x200B;**设备管理** > **Chrome设备**&#x200B;并选择要控制的设备。
1. 单击&#x200B;**系统活动和疑难解答**。
1. 检查设备的&#x200B;**重新启动设备**&#x200B;和&#x200B;**屏幕捕捉**&#x200B;属性。 您还可以检查设备状态和运行状况信息。

>[!NOTE]
>
>请注意，这些设置可能在设备登记后几分钟内启用。 随着时间的推移，每个选项都可能会启用。

### 配置Chrome OS播放器的远程配置{#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player是支持Kiosk的应用程序，它还为Chrome OS播放器启用远程策略配置。

请按照以下步骤配置播放器的各种选项：

1. 登录Chrome管理控制台。
1. 单击&#x200B;**设备管理** > **Chrome Management** > **App Management**。 AEM Screens播放器将显示在列表中。
1. 单击应用程序&#x200B;**AEM Screens Player**。
1. 单击&#x200B;**Kiosk设置**&#x200B;并选择您的组织(*如果使用测试环境*)。
1. 单击&#x200B;**上传配置文件**&#x200B;并上传配置策略（*Json文件*）。
1. 单击&#x200B;**保存**。必须重新启动设备以同步策略。

>[!NOTE]
>
>重新启动设备以同步策略更改。

#### 示例策略JSON文件{#example-policy-json-file}

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

### 策略属性和用途{#policy-attributes-and-purpose}

下表总结了这些策略及其功能。

| **策略名称** | **用途** |
|---|---|
| *服务器* | 指向Adobe Experience Manager Server的URL |
| *分辨率* | Chrome OS设备的分辨率 |
| *rebootSchedule* | 重新启动Chrome播放器的计划 |
| *enableAdminUI* | 启用管理员UI，让技术人员在现场配置设备。 在完全配置后在生产中设置为false。 |
| *enableOSD* | 启用渠道切换器UI，让用户在设备上切换渠道。 在完全配置后，在生产中考虑将其设置为false。 |
| *enableActivityUI* | 启用以显示下载和同步等活动的进度。 在完全配置并投入生产后启用故障排除和禁用。 |

>[!NOTE]
>
>策略配置是严格强制执行的，不会在播放器的管理UI中手动覆盖。 要允许对特定策略进行手动播放器配置，请不要在&#x200B;***策略配置中指定策略，例如***，如果要允许手动配置以进行重新启动计划，请不要在策略配置中指定键&#x200B;***rebootSchedule***。
