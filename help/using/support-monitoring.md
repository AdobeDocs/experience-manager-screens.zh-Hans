---
title: 支持监控
description: 了解AEM Screens支持监控最佳实践指南。
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
TQID: https://experienceleague.adobe.com/uqtkwa1zcJ58tJOxWT0gWkOhAM-C-5zEdcFLjrHa1-Q
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 266
ht-degree: 0%

---

# 支持监控 {#support-monitoring}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

本节提供了与管理数字标牌项目中的设备和内容异常相关的最佳实践。

支持监控包括：

* **设备监控**
* **内容监控**

## 内容监控 {#content-monitoring}

通过内容监控，您可以排除与未在屏幕上正确显示内容相关的问题：

1. 如果遇到空白屏幕问题：

   * 查看&#x200B;*预览*，以便查看频道是否显示黑屏。
   * 在笔记本电脑上注册一个&#x200B;*本地Chrome播放器*（作为扩展）到该显示屏，并查看它是否显示黑屏。
   * 右键单击并检查并检查&#x200B;*适用的日志*。

   此外，如果本地播放器上未出现问题，但设备出现问题：

   * 检查该设备上可能有问题的&#x200B;*媒体类型*（正在使用），并确认内容是否已成功本地下载（管理UI清除通道缓存）。
   * 在票证中包含任何&#x200B;*设备日志*&#x200B;以进行快速故障排除。
   * 从AEM中&#x200B;*收集设备日志*。

## 设备监控 {#device-monitoring}

如果遇到空白屏幕问题，则设备监视与物理设备监视相关：

1. 如果遇到空白屏幕问题：

   * 检查&#x200B;*显示区*&#x200B;是否已通电。
   * 检查&#x200B;*计算机*&#x200B;是否已开机并正在发送信号。
   * 右键单击，检查并检查&#x200B;*适用的日志*。

