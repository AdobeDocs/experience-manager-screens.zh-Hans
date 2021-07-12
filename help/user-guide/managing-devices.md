---
title: 管理设备
seo-title: 管理设备
description: 本页介绍了设备分配。
seo-description: 可查看本页以了解设备分配。通过设备控制台，您可以访问设备管理器，以将设备分配到显示屏。
uuid: 889cc11c-60f7-4966-82b5-9ebdd082a3c5
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8dc08e29-a377-4e84-84ee-442470c19019
feature: 创作屏幕
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 70%

---

# 管理设备 {#managing-devices}

本页介绍了设备分配。

通过设备控制台，您可以访问设备管理器，以将设备分配到显示屏。

>[!CAUTION]
>
>在分配设备之前，您需要先注册该设备。有关更多信息，请参阅[设备注册](device-registration.md)。

## 设备分配 {#device-assignment}

请按照以下步骤将设备分配到显示屏：

1. 导航到项目的设备文件夹，例如

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. 选择您的&#x200B;**设备**&#x200B;文件夹，然后点按/单击操作栏中的&#x200B;**设备管理器**。 此时将显示已分配和未分配的设备。

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. 从列表中选择未分配的设备，然后点按/单击操作栏中的&#x200B;**分配设备**。

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. 从列表中选择要将设备分配到的显示屏，然后点按/单击&#x200B;**Assign**。

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. 点按/单击&#x200B;**完成**&#x200B;以完成分配过程。


   显示功能板会在&#x200B;**设备**&#x200B;面板中显示已分配的设备。

   ![chlimage_1-37](assets/chlimage_1-37.png)

   单击&#x200B;**设备**&#x200B;面板右上角的 (**...**) 以添加设备配置或更新设备。

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>每次将第一台设备添加到新的 Screens 项目时，都会创建一个用户组。
>例如，如果项目节点名称为&#x200B;*we-retail*，则用户组名称为&#x200B;*screens-we-retail-devices*。
>此组将添加为&#x200B;**参与者**&#x200B;组的成员，如下图所示：

![chlimage_1-39](assets/chlimage_1-39.png)

### 后续步骤 {#the-next-steps}

在您熟悉如何将渠道分配到显示屏后，请参阅以下资源：

* [监测和故障诊断](monitoring-screens.md)
