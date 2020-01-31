---
title: 视频播放配置和疑难解答
seo-title: 视频疑难解答
description: null
seo-description: 可查看本页以了解如何对视频进行疑难解答。 在将视频上传到DAM并添加渠道时，您可能会遇到视频在Screens播放器中无法播放的问题，本节将介绍如何调试渠道中播放的视频并对视频进行疑难解答。
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
translation-type: tm+mt
source-git-commit: 6abe309a8beb264f1505b6f39d786acc035bad05

---


# 视频播放配置和疑难解答 {#video-playback-configuration-and-troubleshooting}

在将视频上传到DAM并添加渠道时，您可能会遇到视频在Screens播放器中可能无法播放的问题。

以下各节介绍了如何调试和排除在渠道中播放的视频问题。

## DAM演绎版 {#dam-renditions}

将视频上传到渠道后，AEM应开始为其创建一些再现。 您可以在“资产”下查看您的视频。

要观看视频，请执行以下操作：

1. 例如，导航到您的视频 `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`。
1. 单击视频并展开左上角的菜单，然后单击“演 **绎版”**。

应有不同的再现（MP4或M4V）。

如果没有再现，请确保在运行AEM的操作系统上安装了ffmpeg。

>[!CAUTION]
>
>如果没有再现，请确保在运行AEM的操作系统上安装了ffmpeg。
>
>单击 [此处](https://www.ffmpeg.org/download.html) ，安装ffmpeg。

## 视频资产 {#video-assets}

如果在视频下看不到源属性，可能是视频未转码。 如果视频已正确转码，它将显示在功能板中，如下图所示。

检查ffmpeg已安装并且视频配置文件。

![chlimage_1-2](assets/chlimage_1-2.png)

### 检查视频配置文件 {#checking-video-profile}

1. 导航到视 **频配置文件**，即，然后单 `http://localhost:4502/etc/dam/video.html` 击上传 **测试视频**。

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. 上传测试视频，然后单击“ **确定** ”开始转码。

   如果转码失败，请展开ffmpeg输出以了解ffmpeg的控制台输出中的任何错误。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   此外，如果视频转码成功，则可以下载转码文件。

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >在将视频添加到任何渠道之前，请确保为视频转码提供足够的时间（它应显示新标记而不是处理标记）。

### 使用视频组件检查配置文件 {#checking-profile-with-a-video-component}

如果视频组件配置不正确，请检查页面设计中的配置文件列表。

1. 导航到渠道，然后选择“设 **计** ”模式。

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 选择视频并打开“编 **辑** ”对话框。 Open the **Profiles** tab.

   选择不同的配置文件（至少应该有“High Quality H.264”配置文件）。

   ![chlimage_1-7](assets/chlimage_1-7.png)

### 在Web播放器中检查视频 {#checking-the-video-in-the-web-player}

使用 **Web Player**`http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` ，验证在浏览器（Chrome和Safari）中的播放。 Chrome用于Android设备，而Safari是OSX和iOS浏览器。

如果视频未在Safari上运行，则它不会在OSX和iOS播放器中运行。 这可能是编码问题，必须对视频进行重新编码。

按照以下步骤使用DAM工作流创建FullHD再现：

1. 导航到工 *作流模型管理员*，即 `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`。
1. 选择“屏 **幕”“更新资产** ”模型。
1. 单击 **操作栏中的“启动工作流** ”以打开“运行工 **作流** ”对话框。

1. 在有效负荷中选择您的视频 **资产**。
1. 单击“ **运行**”。

>[!NOTE]
>
>允许一些时间创建再现，但在几秒／分钟（取决于视频大小）后，在Safari上重新加载Web播放器。

#### 自动播放策略标志疑难解答 {#troubleshooting-autoplay-policy-flag}

如果AEM Screens播放器拾取视频但不显示，您需要对“自动播放策略”标记进行疑难解答。

请按照以下步骤对Google的自动播放策略标记问题进行疑难解答：

1. 导航到 ***chrome://flags/#autoplay-policy ***
1. 将“自 **动播放策略** ”从“ **默认** ”更改 **为不需要用户手势**

1. 重新启动Web浏览器并更新播放器

>[!NOTE]
>
>要进一步了解使用Chrome中新的自动播放策略获得良好用户体验的最佳实践，请参阅 *Autoplay Policy Changes*(即 `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`)文档。

### 在多个播放器之间同步视频 {#syncing-video-across-multiple-players}

要跨多个设备同步播放视频，您应对视频所属的序列使用绝对策略。

#### 要求 {#requirements}

* 相同的2+播放器
* 理想的相似硬件
* 相同的网络拓扑（播放器连接到NTP服务器，该服务器将调整其内部系统时钟）

#### 设置绝对策略 {#setting-up-the-absolute-strategy}

绝对战略：

* 计算锚点时间（当天的午夜）
* 计算序列的持续时间（其所有项的持续时间总和）
* 在任何时间点，它通过解序列_remaining_time =(current_time - anchor_time)% sequence_duration来计算当前应播放的项目和下一个项目。

请按照以下步骤设置绝对战略：

1. 导航到渠道作者并选择序列组件，如下图所示。
1. 打开其配置对话框。
1. 编辑策 **略** ，添加绝对。

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>播放器的操作系统必须具有相同的时钟。

**在OS x上对齐时钟** 按照以下步骤在OSX上对齐时钟：

1. 在每 **个OSX框上打开“日期和时间** ”首选项
1. 选中 **自动设置日期和时间**
1. 将值0.pool.ntp.org、1.pool.ntp.org、2.pool.ntp.org、3.pool.ntp.org、time.apple.com粘贴到下拉列表中，或只运行 *sudo ntpdate -u -v 0.pool.ntp.org*
1. 启动2+播放器

玩家可能需要一些时间才能开始新的对齐序列。

