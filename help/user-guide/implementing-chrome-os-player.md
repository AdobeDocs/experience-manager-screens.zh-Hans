---
title: 实施Chrome OS播放器
seo-title: 实施Chrome OS播放器
description: 请阅读本页，了解如何使用Chrome管理控制台实施Chrome OS播放器。
seo-description: 请阅读本页，了解如何使用Chrome管理控制台实施Chrome OS播放器。
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: 管理屏幕
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: 3bda698ca44f58c177f8e87a5c50b789966909de
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 0%

---

# 实施Chrome OS播放器  {#implementing-chrome-os-player}

本节介绍如何使用Chrome管理控制台实施Chrome OS播放器。

## 使用Chrome管理控制台 {#using-chrome-management-console}

请按照以下步骤设置Chrome管理控制台：

1. 注册Chrome管理控制台。 您需要获取Chrome管理控制台的许可证。 有关更多信息，请联系[Google支持](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995)以管理Chrome设备设置。
1. 将您的Chrome OS设备注册到域，等待15分钟，以便设备与Chrome管理控制台同步。 要了解有关注册Chrome设备的更多信息，请单击[此处](https://support.google.com/chrome/a/answer/1360534?hl=en)。
1. Chrome播放器将在Chrome网上应用商店中提供。

>[!NOTE]
>
>为部署和管理Chrome OS设备，建议使用设备管理解决方案（如Chrome管理控制台）。 尽管如此，本文档为Chrome管理控制台提供了实施，但仍有其他供应商声称提供类似功能。 请联系设备管理软件的供应商。

## 命名Chrome OS播放器 {#name-chrome}

您可以为Chrome播放器分配用户友好的设备名称，从而将分配的设备名称发送到Adobe Experience Manager(AEM)。 此功能不仅允许您命名Chrome播放器，还允许您轻松分配相应的内容。

>[!NOTE]
>只有在注册之前，您才可以选择播放器名称。 注册播放器后，无法再更改播放器名称。

请按照以下步骤在Chrome播放器中配置名称：

1. 您可以选择允许AV集成商或IT管理员将资产ID和位置设置为企业注册的一部分。

   ![图像](/help/user-guide/assets/chrome-device/chrome1.png)

1. 当您注册设备时，将为您提供相应的选项。

   ![图像](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. 您可以在企业注册以及Chrome管理控制台中将资产ID设置为一部分。

   ![图像](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >必须在企业注册中注册Chrome播放器，并且必须通过Chrome管理控制台部署Chrome播放器，否则资产ID将返回空白（例如，将Chrome作为扩展）。 设备名称仅在注册时记录。 Adobe Experience Manager(AEM)将不会接收将来的更改。

### 启用Kiosk模式 {#enabling-kiosk-mode}

按照以下步骤启用Kiosk模式：

1. 登录到Chrome开发人员控制台。

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. 浏览至&#x200B;**设备管理** > **Chrome管理** > **设备设置**。
1. 向下滚动到&#x200B;**Kiosk设置**&#x200B;并单击&#x200B;**管理Kiosk应用程序**。

   ![亭](assets/kiosk.png)

1. 从Chrome网上应用店中选择AEM Screens播放器。

   >[!NOTE]
   >
   >最近发布的应用程序可能需要大约15分钟才能显示在此列表中。

1. 从&#x200B;**自动启动网亭应用程序**&#x200B;下拉列表中选择&#x200B;**AEM Screens Player**。

   更改可能需要几分钟才能生效，具体取决于网络。 建议重新启动。

#### 检查远程设备状态 {#checking-remote-device-status}

1. 登录到Chrome开发人员控制台。
1. 浏览至&#x200B;**设备管理** > **Chrome设备**，然后选择要控制的设备。
1. 单击&#x200B;**系统活动和疑难解答**。
1. 检查设备的&#x200B;**重新启动设备**&#x200B;和&#x200B;**屏幕捕获**&#x200B;属性。 您还可以检查设备状态和运行状况信息。

>[!NOTE]
>
>请注意，这些设置可能会在设备注册后几分钟内启用。 每个选项可能会随着时间的推移而启用。

### 配置Chrome OS播放器的远程配置 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player是一个支持Kiosk的应用程序，还为Chrome OS播放器启用远程策略配置。

请按照以下步骤配置播放器的各种选项：

1. 登录到Chrome管理控制台。
1. 单击&#x200B;**设备管理** > **Chrome管理** > **应用程序管理**。 AEM Screens播放器将显示在列表中。
1. 单击应用程序&#x200B;**AEM Screens Player**。
1. 单击&#x200B;**Kiosk设置**&#x200B;并选择您的组织（如果使用测试环境&#x200B;*，请选择*）。
1. 单击&#x200B;**上传配置文件**&#x200B;并上传配置策略（*Json文件*）。
1. 单击&#x200B;**保存**。必须重新启动设备才能同步策略。

>[!NOTE]
>
>重新启动设备以同步策略更改。

#### 策略JSON文件示例 {#example-policy-json-file}

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

下表概述了策略及其功能。

| **策略名称** | **用途** |
|---|---|
| *服务器* | 指向Adobe Experience Manager Server的URL |
| *分辨率* | Chrome OS设备的分辨率 |
| *rebootSchedule* | 重新启动Chrome播放器的计划 |
| *enableAdminUI* | 为技术人员启用管理员UI，以便在现场配置设备。 在生产环境中完全配置后，将其设置为false。 |
| *enableOSD* | 启用渠道切换器UI，以便用户在设备上切换渠道。 在完全配置并投入生产后，请考虑将设置为false。 |
| *enableActivityUI* | 启用以显示下载和同步等活动的进度。 在完全配置并投入生产后，启用以进行故障排除并禁用。 |

>[!NOTE]
>
>策略配置是严格强制执行的，不会在播放器的管理员UI中手动覆盖。 要允许对特定策略进行手动播放器配置，请不要在&#x200B;***策略配置中指定策略，例如***，如果要允许对重新启动计划进行手动配置，请不要在策略配置中指定键&#x200B;***rebootSchedule***。
