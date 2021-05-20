---
title: 测试和质量保证
seo-title: AEM Screens的测试和质量保证
description: 本页介绍《AEM Screens最佳实践测试和质量保证指南》
seo-description: 本页介绍《AEM Screens最佳实践测试和质量保证指南》
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---

# 测试和质量保证 {#testing-quality}

>[!NOTE]
>A/V集成商是此活动的典型利益相关者。

随着我们越来越接近数字标牌网络的实际部署，我们应该制定测试和QA计划，以满足网络的每个元素，包括所有硬件组件、所有软件组件和所有网络组件。
在此阶段，应构建并全面测试整个测试系统。

应创建一个检查表，以标识之前定义的所有KPI并针对这些KPI衡量交付内容。

>[!NOTE]
>
>此阶段还应用作创建安装和用户指南的工具，以后可随设备一起提供并保存在现场供将来参考。

应考虑以下因素：

## 1.机械注意事项{#mechanical-considerations}

建议考虑以下机械问题：

* 显示器安装
* 播放器安装
* 通风
* 外围设备附件
* 电缆管理
* 设备联网

## 2.软件注意事项{#software-considerations}

建议考虑以下软件注意事项：

* 设备注册
* 媒体发布
* 播放
* 数据库依赖关系（以前定义）


## 3.设备管理注意事项{#device-management-considerations}

AEM Screens包括一个设备控制中心模块，该模块允许管理Screens播放器应用程序端点。

这是指任何&#x200B;*player*硬件设备，该设备已安装Screens播放器应用程序并已注册到AEM实例。
此模块允许您：

1. 监视播放器应用程序错误日志
1. 管理远程屏幕截图
1. 管理内容下载
1. 管理应用程序重新启动问题

要详细了解&#x200B;***设备控制中心***，请参阅&#x200B;**AEM Screens用户指南**&#x200B;中的[设备控制中心](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html)故障排除。

>[!CAUTION]
>
> 您不应使用设备控制中心执行以下操作：
> 1. 安装播放器应用程序的新版本
> 1. 监控系统级资源
> 1. 系统级错误故障诊断
> 1. 允许远程桌面干预



>[!NOTE]
>
> Adobe建议将专用的第三方设备管理平台用于所有部署。

选择的特定平台取决于多个因素，包括&#x200B;***目标操作系统***、***项目要求***&#x200B;和&#x200B;***端点数***。

以下是几个示例：

* Google Chrome设备管理
* TeamViewer
* AirWatch
* 42档
* 专有AV集成商中间件
