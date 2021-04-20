---
title: 安全核对清单
seo-title: 安全核对清单
description: 本页介绍了关键安全领域，并列出了问题和注意事项的清单。
seo-description: 本页介绍安全核对清单
feature: Administering Screens
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---


# AEM Screens安全核对清单{#security-checklist}

AEM Screens安全核对清单页面描述了关键安全领域，其中包含一系列问题和注意事项。

## 清单表{#checklist-table}

| **安全区** | **核对清单** | **是/否/不可用** |
|---|---|---|
| **AEM和Screens软件更新** | ***a.是*** *否已应用最新的Adobe Experience Manager(AEM)服务包？* <br>***b.是***  *否已应用最新的AEM Screens功能包？* <br>***c.您*** *是否正在使用AEM Screens Player下载中最新可 [用的AEM Screens Player](https://download.macromedia.com/screens/)?* |
| **物理安全** | ***答：您*** *是否禁用了所有不必要的端口？* <br>***b.您是***  *否有安全的布线和硬件？* <br>***c.您*** *是否在使用任何容器（如果适用）？* |
| **网络安全** | ***答：您*** *是否在为您的标牌设备使用隔离子网？* <br>***b.隔***  *离子网是否允许访问所需的端点，包括AEM、Adobe Analytics或其他所需服务？* <br>***c.您*** *是否使用企业最佳实践保护了您的Wi-Fi?* <br>***d.如*** *果使用同步播放，是否仅允许主控设备上的WebSocket的TCP 24503?* <br>***e.您*** *是否已解除阻止播放器设备的IP地址范围，以便只有经过授权的设备才能在创作时访问注册服务？* |
| **操作系统安全** | ***a.您*** *是否已升级到最新版本的操作系统并应用了所有必需的安全修补程序？* <br>***b.您是*** *否禁用了所有不必要的服务并删除了不必要的应用程序？* <br>***c.您*** *是否已将设备登记到设备管理以实施企业策略？* <br>***d.您*** *是否已将设备锁定到单个应用程序（播放器）kiosk?* <br>***e.您*** *是否有标准操作过程(SOP)，可随时间安装操作系统安全更新？*<br>***f.您*** *是否在使用中遵循了操作系统的安全最佳实践，如防恶意软件软件、非管理用户？* |
| **应用程序安全性** | ***答：您*** *是否已为生产禁用了管理员UI、渠道切换器和活动UI?* <br>***b.您*** *是否已最小化生产日志级别？* <br>***c.*** *您是否使用https连接到AEM?* <br>***d.*** *您使用的是CA签名证书还是企业PKI?（不是自签名证书）*<br>***e.*** *您是否使用TLS而不是SSL v3?*<br>***f.注*** *册时，您是否在设备和AEM上验证注册令牌？*<br> ***g.您*** *是否对正在使用的数据进行了分类，并且设备上不存在PII或PHI?*<br> ***您是*** *否对正在使用的数据进行了分类，并且设备上不存在个人身份信息(PII)或受保护的健康信息(PHI)?*<br> ***i.您*** *是否配置了监视电子邮件，并且您是否有SOP，用于响应监视电子邮件和处理非ping设备？* |
| **访问控制** | ***a.*** *您是否在内部识别和管理基于角色的访问控制(RBAC)?* <br>***b.您*** *是否遵循了使用Adobe的最佳实践为作者、管理员和播放器提供访问权限时最少权限的原则？* |

### 正在下载安全核对清单{#download-checklist}

要下载AEM Screens安全核对清单，请单击[此处](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf)。