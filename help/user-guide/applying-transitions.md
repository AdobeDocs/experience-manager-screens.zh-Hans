---
title: 应用过渡
seo-title: 应用过渡
description: 可查看本页以了解如何将过渡应用于Screens项目。
seo-description: 可查看本页以了解如何将过渡应用于Screens项目。
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 9b54b153676852742859b704ac9aedf908fceecf
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---


# 应用过渡{#applying-transitions}

本节介绍如何在不同资产（图像和视频）和过渡中应用&#x200B;**渠道**&#x200B;组件。


>[!CAUTION]
>
>要详细了解&#x200B;**过渡**&#x200B;组件的属性，请参阅[过渡](adding-components-to-a-channel.md#transition)。

## 将过渡组件添加到渠道{#adding-transition}中的资产

请按照以下步骤将过渡组件添加到您的AEM Screens项目：

>[!NOTE]
>
>**前提条件**
>
>创建具有渠道&#x200B;**TestTransition**&#x200B;的AEM Screens项目&#x200B;**TestProject**。 此外，还可设置一个位置和一个显示器以视图输出。

1. 导航到渠道&#x200B;**TestTransition**，然后单击操作栏中的&#x200B;**编辑**。

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >**TestTransition**&#x200B;渠道中的资源（图像和视频）已经很少。 例如，**TestTransition**&#x200B;渠道包含三个图像和两个视频，如下所示：

   ![image2](assets/transitions2.png)


1. 将&#x200B;**过渡**&#x200B;组件拖放到编辑器中。
   >[!CAUTION]
   >
   >在将过渡添加到渠道中的资产之前，请确保不要在顺序渠道中第一个资产之前添加过渡。 您渠道中的第一个项目必须是资产，而不是过渡。

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >默认情况下，过渡组件（如&#x200B;**Type**）的属性设置为&#x200B;**淡入淡出**，而&#x200B;**持续时间**&#x200B;设置为&#x200B;*1600 ms*。  此外，不建议设置比资产所应用的过渡持续时间长的持续时间。

1. 此外，如果向此渠道编辑器添加&#x200B;**嵌入式序列**&#x200B;组件(包括序列渠道)，则可以在结尾添加过渡组件，以便按顺序播放内容，如下图所示：

   ![image3](assets/transitions5.png)

