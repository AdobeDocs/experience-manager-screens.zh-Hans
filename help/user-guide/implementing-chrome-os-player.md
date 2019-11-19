---
title: 实施Chrome OS Player
seo-title: 实施Chrome OS Player
description: 可查看本页以了解如何使用Chrome管理控制台实现Chrome OS Player。
seo-description: 可查看本页以了解如何使用Chrome管理控制台实现Chrome OS Player。
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 实施Chrome OS Player {#implementing-chrome-os-player}

本节介绍如何使用Chrome管理控制台实现Chrome OS Player。

## 使用Chrome管理控制台 {#using-chrome-management-console}

请按照以下步骤设置Chrome管理控制台：

1. 注册Chrome管理控制台。 您需要获得Chrome管理控制台的许可证。 有关更 [多信息，请与Google支持联系](https://support.google.com/chrome/a/answer/1375678?hl=en&ref_topic=2935995) ，以管理Chrome设备设置。
1. 将您的Chrome OS设备登记到域中，等待15分钟，设备才能与Chrome管理控制台同步。 要了解有关登记Chrome设备的更多信息，请单击 [此处](https://support.google.com/chrome/a/answer/1360534?hl=en)。
1. Chrome web商店中将提供Chrome Player。

>[!NOTE]
>
>建议使用Chrome管理控制台等设备管理解决方案来部署和管理Chrome OS设备。 但是，本文档为Chrome Management Console提供实施，还有一些供应商声称提供类似的功能。 请联系设备管理软件的供应商。

### 启用Kiosk模式 {#enabling-kiosk-mode}

请按照以下步骤启用Kiosk模式：

1. 登录到Chrome Developer Console。

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. 浏览至“设 **备管理** ”&gt;“ **Chrome管理** ” **&gt;“设**&#x200B;备设置”。
1. 向下滚动到 **Kiosk Settings** ，然后单击 **Manage Kiosk Applications**。

   ![亭](assets/kiosk.png)

1. 从Chrome Web store中选择AEM Screens播放器。

   >[!NOTE]
   >
   >最近发布的应用程序可能需要大约15分钟才能显示在此列表中。

1. 从“自 **动启动信息亭应用程序** ”下拉列 **表中选择“AEM Screens播放器** ”。

   根据网络的不同，更改可能需要几分钟时间才能生效。 建议重新启动。

#### 检查远程设备状态 {#checking-remote-device-status}

1. 登录到Chrome Developer Console。
1. 浏览至 **设备管理** &gt; **Chrome设备** ，然后选择要控制的设备。
1. 单击“ **系统活动”和“疑难解答**”。
1. 检查设 **备的Reboot** Device **和Screen Capture** 属性。 您还可以检查设备状态和运行状况信息。

>[!NOTE]
>
>请注意，这些设置可能在设备登记后几分钟内启用。 随着时间的推移，每个选项都可能被启用。

### 配置Chrome OS播放器的远程配置 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens播放器是启用了Kiosk的应用程序，它还为Chrome OS播放器启用了远程策略配置。

请按照以下步骤配置播放器的各种选项：

1. 登录Chrome管理控制台。
1. 单击 **设备管理** &gt; **Chrome管理** &gt;应 **用程**&#x200B;序管理。 AEM Screens播放器将显示在列表中。
1. 单击应用程序 **AEM Screens播放器**。
1. 单击 **Kiosk设置** ，选择您的组织(如&#x200B;*果使用测试环境*)。
1. 单击上 **传配置文件** ，然后上传配置策略(*Json文件*)。
1. 单击&#x200B;**保存**。必须重新启动设备才能同步策略。

>[!NOTE]
>
>重新启动设备以同步策略更改。

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

### 策略属性和用途 {#policy-attributes-and-purpose}

下表总结了策略及其功能。

| **策略名称** | **用途** |
|---|---|
| *服务器* | Adobe Experience Manager server的URL |
| *分辨率* | Chrome OS设备的分辨率 |
| *rebootSchedule* | 重新启动Chrome播放器的计划 |
| *enableAdminUI* | 为技术人员启用管理员UI以现场配置设备。 在完全配置并在生产中设置为false。 |
| *enableOSD* | 启用渠道切换器UI，让用户在设备上切换渠道。 在完全配置并投入生产后，请考虑将其设置为false。 |
| *enableActivityUI* | 启用此选项可显示下载和同步等活动的进度。 在完全配置并投入生产后启用故障排除和禁用。 |

>[!NOTE]
>
>策略配置是严格强制执行的，不会在播放器的管理UI中手动覆盖。 要允许对特定策略进行手动播放器配置，请不要在策略配置中指定策略 ***,*** 例如，如果要允许对重新启动计划进行手动配置，请不要在策略配置中指定 ***rebootSchedule*** 。
