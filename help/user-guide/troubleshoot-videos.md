---
title: 视频播放配置和疑难解答
seo-title: 视频疑难解答
description: 请阅读本页，了解如何调试和排查渠道中播放的视频问题。
seo-description: 请阅读本页，了解如何对视频进行故障诊断。 在将视频上传到DAM并将其添加到渠道时，您可能会遇到视频在Screens播放器中无法播放的问题，本节将介绍如何调试渠道中播放的视频并对其进行故障诊断。
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
feature: 渠道，交互式
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 0%

---


# 视频播放配置和疑难解答{#video-playback-configuration-and-troubleshooting}

在将视频上传到DAM并将其添加到渠道时，您可能会遇到视频无法在Screens播放器中播放的问题。

以下各节介绍如何调试和排查渠道中播放的视频问题。

## DAM呈现版本{#dam-renditions}

将视频上传到渠道后，AEM应该开始为其创建一些演绎版。 您可以在资产下查看视频。

要查看视频，请执行以下操作：

1. 导航到您的视频，例如`http://localhost:4502/assets.html/content/dam/we-retail/en/videos`。
1. 单击视频并展开左上角的菜单，然后单击&#x200B;**演绎版**。

应有不同的演绎版（MP4或M4V）。

如果没有呈现版本，请确保在运行AEM的操作系统上安装了ffmpeg。

>[!CAUTION]
>
>如果没有呈现版本，请确保在运行AEM的操作系统上安装了ffmpeg。
>
>单击[此处](https://www.ffmpeg.org/download.html)安装ffmpeg。

## 视频资产{#video-assets}

如果您在视频下未看到源属性，则可能是该视频未被转码。 如果视频经过正确的转码，它将显示在功能板中，如下图所示。

检查已安装ffmpeg和视频配置文件。

![chlimage_1-2](assets/chlimage_1-2.png)

### 正在检查视频配置文件{#checking-video-profile}

1. 导航到&#x200B;**视频配置文件**，即`http://localhost:4502/etc/dam/video.html`，然后单击&#x200B;**上传测试视频**。

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. 上传测试视频并单击&#x200B;**确定**&#x200B;以开始转码。

   如果转码失败，请展开ffmpeg输出以了解ffmpeg控制台输出中的任何错误。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   此外，如果视频转码成功，则可以下载转码文件。

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >在将视频添加到任何渠道之前，请确保为视频提供足够的时间进行转码（它应显示新标记而不是处理标记）。

### 正在使用视频组件{#checking-profile-with-a-video-component}检查配置文件

如果未正确配置视频组件，请检查页面设计中的用户档案列表。

1. 导航到渠道并选择&#x200B;**Design**&#x200B;模式。

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 选择视频并打开&#x200B;**编辑**&#x200B;对话框。 打开&#x200B;**Profiles**&#x200B;选项卡。

   >[!NOTE]
   >选择不同的用户档案（至少“High Quality H.264”用户档案应位于此处）。

### 检查Web播放器中的视频{#checking-the-video-in-the-web-player}

使用&#x200B;**Web Player** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0`验证浏览器（Chrome和Safari）中的播放。 Safari是OSX和iOS浏览器时，Chrome会在Android设备上使用。

如果视频未在Safari上运行，则它将不会在OSX和iOS播放器中运行。 这可能是编码问题，必须对视频进行重新编码。

请按照以下步骤使用DAM工作流创建全高清演绎版：

1. 导航到&#x200B;*工作流模型管理员*，即`http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`。
1. 选择&#x200B;**屏幕更新资产**&#x200B;模型。
1. 单击操作栏中的&#x200B;**启动工作流**&#x200B;以打开&#x200B;**运行工作流**&#x200B;对话框。

1. 在&#x200B;**有效负荷**&#x200B;中选择您的视频资产。
1. 单击&#x200B;**运行**。

>[!NOTE]
>
>需要一些时间来创建演绎版，但在几秒/分钟（取决于视频大小）后，在Safari上重新加载Web播放器。

#### 自动播放策略标志{#troubleshooting-autoplay-policy-flag}疑难解答

如果AEM Screens播放器拿起视频但没有显示，则您需要对自动播放策略标记进行故障诊断。

请按照以下步骤对Google的自动播放策略标记问题进行故障诊断：

1. 导航到&#x200B;***chrome://flags/#autoplay-policy***
1. 将&#x200B;**自动播放策略**&#x200B;从&#x200B;**Default**&#x200B;更改为&#x200B;**不需要用户手势**

1. 重新启动Web浏览器并更新播放器

>[!NOTE]
>
>要详细了解在Chrome中使用新的自动播放策略获得良好用户体验的最佳实践，请参阅&#x200B;*自动播放策略更改*（即`https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`）的文档。

### 在多个播放器之间同步视频{#syncing-video-across-multiple-players}

要跨多个设备同步播放视频，您应对视频所属的序列使用绝对策略。

#### 要求 {#requirements}

* 相同的2+播放器
* 理想相似的硬件
* 相同的网络拓扑（播放器连接到NTP服务器，该服务器将调整其内部系统时钟）

#### 设置绝对策略{#setting-up-the-absolute-strategy}

绝对策略：

* 计算锚点时间（当天的午夜）
* 计算序列的持续时间（其所有项目的持续时间总和）
* 在任何时间点，它通过解sequence _remaining_time =(current_time - anchor_time)% sequence_duration来计算当前应播放的项目和下一个项目。

请按照以下步骤设置绝对策略：

1. 导航到渠道作者并选择序列组件，如下图所示。
1. 打开其配置对话框。
1. 编辑&#x200B;**Strategy**&#x200B;并添加绝对值。

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >玩家的操作系统必须有相同的时钟。

**在OS Xf上对** 齐时钟按照以下步骤在OSX上对齐时钟：

1. 打开每个OSX框上的&#x200B;**Date &amp; Time**&#x200B;首选项
1. 检查&#x200B;**自动设置日期和时间**
1. 将值0.pool.ntp.org、1.pool.ntp.org、2.pool.ntp.org、3.pool.ntp.org、time.apple.com粘贴到下拉菜单中，或者只运行&#x200B;*sudo ntpdate -u -v 0.pool.ntp.org*
1. 启动2+位播放器

球员们可能需要一些时间才能开始新的一致序列。

