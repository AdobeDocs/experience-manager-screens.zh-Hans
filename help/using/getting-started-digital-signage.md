---
title: '[!UICONTROL AEM Screens]的数字标牌基础知识'
description: 了解数字标牌项目的基础知识。
exl-id: e3913be2-9028-4773-a034-e16924a71e04
TQID: https://experienceleague.adobe.com/w0fVaYNPs2emLyL377rLTXLZRcXd05B56FtIn3Yjoqg
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 464
ht-degree: 0%

---

# 数字标牌项目的基础知识 {#basics-digital-signage}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

在深入探讨AEM Screens实施的最佳实践之前，务必要将该项目视为一个数字标牌项目，而不是传统的软件开发项目。

本节提供了有关对AEM Screens项目实施至关重要的主要关键元素的建议。

## 数字标牌中的关键元素 {#key-elements}

数字标牌项目中的&#x200B;*关键元素*&#x200B;包括：

![](/help/assets/Elements-Revised.png)

在实施数字标牌项目之前，定义关键元素至关重要：

1. **硬件**

   硬件定义了哪些硬件组件适合您的数字标牌项目实施：
   * 设备是否有足够的存储空间来离线运行体验的所有变体？
   * 是否允许视频电缆的类型和长度？ 设备是否同时支持所需分辨率（HD、FullHD、`4K`等）以及我计划部署的视频编解码器（h.264、h.265等）
   * 使用物理铜线
   * 屏幕大小
   * 屏幕数量
      * 方向
      * 宽高比
      * 分辨率首选项

1. **连接**

   连通性强调以下问题：
   * 网络（蜂窝或wi-fi）还是独立？
      * 是否必须允许USB内容更新？
      * 是否必须允许使用数据收集？

1. **安装**

   安装包括：
   * 显示：横向或纵向
   * 如何安装屏幕？
      * 纵向方向与横向方向
      * 全套住房
      * 盖板
   * 夹具支架
   * 人员：负责安装设备并将其连接到网络
   * 电源与固定装置相隔多远？
   * 物理面板与实际设备有多远？

1. **内容**

   内容包括：
   * 单区域还是多区域？
      * 屏幕上同时有多少媒体资产？
      * 交互式应用程序有多少页？
      * 定义UI循环
      * 数据驱动的内容？
   * 版本控制

1. **交互式**

   交互式包括：
   * 首选的触摸屏类型？（电阻、电容、多点触控）？
      * 按键按下
      * 手势
   * 数据触发(I/O)？
      * 发送/接收串行命令（触点关闭、PLC等）
      * 传入数据进入屏幕(RSS)或触发内容
      * RFID/NFC/蓝牙/iBeacon
      * 外部服务（天气、交通）

1. **环境**

   环境强调：
   * 显示位置？
      * 内部与外部
      * 无法联系或直接接触
   * 特别临时要求？
   * 蓄意破坏证据？
   * 高环境光？ 强烈的反差？

1. **维护**

   维护侧重于：

   * 是否需要安装指南和用户指南？
   * 您是否会在发货前配置（编程）设备？
   * 是否必须捕获每个序列号以进行跟踪？
   * 是否有任何备用电源要求（不间断电源）？
   * 如何部署系统更新？ 如何远程监控设备？ 是否需要MDM解决方案？

