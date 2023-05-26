---
title: 支持监控
seo-title: Support Monitoring for AEM Screens
description: 本页介绍了《AEM Screens支持监控最佳实践指南》
seo-description: The page describes Support Monitoring for AEM Screens Best Practices Guide
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 支持监控 {#support-monitoring}

本节提供了与管理数字标牌项目中的设备和内容异常相关的最佳实践。

支持监控包括：

* **设备监控**
* **内容监控**

## 内容监控 {#content-monitoring}

内容监控允许您对与屏幕上未正确显示的内容相关的问题进行故障诊断：

1. 如果遇到空白屏幕问题：

   * Check *预览* 查看渠道是否显示黑屏
   * 注册 *本地chrome播放器* （作为扩展）访问该显示屏，并查看该显示屏是否显示黑屏。
   * 右键单击并检查并检查 *适用的日志*.

   此外，如果本地播放器上没有出现这种情况，但设备没有出现这种情况：

   * Check *媒体类型* （正在使用）时，该设备上可能存在问题，此外还要确认内容是否已成功本地下载（管理员UI清除渠道缓存）。
   * 包括任意 *设备日志* 快速疑难解答的票证中。
   * *收集日志* 从AEM设备访问。


## 设备监控 {#device-monitoring}

与监视物理设备相关的设备监视（如果遇到空白屏幕问题）：

1. 如果遇到空白屏幕问题：

   * 检查 *显示* 已通电。
   * 检查 *计算机* 已通电，正在发送信号。
   * 右键单击，检查并检查 *适用的日志*.
