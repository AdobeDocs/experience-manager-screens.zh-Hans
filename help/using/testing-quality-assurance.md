---
title: 测试和质量Assurance
description: 在最佳实践指南中了解AEM Screens的测试和质量保证。
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
TQID: https://experienceleague.adobe.com/So83gHv7n21zhdoCdWHVf0yswyQuSr1hLWmCA7uHSiE
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 392
ht-degree: 0%

---

# 测试和质量Assurance {#testing-quality}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

>[!NOTE]
>本活动的典型利益相关者是音频/视频集成商。

随着数字标牌网络的部署日益临近，请制定一个测试和QA计划，以解决网络的每个元素的问题，包括所有硬件组件、所有软件组件和所有网络组件。在这个阶段，应该构建整个测试系统并进行全面测试。

应创建一个核对清单，以识别所有以前定义的KPI，并根据它们衡量可交付成果。

>[!NOTE]
>
>此阶段还应该用作创建安装和用户指南的工具。 两者稍后都可以随设备一起发运，并保留在现场以供将来参考。

应考虑以下因素：

## &#x200B;1. 机械注意事项 {#mechanical-considerations}

建议采取以下机械注意事项：

* 显示器安装
* 播放器安装
* 通风
* 外围设备附件
* 电缆管理
* 设备联网

## &#x200B;2. 软件注意事项 {#software-considerations}

建议注意以下软件注意事项：

* 设备注册
* 媒体发布
* 播放
* 数据库依赖关系（以前定义）


## &#x200B;3. 设备管理注意事项 {#device-management-considerations}

AEM Screens包括设备控制中心模块，用于管理Screens播放器应用程序端点。

它是指已安装Screens播放器应用程序并已注册到AEM实例的任何&#x200B;*播放器*&#x200B;硬件设备。通过此模块，您可以：

1. 监控播放器应用程序错误日志
1. 管理远程屏幕截图
1. 管理内容下载
1. 管理应用程序重新启动问题

若要详细了解&#x200B;***设备控制中心***，请参阅&#x200B;**AEM Screens用户指南**&#x200B;中的[设备控制中心疑难解答](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens)。

>[!CAUTION]
>
>请勿使用“Device Control Center（设备控制中心）”执行以下操作：
>
>* 安装播放器应用程序的新版本
>* 监视系统级别的资源
>* 系统级错误疑难解答
>* 允许远程桌面干预


>[!NOTE]
>
> Adobe建议在所有部署中都使用专门的第三方设备管理平台。

所选的特定平台取决于多个因素，包括&#x200B;***目标操作系统***、***项目要求***&#x200B;和&#x200B;***端点数***。

以下是几个示例：

* Google Chrome设备管理
* 团队查看器
* AirWatch
* `42Gears`
* 专有音频/视频集成器中间件

