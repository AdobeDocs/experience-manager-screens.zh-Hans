---
title: AEM Screens通知服务
seo-title: AEM Screens Notifications Service
description: 请阅读本页，详细了解如何监测设备活动。
seo-description: Follow this page to learn more about how you can monitor device activity.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# AEM Screens通知服务{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens通知服务***，介绍用于监控设备活动的功能。

本节涵盖以下主题：

* **概述**
* **配置电子邮件设置**
* **电子邮件通知**
* **示例用例**

>[!CAUTION]
>
>此AEM Screens功能仅在安装了AEM 6.3.2 Feature Pack 3或AEM 6.4.1 Screens Feature Pack 1时才可用。
>
>要访问此功能包，您必须联系Adobe支持部门并请求获取访问权限。 一旦您拥有权限，就可以从包共享下载它。

## 概述 {#overview}

***AEM Screens通知服务***，允许管理员在AEM screens播放器未在可配置的时间段ping时收到电子邮件。

可在OSGi Web控制台中配置此服务。

## 配置电子邮件设置 {#configuring-email-settings}

按照以下步骤配置电子邮件通知设置：

1. 打开 **Adobe Experience Manager Web控制台配置**.
1. 打开 **Screens设备电子邮件监控服务**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 定义以下字段以配置电子邮件的设置：

   **设备路径** 输入要监视的屏幕项目的路径。 路径通常为 `/home/users/screens/<Name of your project>`.

   例如，如果您的项目是 **We.Retail**，您会将项目路径用作 ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >指定设备用户所在的项目路径。

   **计划频率** 以小时为单位指定此监视器应发送电子邮件的时间（例如，5:00下午或17:00）或频率（例如，1）。

   **Ping超时** 这指定间隔（以分钟为单位），在此间隔后，设备应被视为不可访问。

   **SMTP服务器** 指定用于发送电子邮件的SMTP服务器。

   **SMTP端口** 输入SMTP端口。

   **使用TLS** 传输层安全性(TLS)使您能够使用与SMTP服务器的安全通信。

   建议使用TLS安全地连接到公司邮件服务器。 请与邮件管理员联系以获取适当的值。

   **用户名** 指定用于发送电子邮件的用户名。

   **密码** 指定发送电子邮件的密码。

   **收件人** 指定收件人的电子邮件地址。

   >[!NOTE]
   >
   >您只能输入一个电子邮件地址。 要发送批量电子邮件，请创建包含相关用户的组或通讯组列表。

1. 单击 **保存** 以通过电子邮件为AEM Screens设备配置监视器活动。

## 电子邮件通知 {#email-notification}

设置电子邮件通知的配置后，您将收到一封电子邮件通知，其中包含指向被报告为不活动的实际设备的链接。

访问该链接会将您直接导航到设备仪表板。

仅当至少有一台设备在给定的ping超时内未执行ping操作且在生成电子邮件时仍未执行ping操作时，才会发送电子邮件。

### 示例用例 {#example-use-cases}

以下示例介绍了一些场景，以供从Screens设备电子邮件监视服务配置属性时参考。

**场景1**：

如果将计划频率设置为凌晨1:00，将ping超时设置为60，那么如果Screens设备在晚上12:00到下午1:00之间未执行ping操作，则您将收到一封电子邮件通知，确认设备处于非活动状态。

**场景2**：

如果将计划频率设置为1，将ping超时设置为60，那么如果您的Screens设备在一天的任何特定时间都未执行一次ping操作，则您将收到一封电子邮件通知，确认设备处于非活动状态。
