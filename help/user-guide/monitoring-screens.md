---
title: 设备控制中心故障排除
seo-title: 监控屏幕
description: 可按照本页，使用“设备”功能板监控Screens播放器活动和设备的性能并排除其故障。
seo-description: 可按照本页，使用“设备”功能板监控Screens播放器活动和设备的性能并排除其故障。
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
feature: 数字标牌、内容、播放器
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 2%

---


# 设备控制中心{#troubleshooting-device-control-center}故障排除

您可以使用设备功能板监控Screens播放器活动和设备的性能并排除其故障。 本页提供了有关如何监控Screens播放器和已分配设备的性能问题并排除其故障的信息。

## 从设备控制中心{#monitor-and-troubleshoot-from-device-control-center}进行监控和故障诊断

您可以使用“设备功能板”监控活动，从而对Screens播放器进行故障诊断。

### 设备功能板{#device-dashboard}

按照以下步骤导航到设备功能板：

1. 从您的项目导航到设备功能板，例如&#x200B;***测试项目*** —> ***设备***。

   从操作栏中选择&#x200B;**设备**&#x200B;和&#x200B;**设备管理器**。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 列表会显示已分配和未分配的设备，如下图所示。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. 选择设备(**NewTestDevice**)，然后单击操作栏中的&#x200B;**功能板**。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. 该页面显示设备信息、活动和设备详细信息，以便您监控设备活动和功能。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### 监视设备活动{#monitor-device-activity}

**Activity**&#x200B;面板显示了Screens播放器的上次Ping操作，其中包含时间戳。 最后一次Ping操作对应于设备上次联系服务器的时间。

![chlimage_1](assets/chlimage_1.png)

此外，单击&#x200B;**Activity**&#x200B;面板右上角的&#x200B;**收集日志** ，以查看播放器的日志。

### 更新设备详细信息{#update-device-details}

查看&#x200B;**设备详细信息**&#x200B;面板，查看设备IP、存储使用情况、固件版本和播放器的正常运行时间。

![chlimage_1-1](assets/chlimage_1-1.png)

此外，单击&#x200B;**清除缓存**&#x200B;和&#x200B;**更新**&#x200B;可清除设备的缓存，并从此面板分别更新[固件](screens-glossary.md)版本。

此外，单击&#x200B;**...**&#x200B;从&#x200B;**设备详细信息**&#x200B;面板右上角的以重新启动或刷新播放器的状态。

![chlimage_1-2](assets/chlimage_1-2.png)

### 更新设备信息{#update-device-information}

检查&#x200B;**设备信息**&#x200B;面板，查看配置更新、设备型号、设备操作系统和外壳信息。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

此外，单击(**...**)来查看设备属性或更新设备。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

单击&#x200B;**属性**&#x200B;以查看&#x200B;**设备属性**&#x200B;对话框。 您可以编辑设备标题或选择&#x200B;**Manual**&#x200B;或&#x200B;**Automatic**&#x200B;作为配置更新选项。

>[!NOTE]
>
>要了解有关设备自动更新或手动更新相关事件的更多信息，请参阅[管理渠道](managing-channels.md)中设备功能板&#x200B;***中的自动更新与手动更新部分***。

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### 查看播放器屏幕截图{#view-player-screenshot}

您可以从&#x200B;**播放器屏幕截图**&#x200B;面板查看设备中的播放器屏幕截图。

单击(**...**)，然后选择&#x200B;**刷新屏幕截图**&#x200B;以查看正在运行的播放器的快照。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 管理首选项{#manage-preferences}

**首选项**&#x200B;面板允许用户更改设备的&#x200B;**管理员UI**、**渠道切换器**&#x200B;和&#x200B;**远程调试**&#x200B;的首选项。

>[!NOTE]
>要了解有关这些选项的更多信息，请参阅[AEM Screens Player](working-with-screens-player.md)。

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

此外，单击右上角的&#x200B;**设置**&#x200B;以更新设备首选项。 您可以更新以下首选项：

* **服务器 URL**
* **分辨率**
* **重新启动计划**
* **Max No.保留**&#x200B;的日志文件
* **日志级别**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>您可以选择以下任一日志级别：
>* **禁用**
>* **调试**
>* **信息**
>* **警告**
>* **错误**


![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## OSGi设置{#troubleshoot-osgi-settings}故障诊断

您需要启用空反向链接，以便设备将数据发布到服务器。 例如，如果禁用了空反向链接属性，则设备将无法发布回屏幕截图。

目前，其中某些功能仅在OSGi配置中启用了&#x200B;*Apache Sling反向链接过滤器允许空*&#x200B;时才可用。 功能板可能显示一条警告，指出安全设置可能会阻止某些功能正常工作。

请按照以下步骤启用Apache Sling反向链接过滤器允许为空

1. 导航到&#x200B;**Adobe Experience Manager Web控制台配置**，即`https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`。
1. 选中&#x200B;**allow.empty**&#x200B;选项。
1. 单击&#x200B;**保存**。

![chlimage_1-3](assets/chlimage_1-3.png)

### 推荐 {#recommendations}

以下部分建议监控网络链接、服务器和播放器以了解运行状况并对问题做出响应。

AEM提供以下内置监控：

* ** 心率为5秒，表示AEM Screens播放器正在运行。
* ** 屏幕截图，显示播放器中当前显示的内容。
* 播放器上安装的&#x200B;*AEM Screens播放器固件*&#x200B;版本。
* *播放器上* 的可用存储空间。

Recommendations用于第三方软件的远程监控：

* 播放器上的CPU使用率。
* 检查AEM Screens Player进程是否正在运行。
* 远程重新启动/重新启动播放器。
* 实时通知。

建议以允许远程登录诊断问题并重新启动播放器的方式部署播放器硬件和操作系统。

#### 其他资源 {#additional-resources}

请参阅[视频播放配置和疑难解答](troubleshoot-videos.md)以调试和解决频道中播放的视频问题。
