---
title: 应用过渡
seo-title: 应用过渡
description: 可查看本页以了解如何将过渡应用到Screens项目。
seo-description: 可查看本页以了解如何将过渡应用到Screens项目。
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 389a44e3f6175e0a43a6e99edd3048f2b8455d0b

---


# 应用过渡 {#applying-transitions}

本节介绍如何在渠道中的不同资 **产** （图像和视频）和嵌入式序列之间应用过渡组件。


>[!CAUTION]
>
>要详细了解“过渡”组件的属 **性** ，请参阅“过渡 [”](adding-components-to-a-channel.md#transition)。

## 向渠道中的资产添加过渡组件 {#adding-transition}

请按照以下步骤将过渡组件添加到AEM Screens项目：

>[!NOTE]
>
>**前提条件**
> 使用渠道TestTransition创建AEM Screens **项**&#x200B;目TestProject ****。 此外，设置查看输出的位置和显示屏。

1. 导航到Channel **TestTransition** ，然 **后单击操作** 栏中的“编辑”。

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >TestTransition **渠道中的** TestTransition渠道已经很少包含资源（图像和视频）。 例如， **TestTransition** 通道包括三个图像和两个视频，如下所示：

   ![image2](assets/transitions2.png)


1. 将“过渡”组 **件拖放到** “编辑器”中。
   >[!CAUTION]
   >
   >在向渠道中的资产添加过渡之前，请确保不要在顺序渠道中的第一个资产之前添加过渡。 渠道中的第一个项目必须是资产，而不是过渡。

   ![image3](assets/transitions3.png)

   > [!NOTE]
   >
   >默认情况下，过渡组件的属性(如 **Type** )设置为 **Fade** , **Duration** （持续时间） **&#x200B;设置为1600 msFade。  此外，不建议设置比其所应用的资产长的过渡持续时间。

1. 此外，如果向此渠道编辑器添加了嵌入式序列组件(包括序列渠道 **** )，则可以在结尾处添加过渡组件，以便按顺序播放内容，如下图所示：

   ![image3](assets/transitions5.png)

