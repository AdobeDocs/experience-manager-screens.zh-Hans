---
title: 视频播放配置和故障排除
seo-title: Troubleshooting Videos
description: 按照此页面了解如何对频道中的视频播放进行调试和故障排除。
seo-description: Follow this page to learn how to troubleshoot videos. When you upload a video to the DAM and add it your channel, you might encounter issues that video might not play in Screens player and this section describes how to debug and troubleshoot video playing in your channel.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 0%

---

# 视频播放配置和故障排除 {#video-playback-configuration-and-troubleshooting}

在将视频上传到DAM并将其添加到渠道时，您可能会遇到视频可能无法在Screens播放器中播放的问题。

以下部分介绍了如何对频道中的视频播放进行调试和故障排除。

## DAM演绎版 {#dam-renditions}

将视频上传到渠道后，AEM应开始为其创建一些演绎版。 您可以在Assets下查看视频。

观看视频：

1. 导航到您的视频，例如 `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. 单击视频，展开左上角的菜单，然后单击 **演绎版**.

应存在不同的演绎版（MP4或M4V）。

如果没有演绎版，请确保在运行AEM的操作系统上安装了ffmpeg。

>[!CAUTION]
>
>如果没有演绎版，请确保在运行AEM的操作系统上安装了ffmpeg。
>
>单击 [此处](https://www.ffmpeg.org/download.html) 以安装ffmpeg。

## 视频资产 {#video-assets}

如果在视频下未看到源属性，则可能是视频未经过转码。 如果视频进行了正确转码，它将显示在仪表板中，如下图所示。

请检查ffmpeg是否已安装以及视频配置文件。

![chlimage_1-2](assets/chlimage_1-2.png)

### 正在检查视频配置文件 {#checking-video-profile}

1. 导航到 **视频配置文件**，即， `http://localhost:4502/etc/dam/video.html` 并单击 **上传测试视频**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. 上传测试视频并单击 **确定** 开始转码。

   如果转码失败，请展开ffmpeg输出以了解ffmpeg控制台输出中的任何错误。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   此外，如果视频转码成功，则可以下载转码文件。

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >在将视频添加到任何渠道之前，请确保为视频留出足够的时间进行转码（它应显示新的标记而不是正在处理）。

### 使用视频组件检查配置文件 {#checking-profile-with-a-video-component}

如果视频组件配置不正确，请检查页面设计中的配置文件列表。

1. 导航到您的渠道并选择 **设计** 模式。

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 选择视频并打开 **编辑** 对话框。 打开 **配置文件** 选项卡。

   >[!NOTE]
   >选择不同的配置文件（至少应存在“高质量H.264”配置文件）。

### 在Web播放器中检查视频 {#checking-the-video-in-the-web-player}

使用 **Web播放器** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` 验证浏览器（Chrome和Safari）中的播放。 Chrome用于Android设备，而Safari用于OSX和iOS浏览器。

如果视频未在Safari上运行，它将不会在OSX和iOS播放器中运行。 这可能是编码问题，必须对视频进行重新编码。

按照以下步骤使用DAM工作流创建FullHD呈现版本：

1. 导航到 *工作流模型管理员*，即 `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. 选择 **屏幕更新资产** 型号。
1. 点击 **启动工作流** 以打开 **运行工作流** 对话框。

1. 在中选择您的视频资产 **有效负荷**.
1. 单击 **运行**.

>[!NOTE]
>
>留出一些时间创建演绎版，但在几秒/分钟后（取决于视频大小），在Safari上重新加载Web播放器。

#### 自动播放策略标志疑难解答 {#troubleshooting-autoplay-policy-flag}

如果AEM Screens播放器取下视频但未显示，您需要对自动播放策略标记进行故障排除。

请按照以下步骤对Google的自动播放策略标记问题进行故障诊断：

1. 导航到 ***chrome://flags/#autoplay-policy***
1. 更改 **自动播放策略** 起始日期 **默认** 到 **无需用户手势**

1. 重新启动Web浏览器并更新播放器

>[!NOTE]
>
>要详细了解在Chrome中使用新的自动播放策略获得良好用户体验的最佳实践，请参阅以下文档 *自动播放策略更改*，即， `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### 在多个播放器之间同步视频 {#syncing-video-across-multiple-players}

要在多个设备上同步播放视频，您应该对视频所属的序列使用绝对策略。

#### 要求 {#requirements}

* 相同的2+个播放器
* 理想相似的硬件
* 相同的网络拓扑（播放器连接到与其内部系统时钟一致的NTP服务器）

#### 设置绝对策略 {#setting-up-the-absolute-strategy}

绝对策略：

* 计算锚记时间（当天午夜）
* 计算序列的持续时间（其所有项目的持续时间总和）
* 在任意时间点，它通过求解序列_remaining_time = (current_time - anchor_time) % sequence_duration来计算当前应播放的项目和下一个项目。

请按照以下步骤设置绝对策略：

1. 导航到渠道作者，然后选择序列组件，如下图所示。
1. 打开其配置对话框。
1. 编辑 **策略** 并添加absolute。

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >播放器的操作系统必须具有相同的时钟。

**在OS X上调整时钟** 按照以下步骤调整OSX上的时钟：

1. 打开 **日期和时间** 每个OSX框上的首选项
1. Check **自动设置日期和时间**
1. 在下拉列表中粘贴值0.pool.ntp.org、1.pool.ntp.org、2.pool.ntp.org、3.pool.ntp.org、time.apple.com或直接运行 *sudo ntpdate -u -v 0.pool.ntp.org*
1. 启动2个以上的播放器

在玩家开始新的对齐序列之前，可能需要一些时间。
