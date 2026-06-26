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
TQID: https://experienceleague.adobe.com/BtVUYTZ9GisSxK6-M-QsYRGdykFB51IchqI7CX-vsa8
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 288
ht-degree: 5%

---

# 管理设备 {#managing-devices}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

本页介绍设备分配。

通过“设备”控制台，您可以访问设备管理器，将设备分配给显示器。

>[!CAUTION]
>
>在分配设备之前，请先注册该设备。 请参阅[设备注册](device-registration.md)。

## 设备分配 {#device-assignment}

按照以下步骤将设备分配给显示器：

1. 例如，导航到项目的Devices文件夹

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. 单击您的&#x200B;**设备**&#x200B;文件夹，然后单击操作栏中的&#x200B;**设备管理器**。 此时会显示已分配和未分配的设备。

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. 从列表中单击未分配的设备，然后在操作栏中单击&#x200B;**分配设备**。

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. 从列表中单击要为其分配设备的显示，然后单击&#x200B;**分配**。

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. 单击&#x200B;**完成**&#x200B;以完成分配流程。


   显示功能板在&#x200B;**设备**&#x200B;面板中显示分配的设备。

   ![chlimage_1-37](assets/chlimage_1-37.png)

   单击(**...**) 在&#x200B;**设备**&#x200B;面板的右上角添加设备配置或更新设备。

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>每次将第一台设备添加到新的Screens项目时，都会创建一个用户组。例如，如果项目节点名称为&#x200B;*we-retail*，则用户组名称为&#x200B;*screens-we-retail-devices*。该组已添加为&#x200B;**参与者**&#x200B;组的成员，如下图所示：

![chlimage_1-39](assets/chlimage_1-39.png)

### 后续步骤 {#the-next-steps}

熟悉如何为显示分配渠道后，请参阅t[监视和疑难解答](monitoring-screens.md)。

