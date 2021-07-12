---
title: 安全检查列表
seo-title: 安全检查列表
description: 本页介绍了关键安全领域以及一系列问题和注意事项。
seo-description: 本页介绍安全检查列表
feature: 管理屏幕
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# AEM Screens安全检查列表  {#security-checklist}

AEM Screens安全检查列表页面介绍了关键安全区域，其中包含一系列问题和注意事项。

## 核对清单表 {#checklist-table}

| **安全区** | **核对清单** | **是/否/不适用** |
|---|---|---|
| **AEM和Screens软件更新** | ***a.*** *是否已应用最新的Adobe Experience Manager(AEM)Service Pack?* <br>***b.***  *是否已应用最新的AEM Screens功能包？* <br>***c.*** *您是否在使用AEM Screens Player下载中提供的最新 [AEM Screens Player软件](https://download.macromedia.com/screens/)?* |
| **物理安全** | ***a.*** *是否禁用了所有不必要的端口？* <br>***b.***  *您是否有安全的布线和硬件？* <br>***c.*** *是否使用任何容器（如果适用）？* |
| **网络安全** | ***a.*** *您是否在标记设备中使用独立子网？* <br>***b.***  *隔离子网是否允许访问所需的端点，包括AEM、Adobe Analytics或其他必需服务？* <br>***c.*** *您是否使用企业最佳实践来保护Wi-Fi?* <br>***d.*** *如果使用同步播放，是否只允许在主控设备上使用WebSocket的TCP 24503?* <br>***e.*** *您是否已解除阻止播放器设备的IP地址范围，以便只有经过授权的设备才能在创作时访问注册服务？* |
| **操作系统安全** | ***a.*** *是否已升级到最新版本的操作系统并应用了所有必需的安全修补程序？* <br>***b.*** *您是否禁用了所有不必要的服务并删除了不必要的应用程序？* <br>***c.*** *您是否将设备注册到设备管理中以实施企业策略？* <br>***d.*** *是否将设备锁定到单个应用程序（播放器）kiosk?* <br>***e.*** *您是否已制定标准操作过程(SOP)，以随时间安装操作系统安全更新？*<br>***f.*** *您是否遵循了使用中操作系统的安全最佳实践，例如防恶意软件软件、非管理用户？* |
| **应用程序安全** | ***答：*** *您是否禁用了用于生产的管理员UI、渠道切换器和活动UI?* <br>***b.*** *是否最小化了生产的日志级别？* <br>***c.*** *您是否使用https连接到AEM?* <br>***d.*** *您使用的是CA签名证书还是企业PKI?（不是自签名证书）*<br>***e.*** *您是否使用TLS而不是SSL v3?*<br>***f.*** *注册时，您是否在设备和AEM上验证注册令牌？*<br> ***g.*** *您是否对正在使用的数据进行分类，且设备上不存在PII或PHI?*<br> ***h.*** *您是否已对所使用的数据进行分类，且设备上不存在个人身份信息(PII)或受保护的运行状况信息(PHI)?*<br> ***i.*** *您是否配置了监控电子邮件，并且您有没有SOP来响应监控电子邮件和处理非Ping设备？* |
| **访问控制** | ***a.*** *您是否在内部识别和管理了基于角色的访问控制(RBAC)?* <br>***b.*** *在使用Adobe中的最佳实践为作者、管理员和播放器提供访问权限时是否遵循了最低权限原则？* |

### 下载安全检查列表 {#download-checklist}

要下载AEM Screens安全检查列表，请单击[此处](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf)。
