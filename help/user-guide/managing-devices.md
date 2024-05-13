---
title: 管理设备
description: 了解AEM Screens中的设备分配和管理。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 1%

---

# 管理设备 {#managing-devices}

本页介绍设备分配。

通过“设备”控制台，您可以访问设备管理器，将设备分配给显示器。

>[!CAUTION]
>
>在分配设备之前，请先注册该设备。 请参阅 [设备注册](device-registration.md).

## 设备分配 {#device-assignment}

按照以下步骤将设备分配给显示器：

1. 例如，导航到项目的Devices文件夹

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. 单击您的 **设备** 文件夹并单击 **设备管理器** 在操作栏中。 此时会显示已分配和未分配的设备。

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. 在列表中单击未分配的设备，然后单击 **指定设备** 在操作栏中。

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. 在列表中单击要为其分配设备的显示，然后单击 **分配**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. 单击 **完成** 以完成分配流程。


   显示功能板显示分配到的设备 **设备** 面板。

   ![chlimage_1-37](assets/chlimage_1-37.png)

   单击(**...**)的右上角 **设备** 面板以添加设备配置或更新设备。

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>每次将第一个设备添加到新的Screens项目时，都会创建一个用户组。
>例如，如果项目节点名称为 *we-retail*，则用户组名称为 *screens-we-retail-devices*.
>此组已添加为 **参与者** 组，如下图所示：

![chlimage_1-39](assets/chlimage_1-39.png)

### 后续步骤 {#the-next-steps}

熟悉将渠道分配给显示后，请参阅[监控和故障排除](monitoring-screens.md).
