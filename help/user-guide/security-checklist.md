---
title: 安全核对清单
description: 通过问题和注意事项核对表了解AEM Screens的主要安全领域。
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# AEM Screens安全核对清单  {#security-checklist}

AEM Screens安全核对清单页面介绍了关键安全区域，并提供了问题和注意事项核对清单。

## 清单表 {#checklist-table}

| **安全区域** | **清单** | **是/否/不适用** |
|---|---|---|
| **AEM和Screens软件更新** | **答：** *是否已应用最新的Adobe Experience Manager (AEM) Service Pack？* <br>**b.** *是否已应用最新的AEM Screens功能包？* <br>**c.** *您是否在使用最新可用的AEM Screens Player软件，位于 [AEM Screens播放器下载](https://download.macromedia.com/screens/)？* |
| **物理安全性** | **答：** *是否已禁用所有不必要的端口？* <br>**b.** *您是否保护了布线和硬件？* <br>**c.** *您是否使用任何容器（如果适用）？* |
| **网络安全** | **答：** *您的标牌设备是否使用独立子网？* <br>**b.** *隔离子网是否允许访问所需的端点，包括AEM、Adobe Analytics或其他所需的服务？* <br>**c.** *您是否使用企业最佳实践来保护您的Wi-Fi？* <br>**d.** *如果使用同步播放，您只在主设备上允许WebSocket的TCP 24503吗？* <br>**e.** *您是否解除了播放器设备IP地址范围的阻止，以便只有授权设备才能访问创作实例上的注册服务？* |
| **操作系统安全** | **答：** *您是否已升级到最新版本的操作系统并已应用所有必需的安全修补程序？* <br>**b.** *您是否禁用了所有不必要的服务并删除了不必要的应用程序？* <br>**c.** *您是否已将该设备注册到设备管理中以强制执行企业策略？* <br>**d.** *是否已将设备锁定到单个应用程序（播放器）亭？* <br>**e.** *您是否制定了标准操作程序(SOP)来随时间安装操作系统安全更新？*<br>**f.***您是否遵循了正在使用的操作系统（如反恶意软件软件、非管理用户）的安全最佳实践？* |
| **应用程序安全性** | **答：** *是否已为生产禁用管理员UI、渠道切换器和活动UI？* <br>**b.** *您是否已将生产日志级别最小化？* <br>**c.** *您是否使用https连接到AEM？* <br>**d.** *您使用的是CA签名证书还是企业PKI？ （不是自签名证书）*<br>**e.***您是否使用TLS而不是SSL v3？*<br>**f.** *注册时，您是否正在验证设备和AEM上的注册令牌？*<br> **g.** *您是否对正在使用的数据进行过分类，并且设备上不存在任何PII或PHI？*<br> **h.** *您是否对正在使用的数据进行过分类，并且设备上不存在个人身份信息(PII)或受保护的健康信息(PHI)？*<br> **i.** *是否已配置监视电子邮件，以及您是否拥有SOP来响应监视电子邮件和处理非寻呼设备？* |
| **访问控制** | **答：** *您是否拥有内部识别和管理的基于角色的访问控制(RBAC)？* <br>**b.** *您是否遵循了最低权限原则，使用Adobe的最佳实践为作者、管理员和播放器提供了访问权限？* |

### 下载安全核对清单 {#download-checklist}

要下载AEM Screens安全核对清单，请选择 [此处](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).
