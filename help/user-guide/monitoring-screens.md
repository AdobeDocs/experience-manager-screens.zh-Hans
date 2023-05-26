---
title: 设备控制中心故障诊断
seo-title: Monitoring Screens
description: 按照此页面进行操作，以使用Device仪表板对Screens播放器活动和设备的性能进行监视和故障排除。
seo-description: Follow this page to monitor and troubleshoot performance for your Screens player activity and device usingtheDevice dashboard.
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 2%

---

# 设备控制中心故障诊断 {#troubleshooting-device-control-center}

您可以使用设备仪表板监控并排除Screens播放器活动和设备的性能。 本页提供了有关如何监视和疑难解答Screens播放器和分配的设备的感知性能问题的信息。

## 从设备控制中心进行监控和故障排除 {#monitor-and-troubleshoot-from-device-control-center}

您可以使用Device Dashboard监控该活动，从而排除Screens播放器的故障。

### 设备功能板 {#device-dashboard}

按照以下步骤导航到设备仪表板：

1. 从项目中导航到设备仪表板，例如， ***测试项目*** —> ***设备***.

   选择 **设备** 和 **设备管理器** 操作栏中的。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 该列表显示了已分配和未分配的设备，如下图所示。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. 选择设备(**NewTestDevice**)，然后单击 **仪表板** 操作栏中的。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. 该页面显示设备信息、活动，以及允许您监视设备活动和功能的设备详细信息。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### 监控设备活动 {#monitor-device-activity}

此 **活动** 面板显示带有时间戳的screens播放器的最后一次ping。 上次ping对应于设备上次与服务器联系的时间。

![chlimage_1](assets/chlimage_1.png)

此外，单击 **收集日志** 从右上角 **活动** 面板以查看播放器的日志。

### 更新设备详细信息 {#update-device-details}

查看 **设备详细信息** 用于查看设备的设备IP、存储使用情况、固件版本和播放器正常运行时间的面板。

![chlimage_1-1](assets/chlimage_1-1.png)

此外，单击 **清除缓存** 和 **更新** 清除设备的缓存并更新 [固件](screens-glossary.md) 版本。

此外，单击 **...** 从右上角 **设备详细信息** 用于重新启动或刷新播放器状态的面板。

![chlimage_1-2](assets/chlimage_1-2.png)

### 更新设备信息 {#update-device-information}

查看 **设备信息** 用于查看配置更新、设备型号、设备操作系统和shell信息的面板。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

此外，单击(**...**)，以查看属性或更新设备。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

单击 **属性** 查看 **设备属性** 对话框。 您可以编辑设备标题或选择用于配置更新的选项 **手动** 或 **自动**.

>[!NOTE]
>
>要了解有关设备自动或手动更新相关事件的更多信息，请参阅部分 ***从设备仪表板进行自动更新与手动更新*** 在 [管理渠道](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### 查看播放器屏幕快照 {#view-player-screenshot}

您可以从设备查看播放器屏幕快照 **播放器屏幕快照** 面板。

单击(**...**)，然后选择 **刷新屏幕快照** 查看正在运行的播放器的快照。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 管理首选项 {#manage-preferences}

此 **首选项** 允许用户更改首选项 **管理员UI**， **渠道切换器**、和 **远程调试** 设备名称。

>[!NOTE]
>要了解有关这些选项的更多信息，请参阅 [AEM Screens Player](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

此外，单击 **设置** 更新设备首选项。 您可以更新以下首选项：

* **服务器 URL**
* **解决方法**
* **重新启动计划**
* **最大数量 要保留的日志文件**
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

## OSGi设置疑难解答 {#troubleshoot-osgi-settings}

您需要启用空反向链接，以允许设备向服务器发布数据。 例如，如果禁用了空反向链接属性，则设备无法发布屏幕快照。

目前，这些功能中的某些功能仅在 *Apache Sling引用过滤器允许为空* 在OSGi配置中启用。 仪表板可能会显示一条警告，指出安全设置可能会阻止这些功能中的某些功能正常工作。

按照以下步骤启用Apache Sling引用过滤器允许为空

1. 导航到 **Adobe Experience Manager Web控制台配置**，即， `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. 查看 **allow.empty** 选项。
1. 单击“**保存**”。

![chlimage_1-3](assets/chlimage_1-3.png)

### 推荐 {#recommendations}

以下部分建议监控网络链接、服务器和播放器，以了解运行状况并对问题做出反应。

AEM提供针对以下各项的内置监控：

* *心率* 每5秒显示一次，以指示AEM Screens Player正在运行。
* *屏幕快照* 播放器中的播放，其中显示当前在播放器上显示的内容。
* 此 *AEM Screens播放器固件* 版本。
* *可用存储空间* 在播放器上。

使用第三方软件实现远程监控的Recommendations：

* 播放器上的CPU使用情况。
* 检查AEM Screens Player进程是否正在运行。
* 远程重新启动/重新引导播放器。
* 实时通知。

建议以允许远程登录诊断问题和重新启动播放器的方式部署播放器硬件和操作系统。

#### 其他资源 {#additional-resources}

参见 [视频播放配置和故障排除](troubleshoot-videos.md) 调试和排除频道中播放的视频故障。
