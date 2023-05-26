---
title: 管理设备
seo-title: Managing Devices
description: 本页介绍了设备分配。
seo-description: Follow this page to learn about device assignment. The Devices console allows you to access the device manager to assign your device to a display.
uuid: 889cc11c-60f7-4966-82b5-9ebdd082a3c5
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8dc08e29-a377-4e84-84ee-442470c19019
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# 管理设备 {#managing-devices}

本页介绍了设备分配。

“设备”控制台允许您访问设备管理器，以将设备分配给显示器。

>[!CAUTION]
>
>在分配设备之前，您需要注册该设备。 有关更多信息，请参阅 [设备注册](device-registration.md).

## 设备分配 {#device-assignment}

按照以下步骤为显示设备指定设备：

1. 导航到项目的Devices文件夹，例如

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. 选择您的 **设备** 文件夹，然后点按/单击 **设备管理器** 操作栏中的。 此时会显示已分配和未分配的设备。

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. 从列表中选择未分配的设备，然后点按/单击 **指定设备** 操作栏中的。

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. 从列表中选择要将设备分配给的显示，然后点按/单击 **分配**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. 点按/单击 **完成** 以完成分配流程。


   显示功能板会在以下位置显示分配的设备： **设备** 面板。

   ![chlimage_1-37](assets/chlimage_1-37.png)

   单击(**...**)的右上角 **设备** 面板以添加设备配置或更新设备。

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>每次将第一个设备添加到新的Screens项目时，都会创建一个用户组。
>例如，如果项目节点名称为 *we-retail*，则用户组名称为 *screens-we-retail-devices*.
>此组将添加为 **参与者** 组，如下图所示：

![chlimage_1-39](assets/chlimage_1-39.png)

### 后续步骤 {#the-next-steps}

熟悉了为显示分配渠道后，请参阅以下资源：

* [监视和故障排除](monitoring-screens.md)
