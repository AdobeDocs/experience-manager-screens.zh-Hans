---
title: 创建和管理显示区
description: 了解如何在AEM Screens中创建显示和设备配置。 另外，了解显示仪表板。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 1%

---

# 创建和管理显示区 {#creating-and-managing-displays}

显示器是彼此相邻放置的屏幕的虚拟分组。 该显示相对于安装是永久性的。 它是内容作者所使用并始终引用的对象作为逻辑显示，而不是其物理计数器部分。

在创建位置时，必须创建位置的显示。

本页显示了如何创建和管理Screens的显示内容。

**先决条件**：

* [配置和部署Screens](configuring-screens-introduction.md)
* [创建和管理Screens项目](creating-a-screens-project.md)
* [创建和管理渠道](managing-channels.md)
* [创建和管理位置](managing-locations.md)

## 创建新显示 {#creating-a-new-display}

>[!NOTE]
>
>在创建显示之前创建位置。 有关详细信息，请参阅[创建和管理位置](managing-locations.md)。

1. 导航到相应的位置，例如`http://localhost:4502/screens.html/content/screens/TestProject`。
1. 单击您的位置文件夹，然后单击操作栏中加号图标旁边的&#x200B;**创建**。
1. 从&#x200B;**创建**&#x200B;向导中单击&#x200B;**显示**，然后单击&#x200B;**下一步**。
1. 为您的显示位置输入您的&#x200B;**名称**&#x200B;和&#x200B;**标题**。
1. 在&#x200B;**显示**&#x200B;选项卡下，选择布局的详细信息。 选择所需的&#x200B;**分辨率**，如&#x200B;**全高清**。 选择水平和垂直设备数量。
1. 单击&#x200B;**创建**。

已创建显示区(*StoreDisplay*)并将其添加到位置(*SanJose*)。

![显示区](assets/display.gif)

当显示处于适当位置时，下一步是为该特定显示创建设备配置。

>[!NOTE]
>
>**下一步**：
>
>在为您的位置创建显示区时，请为显示区分配一个渠道以使用内容。
>
>请参阅[分配渠道](channel-assignment.md)部分，了解如何为显示分配渠道。

## 创建新设备配置 {#creating-a-new-device-config}

设备配置充当尚未安装的实际数字标牌设备的占位符。

1. 导航到相应的显示区，例如`http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`。
1. 单击您的显示文件夹，然后单击操作栏中的&#x200B;**查看仪表板**。
1. 单击&#x200B;**设备**&#x200B;面板右上角的&#x200B;**+添加设备配置**。

1. 单击&#x200B;**设备配置**&#x200B;作为所需的模板，然后单击&#x200B;**下一步**。

1. 根据需要输入属性，然后单击&#x200B;**创建**。

设备配置已创建并添加到当前显示（在以下演示中，新设备配置为&#x200B;*DeviceConfig*）。

![deviceconfig](assets/deviceconfig.gif)

>[!NOTE]
>
>当设备配置设置为您在该位置的显示时，下一步是为您的显示分配一个渠道。
>
>如下图所示，如果设备配置在&#x200B;**设备**&#x200B;面板中显示为“未分配”，且没有为该特定设备配置分配渠道。
>
>您应该事先了解如何创建和管理渠道。 有关详细信息，请参阅[创建和管理渠道](managing-channels.md)。

![chlimage_1-9](assets/chlimage_1-9.png)

## 显示功能板 {#display-dashboard}

显示仪表板为您提供了用于管理显示设备的不同面板。 它还允许您配置设备。

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>您可以单击功能板列表并触发对项目的批量操作，而不是单独查看每个项目。
>
>例如，下图显示了如何从显示功能板中单击多个渠道。

![cqdoc9456](assets/cqdoc9456.gif)

### 显示信息面板 {#display-information-panel}

**显示信息**&#x200B;面板提供显示属性。

单击&#x200B;**显示信息**&#x200B;面板右上角的(**...**)，以便查看属性并预览显示。


#### 查看属性 {#viewing-properties}

单击&#x200B;**属性**，以便查看或更改显示的属性。

此外，您还可以在&#x200B;**显示**&#x200B;选项卡下调整交互式渠道的事件计时器值。 默认值设置为&#x200B;*300秒*。

使用&#x200B;**CRXDE Lite**&#x200B;访问&#x200B;**idleTimeout**&#x200B;属性，即`http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels`。


### 已分配渠道面板 {#assigned-channels-panel}

**分配的渠道**&#x200B;面板显示分配给此设备的渠道。


### “设备”面板 {#devices-panel}

**DEVICES**&#x200B;面板提供了有关设备配置的信息。

单击“**设备**”面板右上角的(**...**)，以便添加设备配置和更新设备。

另外，单击设备配置可查看属性、指定设备或将其完全删除。

![chlimage_1-13](assets/chlimage_1-13.png)

#### 后续步骤 {#the-next-steps}

在为您的位置创建显示区后，请为您的显示区分配一个渠道。

有关更多详细信息，请参阅[分配渠道](channel-assignment.md)。
