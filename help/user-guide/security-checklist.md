---
title: 安全清单
description: 通过问题和注意事项核对表了解AEM Screens的主要安全领域。
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
TQID: https://experienceleague.adobe.com/ES-ciW55PF5Zzh9zqRYGu-kWbOym8XkLInXmmqga524
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 536
ht-degree: 0%

---

# AEM Screens安全核对清单 {#security-checklist}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

AEM Screens安全核对清单页面描述了关键安全领域，并包含问题和注意事项核对清单。

## 清单表 {#checklist-table}

| **安全区域** | **清单** | **是/否/NA** |
|---|---|---|
| **AEM和Screens软件更新** | **a.** *是否已应用最新的Adobe Experience Manager (AEM) Service Pack？* <br>**b.** *是否已应用最新的AEM Screens功能包？* <br>**c.** *您是否使用[AEM Screens播放器下载](https://download.macromedia.com/screens/)中最新推出的AEM Screens播放器软件？* | |
| **物理安全性** | **a.** *是否已禁用所有不必要的端口？* <br>**b.** *您是否保护了布线和硬件？* <br>**c.** *您是否使用任何容器（如果适用）？* | |
| **网络安全** | **a.** *您的标牌设备是否使用隔离的子网？* <br>**b.** *隔离子网是否允许访问所需的端点，包括AEM、Adobe Analytics或其他所需的服务？* <br>**c.** *您是否使用企业最佳实践来保护您的Wi-Fi？* <br>**d.** *如果使用同步播放，是否仅允许主设备上的WebSocket使用TCP 24503？* <br>**e.** *您是否已取消阻止播放器设备的IP地址范围，以便只有授权设备才能访问创作实例上的注册服务？* | |
| **操作系统安全** | **a.** *您是否已升级到最新版本的操作系统并应用了所有必需的安全修补程序？* <br>**b.** *您是否禁用了所有不必要的服务并删除了不必要的应用程序？* <br>**c.** *您是否已将设备注册到设备管理以强制执行企业策略？* <br>**d.** *你是否已将设备锁定到单个应用程序（播放器）亭？* <br>**e.** *您是否制定了标准操作程序(SOP)来随时间安装操作系统安全更新？*<br>**f.***您是否遵循了正在使用的操作系统（如反恶意软件软件、非管理用户）的安全最佳实践？* | |
| **应用程序安全** | **a.** *您是否已为生产禁用管理UI、渠道切换器和活动UI？* <br>**b.** *您是否已将生产日志级别最小化？* <br>**c.** *您是否使用https连接到AEM？* <br>**d.** *您使用的是CA签名证书还是企业PKI？ （不是自签名证书）*<br>**e.***您是否使用TLS而不是SSL v3？*<br>**f.** *您在注册时是否在设备和AEM上验证注册令牌？*<br> **g.** *您是否对正在使用的数据进行分类，并且设备上不存在PII或PHI？*<br> **小时。** *您是否对正在使用的数据进行分类，并且设备上不存在个人身份信息(PII)或受保护的健康信息(PHI)？*<br> **i.** *您是否已配置监视电子邮件？ 您是否已设置SOP来响应监视电子邮件和处理非呼入设备？* | |
| **访问控制** | **a.** *您是否已在内部识别并管理基于角色的访问控制(RBAC)？* <br>**b.** *您是否遵循了最低权限原则，使用Adobe的最佳实践为作者、管理员和播放器提供了访问权限？* | |

### 下载安全核对清单 {#download-checklist}

要下载AEM Screens安全核对清单，请单击[此处](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf)。

