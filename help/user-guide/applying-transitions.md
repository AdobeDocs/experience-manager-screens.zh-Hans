---
title: 应用过渡
seo-title: 应用过渡
description: 请阅读本页内容，了解如何将过渡应用到Screens项目。
seo-description: 请阅读本页内容，了解如何将过渡应用到Screens项目。
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
feature: 创作屏幕
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 2%

---


# 应用过渡{#applying-transitions}

本节介绍如何在不同资产（图像和视频）和渠道中的嵌入式序列之间应用&#x200B;**过渡**&#x200B;组件。


>[!CAUTION]
>
>要详细了解&#x200B;**Transition**&#x200B;组件的属性，请参阅[Transitions](adding-components-to-a-channel.md#transition)。

## 将过渡组件添加到渠道{#adding-transition}中的资产

请按照以下步骤将过渡组件添加到您的AEM Screens项目：

>[!NOTE]
>
>**前提条件**
>
>创建具有渠道&#x200B;**TestTransition**&#x200B;的AEM Screens项目&#x200B;**TestProject**。 此外，还应设置一个位置和一个显示器，以查看输出。

1. 导航到渠道&#x200B;**TestTransition**，然后单击操作栏中的&#x200B;**编辑**。

   ![图像1](assets/transitions1.png)

   >[!NOTE]
   >
   >**TestTransition**&#x200B;渠道中已有很少的资产（图像和视频）。 例如，**TestTransition**&#x200B;渠道包含三个图像和两个视频，如下所示：

   ![图像2](assets/transitions2.png)


1. 将&#x200B;**Transition**&#x200B;组件拖放到编辑器中。
   >[!CAUTION]
   >
   >在渠道中将过渡添加到资产之前，请确保不要在顺序渠道中的第一个资产之前添加过渡。 渠道中的第一个项目必须是资产，而不是过渡。

   ![图像3](assets/transitions3.png)

   >[!NOTE]
   >
   >默认情况下，过渡组件的属性（如&#x200B;**Type**）设置为&#x200B;**Fade**，而&#x200B;**Duration**)设置为&#x200B;*1600毫秒*。  此外，不建议设置的过渡持续时间长于应用到的资产。

1. 此外，如果向此渠道编辑器添加&#x200B;**嵌入式序列**&#x200B;组件（包括序列渠道），则可以在末尾添加过渡组件，以便内容按顺序播放，如下图所示：

   ![图像3](assets/transitions5.png)

