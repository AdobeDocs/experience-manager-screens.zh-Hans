---
title: 设备控制中心故障排除
description: 了解如何使用设备仪表板监测和对AEM Screens Player活动和设备的性能进行故障排除。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 0%

---

# 设备控制中心故障排除 {#troubleshooting-device-control-center}

您可以使用设备仪表板监控AEM Screens Player活动和设备的性能并排除其故障。 本页提供了有关如何监视和排除Screens播放器和所分配设备的感知性能问题的信息。

## 从设备控制中心进行监控和故障排除 {#monitor-and-troubleshoot-from-device-control-center}

您可以使用Dashboard监控该活动，从而排除AEM Screens Player故障。

### 设备功能板 {#device-dashboard}

按照以下步骤导航到设备功能板：

1. 从您的项目导航到设备仪表板，例如，***测试项目*** > ***设备***。

   从操作栏中单击&#x200B;**设备**&#x200B;和&#x200B;**设备管理器**。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 该列表显示了已分配和未分配的设备，如下图所示。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. 单击设备(**NewTestDevice**)，然后单击操作栏中的&#x200B;**仪表板**。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. 该页面显示设备信息、活动以及设备详细信息，用于监视设备活动和功能。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### 监控设备活动 {#monitor-device-activity}

**活动**&#x200B;面板显示带有时间戳的AEM Screens Player的最后一次Ping。 上次ping对应于设备上次与服务器联系的时间。

![chlimage_1](assets/chlimage_1.png)

此外，单击&#x200B;**活动**&#x200B;面板右上角的&#x200B;**收集日志**&#x200B;以查看播放器的日志。

### 更新设备详细信息 {#update-device-details}

检查&#x200B;**设备详细信息**&#x200B;面板，以便查看设备的设备IP、存储使用情况、固件版本和播放器正常运行时间。

![chlimage_1-1](assets/chlimage_1-1.png)

此外，单击&#x200B;**清除缓存**&#x200B;和&#x200B;**更新**&#x200B;可清除设备的缓存，并从此面板分别更新[固件](screens-glossary.md)版本。

此外，单击&#x200B;**设备详细信息**&#x200B;面板右上角的&#x200B;**...**&#x200B;以重新启动或刷新播放器的状态。

![chlimage_1-2](assets/chlimage_1-2.png)

### 更新设备信息 {#update-device-information}

检查&#x200B;**设备信息**&#x200B;面板。 您可以在此处查看配置更新、设备型号、设备操作系统和shell信息。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

另外，单击“设备信息”面板右上角的(**...**)以查看属性或更新设备。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

单击&#x200B;**属性**，以便查看&#x200B;**设备属性**&#x200B;对话框。 您可以编辑设备标题或选择配置更新的选项，如&#x200B;**手动**&#x200B;或&#x200B;**自动**。

>[!NOTE]
>
>若要了解有关设备自动或手动更新相关事件的更多信息，请参阅[管理渠道](managing-channels.md)中设备仪表板&#x200B;***的***&#x200B;自动与手动更新部分。

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### 查看播放器屏幕截图 {#view-player-screenshot}

您可以从&#x200B;**播放器屏幕快照**&#x200B;面板查看设备中的播放器屏幕快照。

单击“播放器屏幕快照”面板右上角的(**...**)，然后单击“**刷新屏幕快照**”以查看正在运行的播放器的快照。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 管理首选项 {#manage-preferences}

通过&#x200B;**PREFERENCES**&#x200B;面板，用户可以更改设备的&#x200B;**管理员UI**、**渠道切换器**&#x200B;和&#x200B;**远程调试**&#x200B;的首选项。

>[!NOTE]
>若要了解有关这些选项的更多信息，请参阅[AEM Screens播放器](working-with-screens-player.md)。

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

另外，单击右上角的&#x200B;**设置**&#x200B;以更新设备首选项。 您可以更新以下首选项：

* **服务器URL**
* **解决方法**
* **重新启动计划**
* **最大数量 要保留的日志文件数量**
* **日志级别**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>您可以单击以下任一日志级别：
>
>* **禁用**
>* **调试**
>* **信息**
>* **警告**
>* **错误**

![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## OSGi设置疑难解答 {#troubleshoot-osgi-settings}

启用空反向链接以允许设备向服务器发布数据。 例如，如果禁用empty referrer属性，设备将无法张贴屏幕快照。

目前，这些功能中的某些功能仅在&#x200B;*`Apache Sling Referrer Filter Allow Empty`*&#x200B;在OSGi配置中启用时可用。 仪表板可能会显示警告，指出安全设置可能会阻止这些功能中的某些功能正常工作。

执行以下步骤以启用Apache Sling反向链接过滤器允许为空

1. 导航到&#x200B;**Adobe Experience Manager Web控制台配置**，即`https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`。
1. 选中&#x200B;**allow.empty**&#x200B;选项。
1. 单击&#x200B;**保存**。

![chlimage_1-3](assets/chlimage_1-3.png)

### 推荐 {#recommendations}

以下部分建议监控网络链接、服务器和播放器，以了解运行状况并对问题做出反应。

AEM提供针对以下各项的内置监控：

* 每5秒&#x200B;*一次心率*，表示AEM Screens播放器正在运行。
* 播放器中的&#x200B;*屏幕快照*，显示播放器上显示的内容。
* 播放器上已安装&#x200B;*AEM Screens播放器固件*&#x200B;版本。
* 播放器上的&#x200B;*可用存储空间*。

对使用第三方软件进行远程监控的建议：

* 播放器中的CPU用法。
* 检查AEM Screens Player进程是否正在运行。
* 远程重新启动/重新启动播放器。
* 实时通知。

建议以允许远程登录诊断问题和重新启动播放器的方式部署播放器硬件和操作系统。

#### 其他资源 {#additional-resources}

如果要对频道中播放的视频进行调试和故障排除，请参阅[视频播放配置和故障排除](troubleshoot-videos.md)。
