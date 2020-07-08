---
title: 测试和质量保证
seo-title: 针对AEM Screens的测试和质量保证
description: 本页介绍《AEM Screens测试和质量保证最佳实践指南》
seo-description: 本页介绍《AEM Screens测试和质量保证最佳实践指南》
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---


# 测试和质量保证 {#testing-quality}

>[!NOTE]
>
>本活动的典型利益相关方是A/V集成商。

随着数字标牌网络的实际部署越来越接近，我们应制定测试和QA计划，针对网络的每个元素，包括所有硬件组件、所有软件组件和所有网络组件。
在此阶段，整个测试系统都要建立并全面测试。

应创建一个清单，它标识所有以前定义的KPI并根据这些KPI衡量可交付内容。

>[!NOTE]
>
>此阶段还应用作创建安装和用户指南的工具，以后可随设备一起提供并保存在现场以供将来参考。

应考虑以下要素：

## 1.机械考虑 {#mechanical-considerations}

建议考虑以下机械问题：

* 显示器安装
* 播放器安装
* 通风
* 外围设备附件
* 电缆管理
* 设备联网

## 2.软件注意事项 {#software-considerations}

建议考虑以下软件事项：

* 设备注册
* 媒体发布
* 播放
* 数据库依赖关系（以前定义）


## 3.设备管理注意事项 {#device-management-considerations}


AEM Screens包含一个设备控制中心模块，该模块允许管理Screens播放器应用程序端点。

这是指已安 *装Screens* 播放器应用程序并已注册到AEM实例的任何播放器硬件设备。
此模块允许您：

1. 监视播放器应用程序错误日志
1. 管理远程屏幕截图
1. 管理内容下载
1. 管理应用程序重启问题

要详细了解设备控 ***制中心***，请参阅《AEM Screens用 [户指南》中的“Troubleshooting Device Control](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) Center(设备控 **制中心故障排除)**”。

>[!CAUTION]
>
> 您不应使用设备控制中心来：
>
> 1. 安装播放器应用程序的新版本
> 1. 监视系统级资源
> 1. 系统级错误疑难解答
> 1. 允许远程桌面干预



>[!NOTE]
>
> Adobe建议所有部署都应使用专用的第三方设备管理平台。

选择的特定平台取决于许多因素，包括 ***目标操作******系统、项*** 目要 ***求和***&#x200B;终点数。

以下是几个示例：

* Google Chrome设备管理
* TeamViewer
* AirWatch
* 42Gears
* 专有AV集成商中间件
