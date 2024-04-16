---
title: 视频播放配置和故障排除
description: 了解如何在AEM Screens的渠道中调试和排除视频播放故障。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---

# 视频播放配置和故障排除 {#video-playback-configuration-and-troubleshooting}

在将视频上传到DAM并将其添加到渠道时，您可能会遇到视频无法在AEM Screens播放器中播放的问题。

以下部分介绍了如何对渠道中的视频播放进行调试和故障排除。

## DAM演绎版 {#dam-renditions}

将视频上传到渠道后，AEM应开始为其创建一些演绎版。 您可以在Assets下查看视频。

观看视频：

1. 导航到您的视频，例如 `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. 单击视频，展开左上角的菜单，然后单击 **节目**.

应存在不同的演绎版（MP4或M4V）。

如果没有格式副本，请确保在运行AEM的操作系统上安装了ffmpeg。

>[!CAUTION]
>
>如果没有格式副本，请确保在运行AEM的操作系统上安装了ffmpeg。
>
>单击 [此处](https://www.ffmpeg.org/download.html) 以安装ffmpeg。

## 视频资产 {#video-assets}

如果在视频下未看到源属性，则可能是视频未进行反编码。 如果视频进行了正确转码，它将显示在功能板中，如下所示：

请检查ffmpeg是否已安装以及视频配置文件。

![chlimage_1-2](assets/chlimage_1-2.png)

### 正在检查视频配置文件 {#checking-video-profile}

1. 导航至 **视频配置文件**，即， `http://localhost:4502/etc/dam/video.html` 并单击 **上传测试视频**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. 上传测试视频并单击 **确定** 这样你就可以开始转码了。

   如果转码视频失败，请展开ffmpeg输出以了解ffmpeg控制台输出中的任何错误。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   此外，如果视频转码成功，也可以下载转码文件。

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >在将视频添加到任何渠道之前，请确保留出足够的时间对视频进行转码（应显示新标记而不是进行处理）。

### 使用视频组件检查配置文件 {#checking-profile-with-a-video-component}

如果视频组件配置不正确，请检查页面设计中的配置文件列表。

1. 导航到您的渠道，然后单击 **设计** 模式。

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 单击视频并打开 **编辑** 对话框。 打开 **配置文件** 选项卡。

   >[!NOTE]
   >单击不同的配置文件（至少应存在“高质量H.264”配置文件）。

### 在Web播放器中检查视频 {#checking-the-video-in-the-web-player}

使用 **Web播放器** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` 验证浏览器（Chrome和Safari）中的播放。 Chrome用于Android™设备，而Safari则用于OS X和iOS浏览器。

如果视频未在Safari上运行，则它也不会在OS X和iOS播放器中运行。 这可能是编码问题，必须对视频重新编码。

要使用DAM工作流创建FullHD呈现版本，请执行以下操作：

1. 导航至 *工作流模型管理员* 那是 `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. 单击 **屏幕更新资产** 模型。
1. 单击 **启动工作流** 从操作栏中。
1. 从 **运行工作流** 对话框中，单击位于页面顶部的 **有效负荷**.
1. 单击 **运行**.

>[!NOTE]
>
>留出一些时间创建演绎版，但在几秒/分钟（取决于视频大小）后，在Safari上重新加载Web播放器。

#### 自动播放策略标志疑难解答 {#troubleshooting-autoplay-policy-flag}

如果AEM Screens播放器拿起视频但未显示，请对“Autoplay Policy（自动播放策略）”标记进行故障诊断。

请按照以下步骤对Google的自动播放策略标记问题进行故障诊断：

1. 导航到 ***chrome://flags/#autoplay-policy***
1. 更改 **自动播放策略** 从 **默认** 到 **无需用户手势**

1. 重新启动Web浏览器并更新播放器

>[!NOTE]
>
>要详细了解在Chrome中使用新的自动播放策略获得良好用户体验的最佳实践，请参阅文档 *自动播放策略更改* 在 `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### 在多个播放器之间同步视频 {#syncing-video-across-multiple-players}

要在多个设备上同步播放视频，您应该对视频所属的序列使用绝对策略。

#### 要求 {#requirements}

* 相同的2个以上播放器
* 理想相似的硬件
* 相同的网络拓扑（播放器连接到与其内部系统时钟一致的NTP服务器）

#### 设置绝对策略 {#setting-up-the-absolute-strategy}

绝对策略：

* 计算锚记时间（当天午夜）。
* 计算序列的持续时间（其所有项目的持续时间总和）。
* 在任何时间点，它通过求解序列_remaining_time = (current_time - anchor_time) % sequence_duration来计算当前应播放的项目和下一个项目。

请按照以下步骤设置绝对策略：

1. 导航到渠道作者，然后单击序列组件，如下图所示。
1. 打开其配置对话框。
1. 编辑 **策略** 并添加绝对。

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >玩家的操作系统必须有相同的时钟。

**在OS X上调整时钟** 按照以下步骤调整OS X上的时钟：

1. 打开 **日期和时间** 每个OS X框上的首选项
1. Check **自动设置日期和时间**
1. 在下拉列表中粘贴值0.pool.ntp.org、1.pool.ntp.org、2.pool.ntp.org、3.pool.ntp.org、time.apple.com或仅运行 *sudo ntpdate -u -v 0.pool.ntp.org*
1. 启动2个以上的播放器

可能需要一些时间，玩家才会开始新的对齐序列。
