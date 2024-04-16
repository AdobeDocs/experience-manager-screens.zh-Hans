---
title: AEM Screens中对视频的缩略图支持
description: 了解如何在AEM Screens中为视频添加缩略图支持。
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 2%

---

# 视频支持缩略图 {#thumbnail-support-videos}

## 简介 {#introduction}

内容作者可以定义视频的缩略图，以便在相应团队最终确定实际视频时，将图像用作占位符并正确测试内容播放和定位。 在视频播放失败时，也可以使用该图像。

在视频组件上添加对缩略图图像的支持，可让客户在渠道中正确添加包含实际内容的有效组件，并在交付视频之前执行任何定位配置。

>[!NOTE]
>如果在播放器上出现视频播放失败，则播放缩略图图像（如果在视频组件上设置）。 这样，您就可以将所需的消息（通过播放内容）传递给受众，而不是完全跳过该消息。

缩略图支持允许您：

* 当视频尚未准备就绪，或您不需要测试播放器上的大型资产下载时，准备渠道体验

* 设置回退机制，以防设备上出现播放问题。

## 在视频中使用缩略图 {#using-thumbnails}

请按照以下步骤在视频中使用缩略图：

1. 导航到现有AEM Screens渠道或创建渠道。

1. 选择渠道并选择 **编辑** 从操作栏中。

   ![图像](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. 添加或编辑现有视频组件，如下图所示。

   ![图像](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. 选择视频，然后选择 *扳手* 图标。

   ![图像](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. 此 **视频** 对话框打开，您可以在其中查看 **缩略图** 放置区域。

   ![图像](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. 将图像从资产选取器拖放到 **缩略图** 放置区域并选择 **完成**.

   ![图像](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. 选择 **预览**.

1. 如果已在组件上设置视频，则会播放视频。 如果未设置并且设置了缩略图，则会播放缩略图。 否则，该组件被视为未配置并被跳过。

## 在视频中使用缩略图时支持的用例 {#understand-use-case}

视频中的缩略图支持以下用例：

* 跳过未设置视频组件。

* 仅具有缩略图集的视频组件播放缩略图。

* 同时具有视频（如果视频具有正确的演绎版）和缩略图集的视频组件将播放视频。

* 如果存在播放错误，包含视频集的视频组件将播放缩略图，如果未配置缩略图，将跳过到下一项。
