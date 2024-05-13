---
title: AEM Screens通知服务
description: 详细了解如何监控AEM Screens的设备活动。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# AEM Screens通知服务{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens通知服务*** 描述了监控设备活动。

本节涵盖以下主题：

* **概述**
* **配置电子邮件设置**
* **电子邮件通知**
* **示例用例**

<!-- OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3.2 Feature Pack 3 or AEM 6.4.1 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. After you have permissions you can download it from Package Share. -->

## 概述 {#overview}

***AEM Screens通知服务*** 如果AEM Screens Player在配置的时间内未执行ping操作，管理员将收到电子邮件。

可在OSGi Web控制台中配置此服务。

## 配置电子邮件设置 {#configuring-email-settings}

按照以下步骤配置电子邮件通知设置：

1. 打开 **Adobe Experience Manager Web控制台配置**.
1. 打开 **Screens设备电子邮件监控服务**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 定义以下字段，以便配置电子邮件的设置：

   **设备路径** 输入要监视的屏幕项目的路径。 路径通常为 `/home/users/screens/<Name of your project>`.

   例如，如果项目为 **`We.Retail`**，使用项目路径作为 ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >指定设备用户所在的项目路径。

   **计划频率**  — 指定此监视器应发送电子邮件的时间（例如，下午5:00或17:00）或频率（以小时为单位，例如，1）。

   **Ping超时**  — 此字段指定间隔（以分钟为单位），在此间隔后设备应被视为不可访问。

   **SMTP服务器**  — 指定用于发送电子邮件的SMTP服务器。

   **SMTP端口**  — 输入SMTP端口。

   **使用TLS**  — 传输层安全性(TLS)允许您使用与SMTP服务器的安全通信。

   Adobe建议您使用TLS安全地连接到公司邮件服务器。 请与邮件管理员联系以获取相应的值。

   **用户名**  — 指定用于发送电子邮件的用户名。

   **密码**  — 指定发送电子邮件的密码。

   **收件人**  — 指定收件人的电子邮件地址。

   >[!NOTE]
   >
   >您只能输入一个电子邮件地址。 要发送批量电子邮件，请创建包含相关用户的组或通讯组列表。

1. 单击 **保存** 要通过电子邮件为AEM Screens设备配置监视器活动，请执行以下操作。

## 电子邮件通知 {#email-notification}

在设置电子邮件通知的配置后，您将收到一封电子邮件通知，其中包含指向报告为不活动状态的实际设备的链接。

访问该链接会将您直接导航到设备仪表板。

仅当满足以下条件时才发送电子邮件：

* 在给定的ping超时内，至少有一个设备未执行ping操作，并且
* 在生成电子邮件时仍未发出ping命令。

### 示例用例 {#example-use-cases}

以下示例介绍了一些场景，以供从Screens设备电子邮件监视服务配置属性时参考。

**场景1**

将计划频率设置为1:00 A.M. ， ping超时设置为60。 然后，如果您的AEM Screens设备在下午12:00到1:00之间未执行ping操作，则会收到电子邮件通知，确认设备处于非活动状态。

**场景2**

将计划频率设置为1，将ping超时设置为60。 然后，如果您的AEM Screens设备没有在一天中的任意特定时间立即ping通，您将收到一封电子邮件通知，以确认设备处于非活动状态。
