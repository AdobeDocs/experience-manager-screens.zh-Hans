---
title: 测试和质量保证
seo-title: Testing and Quality Assurance for AEM Screens
description: 此页面介绍了AEM Screens最佳实践的测试和质量保证指南
seo-description: The page describes Testing and Quality Assurance for AEM Screens Best Practices Guide
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 2%

---

# 测试和质量保证 {#testing-quality}

>[!NOTE]
>此活动的典型利益相关者是A/V集成商。

随着我们越来越接近数字标牌网络的实际部署，我们应制定一个测试和QA计划，以解决网络的每个元素，包括所有硬件组件、所有软件组件和所有网络组件。
在这一阶段，应建立并全面测试整个测试系统。

应创建一个清单，该清单可识别之前定义的所有关键绩效指标，并根据这些指标衡量可交付成果。

>[!NOTE]
>
>此阶段还应该用作创建安装和用户指南的工具，该指南以后可以随设备一起提供，并保留在现场以供将来参考。

应考虑以下元素：

## 1.机械方面的考虑 {#mechanical-considerations}

建议采取以下机械注意事项：

* 显示器安装
* 播放器安装
* 通风
* 外围设备附件
* 电缆管理
* 设备联网

## 2.软件注意事项 {#software-considerations}

建议注意以下软件注意事项：

* 设备注册
* 媒体发布
* 播放
* 数据库依赖关系（以前定义）


## 3.设备管理注意事项 {#device-management-considerations}

AEM Screens包括设备控制中心模块，用于管理Screens播放器应用程序端点。

这指任何 *播放器* 安装了Screens播放器应用程序并注册到AEM实例的硬件设备。
利用此模块，您可以：

1. 监控播放器应用程序错误日志
1. 管理远程屏幕截图
1. 管理内容下载
1. 管理应用程序重启问题

详细了解 ***设备控制中心***，请参阅 [设备控制中心故障诊断](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) 在 **AEM Screens用户指南**.

>[!CAUTION]
>
> 您不应使用设备控制中心来：
> 1. 安装播放器应用程序的新版本
> 1. 监视系统级别资源
> 1. 系统级错误故障诊断
> 1. 允许远程桌面干预



>[!NOTE]
>
> Adobe建议在所有部署中都使用专用的第三方设备管理平台。

选择的特定平台取决于多种因素，包括 ***目标操作系统***， ***项目要求*** 和 ***端点数***.

以下示例很少：

* Google Chrome设备管理
* TeamViewer
* AirWatch
* 42Gears
* 专有AV Integrator中间件
