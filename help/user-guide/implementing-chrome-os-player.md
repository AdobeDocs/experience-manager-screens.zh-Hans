---
title: 实施Chrome操作系统播放器
seo-title: Implementing Chrome OS Player
description: 请阅读本页，了解如何使用Chrome管理控制台实施Chrome OS Player。
seo-description: Follow  this page to learn about the implementation of the Chrome OS Player using the Chrome Management Console.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 0%

---

# 实施Chrome操作系统播放器  {#implementing-chrome-os-player}

本节介绍如何使用Chrome管理控制台实施Chrome OS Player。

## 使用Chrome管理控制台 {#using-chrome-management-console}

按照以下步骤设置Chrome管理控制台：

1. 注册Chrome管理控制台。 您需要获取Chrome管理控制台的许可证。 联系人 [Google支持](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995) 有关更多信息，请参阅管理Chrome设备设置。
1. 将您的Chrome操作系统设备注册到域，等待15分钟，以便设备与Chrome管理控制台同步。 要了解有关注册Chrome设备的更多信息，请单击 [此处](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. Chrome播放器将显示在Chrome网上商店中。

>[!NOTE]
>
>建议使用设备管理解决方案（如Chrome管理控制台）来部署和管理Chrome操作系统设备。 尽管本文档提供了Chrome管理控制台的实施，但其他供应商也声称提供了类似的功能。 请与设备管理软件的供应商联系。

## 命名Chrome OS Player {#name-chrome}

您可以为Chrome播放器分配一个用户友好的设备名称，从而将分配的设备名称发送到Adobe Experience Manager (AEM)。 此功能不仅允许您为Chrome播放器命名，还允许您轻松分配适当的内容。

>[!NOTE]
>您只能在注册之前选择播放器名称。 注册播放器后，无法再更改播放器名称。

按照以下步骤在Chrome播放器中配置名称：

1. 您可以选择允许AV集成商或IT管理员在企业注册过程中设置资产ID和位置。

   ![图像](/help/user-guide/assets/chrome-device/chrome1.png)

1. 当您注册设备时，将会为您显示选项。

   ![图像](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. 您可以将资产ID设置为企业注册的一部分以及在Chrome管理控制台中。

   ![图像](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >必须在企业注册中注册Chrome播放器，并且必须通过Chrome管理控制台部署Chrome播放器，否则资产ID将返回空白（例如，将chrome作为扩展）。 设备名称仅在注册时记录。 Adobe Experience Manager (AEM)不会接受将来的更改。

### 启用Kiosk模式 {#enabling-kiosk-mode}

按照以下步骤启用Kiosk模式：

1. 登录到Chrome开发人员控制台。

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. 浏览到 **设备管理** > **Chrome管理** > **设备设置**.
1. 向下滚动到 **网亭设置** 并单击 **管理Kiosk应用程序**.

   ![信息亭](assets/kiosk.png)

1. 从Chrome网上应用商店中选择AEM Screens Player。

   >[!NOTE]
   >
   >最近发布的应用程序可能需要大约15分钟才能显示在此列表中。

1. 选择 **AEM Screens Player** 从 **自动启动Kiosk应用程序** 下拉菜单。

   根据网络的不同，更改可能需要几分钟才会生效。 建议重新引导。

#### 正在检查远程设备状态 {#checking-remote-device-status}

1. 登录到Chrome开发人员控制台。
1. 浏览到 **设备管理** > **Chrome设备** 并选择要控制的设备。
1. 单击 **系统活动和故障排除**.
1. 查看 **重新引导设备** 和 **屏幕截图** 设备的属性。 您还可以检查设备状态和运行状况信息。

>[!NOTE]
>
>请注意，这些设置可能会在设备注册后几分钟启用。 每个选项都可能随时间启用。

### 配置Chrome OS播放器的远程配置 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player是一个支持Kiosk的应用程序，它还为Chrome OS播放器启用了远程策略配置。

按照以下步骤配置播放器的各种选项：

1. 登录到Chrome管理控制台。
1. 单击 **设备管理** > **Chrome管理** > **应用程序管理**. AEM Screens Player将显示在列表中。
1. 单击应用程序 **AEM Screens Player**.
1. 单击 **网亭设置** 并选择您的组织(*如果使用测试环境*)。
1. 单击 **上传配置文件** 并上传配置策略(*Json文件*)。
1. 单击“**保存**”。必须重新启动设备才能同步策略。

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

### 策略属性和目的 {#policy-attributes-and-purpose}

下表总结了策略及其功能。

| **策略名称** | **用途** |
|---|---|
| *服务器* | Adobe Experience Manager服务器的URL |
| *分辨率* | Chrome操作系统设备的分辨率 |
| *rebootSchedule* | 重新引导Chrome播放器的计划 |
| *enableAdminUI* | 为技术人员启用Admin UI以在现场配置设备。 在完全配置并投入生产后，设置为false。 |
| *enableOSD* | 为用户启用频道切换器UI以在设备上切换频道。 在完全配置并投入生产后，请考虑将设置为false 。 |
| *enableActivityUI* | 启用可显示下载和同步等活动的进度。 启用以进行故障排除，并在完全配置并投入生产后禁用。 |

>[!NOTE]
>
>策略配置是严格强制实施的，不会在播放器的管理员UI中手动覆盖。 要允许为特定策略手动配置播放器，请不要在 ***策略配置，*** 例如，如果要允许手动配置重新启动计划，请不要指定键 ***rebootSchedule*** 在策略配置中。

### 使用Screens遥控器 {#using-remote-control}

AEM Screens提供远程控制功能。 可在此处详细了解此功能： [屏幕远程控制](implementing-remote-control.md)
