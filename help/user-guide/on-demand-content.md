---
title: 按需内容更新
seo-title: On-Demand Content Update
description: 按照此页面了解On-Demand内容更新。
seo-description: Follow this page to learn about On-Demand Content Update.
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 9ffdb1eb-a1ba-42ac-a30f-260004e5b165
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# 按需内容更新 {#on-demand}

本节介绍用于管理出版物的按需内容。

## 管理发布：将内容更新从作者发布到设备 {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

您可以从AEM Screens发布和取消发布内容。 通过“管理发布”功能，可将内容更新从作者发布到设备。 您可以为整个AEM Screens项目或仅为渠道、位置、设备、应用程序或计划之一发布/取消发布内容。

### 管理AEM Screens项目的发布 {#managing-publication-for-an-aem-screens-project}

请按照以下步骤为AEM Screens项目从创作到发布到设备交付内容更新：

1. 导航到您的AEM Screens项目。
1. 单击 **管理发布** 将项目发布到发布实例。

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. 此 **管理发布** 向导打开。 您可以选择 **操作** 还可以将发布时间安排为现在或以后。 单击&#x200B;**下一步**。

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 选中方框可从中选择整个项目 **管理发布** 向导。

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. 单击 **+包括子项** 从操作栏中，取消选中所有选项以发布项目中的所有模块，然后单击 **添加** 以发布。

   >[!NOTE]
   >
   >默认情况下，将选中所有框，您必须手动取消选中这些框以发布项目中的所有模块。

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **“了解包括子项”对话框**

   上述步骤显示了如何发布整个内容。 如果您要使用其他三个可用的替代项，则必须选中该特定选项。
例如，下图允许您仅管理和更新项目中已修改的页面：
   ![图像](assets/author-publish-manage.png)

   请按照下面的解释了解可用的选项：

   1. **仅包括下级子项**：利用此选项，可管理仅对项目结构中的子节点的更新。
   1. **仅包括已修改的页面**：利用此选项，您只能管理对项目结构中发现了更改的已修改页面的更新。
   1. **仅包括已发布的页面**：此选项允许仅管理对之前发布的页面的更新。


1. 单击 **Publish** 从 **管理发布向导。**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >请等待几秒钟/分钟，以便内容到达发布实例。
   >
   >
   >    1. 如果项目中没有变化，并且没有变化，则工作流将不起作用 **更新离线内容**.
   >    1. 如果作者在单击“ ”后未完成复制过程（内容仍在上载到发布实例），则工作流将不起作用 **Publish** 按钮。


   >[!CAUTION]
   >如果作为作者或内容创建者，您希望查看附加到作者实例的设备中的更改，请单击 **更新离线内容** 通过渠道仪表板或选择项目。 在这种情况下，仅在创作实例中执行更新离线内容。

1. 导航到项目并单击 **更新离线内容** 操作栏中的。 此操作将相同的命令转发到发布实例，以便也在发布实例上创建离线zip。

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >完成管理发布工作流后，如果存在指向创作实例的播放器，则必须在创作中触发更新离线内容，该操作将在创作实例上离线创建更新。

   >[!CAUTION]
   >
   >如果您有向创作服务器注册的播放器，则必须触发创作实例中的更新离线内容。 在发布实例中注册的播放器不需要更新离线内容。

### 管理渠道的发布 {#managing-publication-for-a-channel}

请按照以下步骤为AEM Screens项目中的渠道将内容更新从作者发布到设备：

>[!NOTE]
>
>仅当渠道中有更改时，才遵循此部分。 如果在上次更新离线内容后，渠道没有任何更改，则单个渠道的管理发布工作流将无法工作。

1. 导航到屏幕项目并选择渠道。
1. 单击 **管理发布** 将渠道发布到发布实例。

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. 此 **管理发布** 向导打开。 您可以选择 **操作** 还可以将发布时间安排为现在或以后。 单击&#x200B;**下一步**。

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 单击 **Publish** 从 **管理发布向导。**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >请等待几秒钟/分钟，以便内容到达发布实例。

1. 触发器 **更新离线内容** 中的渠道功能板将仅将离线内容推送到创作实例，而不会推送到发布实例。 步骤1-4是将离线内容推送到发布实例。

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >您必须首先发布，然后触发更新离线内容，如前面的步骤中所述。

### 渠道和设备重新分配： {#channel-and-device-re-assignment}

如果重新分配了设备，则一旦将设备重新分配给新显示，您必须发布初始显示和新显示。

同样，如果您已重新分配了渠道，则一旦渠道重新分配给新显示，您必须发布初始显示和新显示。
