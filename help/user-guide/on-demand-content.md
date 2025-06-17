---
title: 按需内容更新
description: 了解用于管理出版物的按需内容更新。
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 9ffdb1eb-a1ba-42ac-a30f-260004e5b165
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# 按需内容更新 {#on-demand}

本节介绍用于管理出版物的按需内容。

## 管理发布：将内容更新从作者发布到设备 {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

您可以从AEM Screens发布和取消发布内容。 **管理发布**&#x200B;允许您从作者到发布设备交付内容更新。 您可以为整个AEM Screens项目或仅为某个渠道、位置、设备、应用程序或计划发布/取消发布内容。

### 管理AEM Screens项目的发布 {#managing-publication-for-an-aem-screens-project}

请按照以下步骤为AEM Screens项目从创作到发布到设备交付内容更新：

1. 导航到您的AEM Screens项目。
1. 单击操作栏中的&#x200B;**管理发布**，以便您可以将项目发布到发布实例。

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. 将打开&#x200B;**管理发布**&#x200B;向导。 您可以单击&#x200B;**操作**，还可以安排现在或之后的发布时间。 单击&#x200B;**下一步**。

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 选中该框，以便您可以从&#x200B;**`Manage Publication`**&#x200B;向导中单击整个项目。

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. 单击操作栏中的&#x200B;**+包括子项**&#x200B;并取消选中所有选项，以便发布项目中的所有模块，然后单击&#x200B;**添加**&#x200B;以进行发布。

   >[!NOTE]
   >
   >默认情况下，所有复选框都处于选中状态，您必须手动取消选中这些复选框以发布项目中的所有模块。

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **了解包括子项对话框**

   上述步骤显示了如何发布整个内容。 如果要使用其他三个可用的替代项，则必须选中该特定选项。
例如，下图显示了如何仅管理和更新项目中已修改的页面：
   ![图像](assets/author-publish-manage.png)

   请按照下面的解释进行操作，以便您了解可用的选项：

   1. **仅包括下级子项**：
利用此选项，您可以仅管理对项目结构中子节点的更新。
   1. **仅包括已修改的页面**：
利用此选项，您可以仅管理对项目结构中找到的更改的已修改页面的更新。
   1. **仅包括已发布的页面**：
通过此选项，您可以仅管理对之前发布的页面的更新。


1. 在&#x200B;**`Manage Publication wizard`**&#x200B;中，单击&#x200B;**发布**。

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >请等待几秒/分钟，以便内容可到达发布实例。
   >
   >
   >    1. 如果项目中没有更改，并且&#x200B;**更新离线内容**&#x200B;没有任何内容，则工作流无法运行。
   >    1. 在管理发布工作流中选择&#x200B;**发布**&#x200B;按钮后，如果作者未完成复制过程（内容正在上载到发布实例），则工作流无法运行。

   >[!CAUTION]
   >作为内容创建者，如果要查看附加到创作实例的设备中的更改，请在渠道仪表板中单击&#x200B;**更新离线内容**，或者通过选择项目来进行更新。 在这种情况下，仅在Author实例中更新离线内容。

1. 导航到项目，然后单击操作栏中的&#x200B;**更新离线内容**。 此操作会将相同的命令转发到发布实例，以便在发布实例上也创建离线ZIP。

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >完成管理发布工作流后，如果存在指向创作实例的播放器，则在创作中触发更新离线内容。 这样做会在创作实例上脱机创建更新。

   >[!CAUTION]
   >
   >如果您有向创作服务器注册的播放器，则在创作实例中触发更新离线内容。 对于在发布实例中注册的播放器，不需要更新离线内容。

### 管理渠道发布 {#managing-publication-for-a-channel}

请按照以下步骤在AEM Screens项目中通过“创作”>“发布”>“设备”为渠道交付内容更新：

>[!NOTE]
>
>仅当渠道中有更改时，才遵循此部分。 如果在上次更新离线内容后，渠道没有任何更改，则单个渠道的管理发布工作流将无法工作。

1. 导航到您的AEM Screens项目，然后单击渠道。
1. 单击操作栏中的&#x200B;**管理发布**，以便将该渠道发布到发布实例。

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. 将打开&#x200B;**管理发布**&#x200B;向导。 您可以单击&#x200B;**操作**，还可以安排现在或之后的发布时间。 单击&#x200B;**下一步**。

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 从&#x200B;**`Manage Publication`**&#x200B;向导中单击&#x200B;**发布**。

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >请等待几秒/分钟，以便内容可到达发布实例。

1. 在渠道仪表板中触发&#x200B;**更新离线内容**&#x200B;仅将离线内容推送到作者实例，而不会推送到发布实例。 步骤1-4是将离线内容推送到发布实例。

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >首先发布，然后触发更新离线内容，如前面的步骤中所述。

### 渠道和设备重新分配： {#channel-and-device-re-assignment}

如果重新分配了设备，则在将该设备重新分配给新显示时，发布初始显示和新显示。

同样，如果重新分配了渠道，在将渠道重新分配给新显示后，发布初始显示和新显示。
