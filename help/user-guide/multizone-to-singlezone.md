---
title: MultiZone到SingleZone过渡用例
description: 可查看本页以了解MultiZone到SingleZone过渡的用例。
seo-description: MultiZone到SingleZone过渡的用例。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6f770734941635a0cd404986c259022137355af3

---


# 多区到单区过渡 {#multizone-to-singlezone-use-case}


## 用例描述 {#use-case-description}

本节介绍一个用例示例，其中着重介绍如何设置与单区布局渠道替代的多区布局渠道。 多区域渠道具有图像／视频资产的排序，它显示了如何设置从多区域到单区域交替的项目，反之亦然。

### 先决条件 {#preconditions}

在开始此使用案例之前，请确保您了解如何：

* **[创建和管理渠道](managing-channels.md)**
* **[创建和管理位置](managing-locations.md)**
* **[创建和管理计划](managing-schedules.md)**
* **[设备注册](device-registration.md)**

### 主要演员 {#primary-actors}

内容作者

## 设置项目 {#setting-up-the-project}

请按照以下步骤设置项目：

1. 创建一个名为 **TakeoverLoop的AEM Screens项目**，如下所示。

   ![资产](assets/mz-to-sz1.png)


1. **创建多区域屏幕渠道**

   1. 选择渠 **道文件夹** ，然后单击操 **作栏中的创建** ，以打开向导以创建渠道。
   1. 从向 **导中选择Left-L Bar Split Screen Channel** ，然后创建标题为MultiZoneLayout的 **渠道**。
   1. 向渠道添加内容。 将资产拖放到每个区域。 以下示例显示 **MultiZoneLayout** channel，该频道由视频、图像和文本横幅（在嵌入式序列中）组成，如下所示。
   ![资产](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >要了解有关在渠道中创建多区域布局的更多信息，请参 [阅多区域布局](multi-zone-layout-aem-screens.md)。


1. 创建标题为TakeoverChannel的另 **一个渠道** ，指 **向Channels文** 件夹。

   ![资产](assets/mz-to-sz3.png)

1. 单击 **操作栏中的** “编辑”，将内容添加到此渠道。 向此渠 **道添加Channel** 组件和要切换到的图像资产，如下图所示：

   ![资产](assets/mz-to-sz4.png)

1. 打开渠道组件的设置，并将其指向您在步骤2中 **创建的MultiZoneLayout***渠道*。

   ![资产](assets/mz-to-sz5.png)

1. 将“序列”字段的持 **续时间** 设置为 **10000毫秒**。

   ![资产](assets/mz-to-sz6.png)

1. 同样，打开图像（您添加的资产）的设置，并将其持续时间从“序列”字 **段设置** 为 **3000毫秒**。

   ![资产](assets/mz-to-sz7.png)

## 检查预览 {#checking-the-preview}

您可以从播放器中查看所需的输出，也可以只通过单击编辑器中的“ **预览** ”来查看。

输出将演示多区域布局在 *10000毫秒内的播放方式* ，然后切换到播放持续时间为 ** 3000毫秒的单个区域布局，然后切换回多区域布局。

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>您可以根据需要自定义渠道过渡（从多区域到单区域布局，反之亦然）。