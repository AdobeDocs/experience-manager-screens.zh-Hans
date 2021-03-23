---
title: 设备控制中心故障排除
seo-title: 监视屏幕
description: 可查看本页以使用“设备”仪表板监视Screens播放器活动和设备的性能并排除故障。
seo-description: 可查看本页以使用“设备”仪表板监视Screens播放器活动和设备的性能并排除故障。
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
feature: 数字标牌、内容、播放器
role: 开发人员
level: 中间
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 2%

---


# 设备控制中心{#troubleshooting-device-control-center}故障排除

您可以使用设备仪表板监视Screens播放器活动和设备的性能并排除故障。 本页提供了有关如何监视和解决Screens播放器和已分配设备的性能问题的信息。

## 从设备控制中心{#monitor-and-troubleshoot-from-device-control-center}进行监视和疑难解答

您可以监视活动，并因此使用设备仪表板对Screens播放器进行疑难解答。

### 设备仪表板{#device-dashboard}

请按照以下步骤导航到设备仪表板:

1. 从您的项目导航到设备仪表板，例如&#x200B;***测试项目*** —> ***设备***。

   从操作栏中选择&#x200B;**设备**&#x200B;和&#x200B;**设备管理器**。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 列表显示已分配和未分配的设备，如下图所示。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. 选择设备(**NewTestDevice**)，然后单击操作栏中的&#x200B;**仪表板**。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. 该页显示设备信息、活动和设备详细信息，允许您监视设备活动和功能。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### 监视设备活动{#monitor-device-activity}

**活动**&#x200B;面板显示屏幕播放器的上次ping及时间戳。 最后一个ping对应于设备上次联系服务器的时间。

![chlimage_1](assets/chlimage_1.png)

此外，单击&#x200B;**活动**&#x200B;面板右上角的&#x200B;**收集日志**&#x200B;以视图播放器的日志。

### 更新设备详细信息{#update-device-details}

检查&#x200B;**设备详细信息**&#x200B;面板，以视图设备IP、存储使用情况、固件版本以及设备的播放器正常运行时间。

![chlimage_1-1](assets/chlimage_1-1.png)

此外，单击&#x200B;**清除缓存**&#x200B;和&#x200B;**更新**&#x200B;可清除设备缓存，并从此面板分别更新[固件](screens-glossary.md)版本。

此外，单击&#x200B;**...**&#x200B;从&#x200B;**设备详细信息**&#x200B;面板的右上角，重新启动或刷新播放器的状态。

![chlimage_1-2](assets/chlimage_1-2.png)

### 更新设备信息{#update-device-information}

检查&#x200B;**设备信息**&#x200B;面板以视图配置更新、设备型号、设备操作系统和外壳信息。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

此外，单击(**...**)，以视图属性或更新设备。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

单击&#x200B;**属性**&#x200B;以视图&#x200B;**设备属性**&#x200B;对话框。 您可以编辑设备标题或选择&#x200B;**Manual**&#x200B;或&#x200B;**Automatic**&#x200B;进行配置更新的选项。

>[!NOTE]
>
>要进一步了解与设备的自动或手动更新相关的事件，请参阅[管理渠道](managing-channels.md)中&#x200B;***设备仪表板***&#x200B;的自动与手动更新部分。

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### 视图 Player屏幕截图{#view-player-screenshot}

您可以从&#x200B;**播放器屏幕截图**&#x200B;面板中视图设备中的播放器屏幕截图。

单击(**...**)，并选择&#x200B;**刷新屏幕快照**&#x200B;以视图正在运行的播放器的快照。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 管理首选项{#manage-preferences}

通过&#x200B;**PREFERENCES**&#x200B;面板，用户可以更改设备的&#x200B;**管理UI**、**渠道切换器**&#x200B;和&#x200B;**远程调试**&#x200B;的首选项。

>[!NOTE]
>要进一步了解这些选项，请参阅[AEM Screens Player](working-with-screens-player.md)。

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

此外，单击右上角的&#x200B;**设置**&#x200B;以更新设备首选项。 您可以更新以下首选项：

* **服务器 URL**
* **分辨率**
* **重新启动计划**
* **Max No.要保留的日志文件**
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

## OSGi设置{#troubleshoot-osgi-settings}疑难解答

您需要启用空推荐人以允许设备向服务器发布数据。 例如，如果禁用了空的推荐人属性，则设备无法向后发布屏幕截图。

目前，只有在OSGi配置中启用了&#x200B;*Apache Sling推荐人过滤器允许空*&#x200B;时，这些功能中的某些功能才可用。 仪表板可能会显示警告，指出安全设置可能会阻止某些功能正常工作。

请按照以下步骤启用Apache Sling推荐人过滤器允许空

1. 导航到&#x200B;**Adobe Experience Manager Web控制台配置**，即`https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`。
1. 选中&#x200B;**allow.empty**&#x200B;选项。
1. 单击&#x200B;**保存**。

![chlimage_1-3](assets/chlimage_1-3.png)

### 推荐 {#recommendations}

以下部分建议监视网络链接、服务器和播放器，以了解运行状况并对问题做出响应。

AEM提供以下内置监控：

* *5* 秒钟表示AEM Screens播放器正在运行。
* *播放* 器中显示播放器中当前显示的内容的屏幕快照。
* 播放器上安装的&#x200B;*AEM Screens Player固件*&#x200B;版本。
* *播放器* 上的免费存储空格。

Recommendations用于第三方软件的远程监控：

* 播放器上的CPU使用。
* 检查AEM Screens Player进程是否正在运行。
* 远程重新启动/重新启动播放器。
* 实时通知。

建议以允许远程登录诊断问题和重新启动播放器的方式部署播放器硬件和操作系统。

#### 其他资源 {#additional-resources}

请参阅[视频播放配置和疑难解答](troubleshoot-videos.md)以调试和疑难解答在您的渠道中播放的视频。
