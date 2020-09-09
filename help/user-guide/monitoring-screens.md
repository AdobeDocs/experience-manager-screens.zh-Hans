---
title: 设备控制中心故障排除
seo-title: 监视屏幕
description: 可查看本页以使用设备活动监视Screens播放器仪表板和设备的性能并对其进行疑难解答。
seo-description: 可查看本页以使用设备活动监视Screens播放器仪表板和设备的性能并对其进行疑难解答。
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 2%

---


# 设备控制中心故障排除 {#troubleshooting-device-control-center}

您可以使用设备活动监视Screens播放器仪表板和设备的性能并进行故障排除。 本页提供了有关如何监视和解决Screens播放器和已分配设备的性能问题的可感知问题的信息。

## 从设备控制中心进行监视和故障诊断 {#monitor-and-troubleshoot-from-device-control-center}

您可以监视活动，并因此使用设备仪表板对Screens播放器进行疑难解答。

### 设备仪表板 {#device-dashboard}

按照以下步骤导航到设备仪表板:

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --> ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 列表显示已分配和未分配的设备，如下图所示。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. 选择设备(**NewTestDevice**)，然后 **单击操作** 栏中的“仪表板”。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. 该页显示设备信息、活动和设备详细信息，允许您监视设备活动和功能。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### 监视设备活动 {#monitor-device-activity}

活动 **面板** 会显示屏幕播放器上次ping的时间戳。 最后一次ping对应于设备上次联系服务器的时间。

![chlimage_1](assets/chlimage_1.png)

此外，单 **击活动** 面板右上角的“收 **集日志** ”以视图播放器的日志。

### 更新设备详细信息 {#update-device-details}

检查“ **设备详细信息** ”面板，视图设备IP、存储使用情况、固件版本以及设备的播放器正常运行时间。

![chlimage_1-1](assets/chlimage_1-1.png)

此外，单 **击清除****缓存和更新** ，清除设备缓存并分别从此面板 [更新固](screens-glossary.md) 件版本。

此外，单击 **“设备详细** 信息”面板右上角的 **** ...以重新启动或刷新播放器的状态。

![chlimage_1-2](assets/chlimage_1-2.png)

### 更新设备信息 {#update-device-information}

检查“ **设备信息** ”面板以视图配置更新、设备型号、设备操作系统和外壳信息。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

此外，单击“设备&#x200B;**信息”面板右上角**(...)以视图属性或更新设备。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

单击 **属性** ，以视图 **设备属性** 对话框。 您可以编辑设备标题或选择“手动”或“自动” **配置** 更 **新选项**。

>[!NOTE]
>
>要进一步了解与设备的自动或手动更新相关的事件，请参阅管理渠道中 ***设备仪表板的自动与手动更*** 新 [一节](managing-channels.md)。

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### 视图播放器屏幕截图 {#view-player-screenshot}

您可以从“播放器屏幕截图”面板视图设备中 **的播放器屏** 幕截图。

单击“播&#x200B;**放器屏幕截图**”面板右上角的(... **)，然后选择“刷** 新屏幕截图”以视图正在运行的播放器的快照。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 管理首选项 {#manage-preferences}

使用 **“首选项** ”面板，用户可以更改管理员UI、 **渠道切**&#x200B;换器和设 **备的远程调****** 试切换器的首选项。

>[!NOTE]
>要进一步了解这些选项，请参阅 [AEM Screens播放器](working-with-screens-player.md)。

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

此外，单击 **右上角** 的“设置”以更新设备首选项。 您可以更新以下首选项：

* **服务器 URL**
* **分辨率**
* **重新启动计划**
* **Max No. 保存的日志文件**
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

您需要启用空推荐人才能允许设备向服务器发布数据。 例如，如果禁用了空推荐人属性，则设备将无法发布屏幕截图。

目前，其中一些功能仅在OSGi配置中 *启用了Apache Sling推荐人过滤器* “允许为空”时可用。 仪表板可能会显示警告，指出安全设置可能会阻止某些功能正常工作。

请按照以下步骤启用Apache Sling推荐人过滤器允许空

1. 导航到 **Adobe Experience ManagerWeb控制台**，即 `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`。
1. 选中 **allow.empty选项** 。
1. 单击&#x200B;**保存**。

![chlimage_1-3](assets/chlimage_1-3.png)

### 推荐 {#recommendations}

以下部分建议监视网络链接、服务器和播放器，以了解运行状况并对问题做出响应。

AEM提供以下内置监视：

* *心跳* （每5秒）表示AEM Screens播放器正在运行。
* *播放器* 的屏幕截图，显示播放器上当前显示的内容。
* 播放 *器上安装的* AEM Screens播放器Firmware版本。
* *播放器上的* “可用存储”空间。

Recommendations公司用于第三方软件的远程监控：

* 播放器上的CPU使用。
* 检查AEM Screens播放器进程是否正在运行。
* 播放器的远程重启／重新启动。
* 实时通知。

建议以允许远程登录诊断问题和重新启动播放器的方式部署播放器硬件和操作系统。

#### 其他资源 {#additional-resources}

请参 [阅视频播放配置和疑难解答](troubleshoot-videos.md) ，以调试在渠道中播放的视频并对视频进行疑难解答。
