---
title: AEM Screens Notifications Service
seo-title: AEM Screens Notifications Service
description: 可查看本页以了解有关如何监视设备活动的更多信息。
seo-description: 可查看本页以了解有关如何监视设备活动的更多信息。
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
feature: 创作屏幕
role: 管理员、开发人员
level: 中间
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 5%

---


# AEM Screens Notifications Service{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens Notifications Service***，介绍可监视设备活动的功能。

本节涵盖以下主题：

* **概述**
* **配置电子邮件设置**
* **电子邮件通知**
* **示例用例**

>[!CAUTION]
>
>此AEM Screens功能仅在您安装了AEM 6.3.2功能包3或AEM 6.4.1屏幕功能包1时可用。
>
>要获取此功能包，您必须联系 Adobe 支持人员并申请访问权限。您获得权限后，就可以从“包共享”下载它。

## 概述 {#overview}

***AEM Screens Notifications*** Service，允许管理员在AEM screens播放器在可配置的时间段内未ping通时接收电子邮件。

此服务可在OSGi Web控制台中配置。

## 配置电子邮件设置{#configuring-email-settings}

请按照以下步骤配置电子邮件通知设置：

1. 打开&#x200B;**Adobe Experience Manager Web控制台配置**。
1. 打开&#x200B;**屏幕设备电子邮件监视服务**。

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 定义以下字段以配置电子邮件的设置：

   **设** 备路径输入要监视的Screens项目的路径。路径通常为`/home/users/screens/<Name of your project>`。

   例如，如果您的项目是&#x200B;**We.Retail**，则您将项目路径用作&#x200B;***/home/users/screens/we-retail***。

   >[!NOTE]
   >
   >指定用户所在的项目路径。

   **计划** 频率指定此监视器发送电子邮件的时间（例如，下午5:00或17:00）或频率（例如，1）（以小时为单位）。

   **Ping超** 时此值指定一个时间间隔（以分钟为单位），在此时间之后，设备将被视为不可访问。

   **SMTP服** 务器指定用于发送电子邮件的SMTP服务器。

   **SMTP** 端口输入SMTP端口。

   **使** 用TLSTransport层安全性(TLS)可以使用与SMTP服务器的安全通信。

   建议使用TLS来安全地连接到公司邮件服务器。 请咨询邮件管理员以了解相应的值。

   **用** 户名指定发送电子邮件的用户名。

   **口** 令指定用于发送电子邮件的口令。

   **收** 件人指定收件人的电子邮件地址。

   >[!NOTE]
   >
   >您只能输入一个电子邮件地址。 要发送批量电子邮件，请与相关用户创建组或分发列表。

1. 单击&#x200B;**保存**，通过电子邮件为AEM Screens设备配置监视器活动。

## 电子邮件通知{#email-notification}

设置电子邮件通知的配置后，您将收到一封电子邮件通知，其中将包含指向实际设备（报告为不活动）的链接。

访问该链接将直接导航到设备仪表板。

仅当至少有一个设备未针对给定的ping超时进行ping，并且在生成电子邮件时仍未ping时，才会发送电子邮件。

### 用例{#example-use-cases}

以下示例介绍了从Screens设备电子邮件监视服务中配置属性的一些参考方案。

**方案1**:

如果您将计划频率设置为上午1:00,ping超时设置为60，则如果Screens设备在中午12:00至下午1:00之间没有ping，您将收到确认设备不活动的电子邮件通知。

**方案2**:

如果您将计划频率设置为1，将ping超时设置为60，则如果Screens设备在一天中的任何特定时间没有ping一次，您将收到确认设备不活动的电子邮件通知。
