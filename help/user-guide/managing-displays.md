---
title: 创建和管理显示区
seo-title: Managing Displays
description: 按照本页了解如何创建新的显示和设备配置。 此外，了解显示功能板。
seo-description: Follow this page to learn about creating a new display and device config. Additionally, learn about the display dashboard.
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 1%

---

# 创建和管理显示区 {#creating-and-managing-displays}

显示屏是屏幕的虚拟分组，通常位于彼此旁边。 对于安装而言，显示通常是永久性的。 这是内容作者将使用的对象，并且始终引用为逻辑显示，而不是其物理计数器部分。

创建位置后，必须为位置创建新显示。

此页显示如何创建和管理Screens显示器。

**先决条件**：

* [配置和部署Screens](configuring-screens-introduction.md)
* [创建和管理屏幕项目](creating-a-screens-project.md)
* [创建和管理渠道](managing-channels.md)
* [创建和管理位置](managing-locations.md)

## 创建新显示 {#creating-a-new-display}

>[!NOTE]
>
>在创建显示之前，需要先创建位置。 要了解如何创建位置，请参阅 [创建和管理位置](managing-locations.md) 了解更多信息。

要在您的位置创建新显示区，请执行以下步骤：

1. 导航到相应的位置，例如 `http://localhost:4502/screens.html/content/screens/TestProject`.
1. 选择您的位置文件夹，然后点按/单击 **创建** 操作栏中加号图标旁边。 此时将打开向导。
1. 选择 **显示** 从 **创建** 向导并单击 **下一个**.

1. 输入 **名称** 和 **标题** 显示位置的信息。

1. 在 **显示** 选项卡，选择布局的详细信息。 选择所需的 **分辨率** (例如， as， as **全高清**)。 此外，您还可以水平和垂直选择设备数量。

1. 单击&#x200B;**创建**。

显示区(*StoreDisplay*)创建并添加到位置(*圣何塞*)。

![显示](assets/display.gif)

一旦显示就位，下一步就是为该特定显示创建设备配置。 按照以下部分创建新设备配置。

>[!NOTE]
>
>**下一步**：
>
>为位置创建显示区后，您需要为显示区分配一个渠道以利用内容。
>
>参见 [分配渠道](channel-assignment.md) 部分，以了解如何为显示分配渠道。

## 创建新设备配置 {#creating-a-new-device-config}

设备配置充当尚未安装的实际数字标牌设备的占位符。

按照以下步骤创建新设备配置：

1. 导航到相应的显示区，例如， `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. 选择您的显示文件夹并点按/单击 **查看功能板** 操作栏中的。
1. 点按/单击 **+添加设备配置** 右上角的 **设备** 面板。

1. 选择 **设备配置** 作为所需的模板，然后点按/单击 **下一个**.

1. 根据需要输入属性，然后点按/单击 **创建**.

设备配置已创建并添加到当前显示中(在以下演示中，新的设备配置为 *DeviceConfig*)。

![设备配置](assets/deviceconfig.gif)

一旦将设备配置设置为您在该位置的显示器，下一步就是为显示器分配一个频道。

>[!NOTE]
>
>一旦将设备配置设置为您在该位置的显示器，下一步就是为显示器分配一个频道。
>
>如下图所示，如果设备配置在 **设备** 面板（如果没有为该特定设备配置分配频道）。
>
>您应事先了解如何创建和管理渠道。 参见 [创建和管理渠道](managing-channels.md) 了解更多详细信息。

![chlimage_1-9](assets/chlimage_1-9.png)

## 显示功能板 {#display-dashboard}

显示仪表板为您提供不同的面板，用于管理显示设备和设备的设备配置。

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>您可以选择功能板列表并触发对项目的批量操作，而不是分别浏览每个项目。
>
>例如，下图显示了如何从显示功能板中选择多个渠道。

![cqdoc9456](assets/cqdoc9456.gif)

### “显示信息”面板 {#display-information-panel}

此 **显示信息** 面板提供显示属性。

单击(**...**)的右上角 **显示信息** 面板以查看属性并预览显示。


#### 查看属性 {#viewing-properties}

单击 **属性** 查看或更改显示的属性。

此外，您还可以在以下位置调整交互式渠道的事件计时器值 **空闲超时** 下的属性 **显示** 选项卡。 默认值设置为 *300秒*.

使用 **CRXDE Lite**，以访问 **idleTimeout** 属性，也就是说， `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .


### “分配的渠道”面板 {#assigned-channels-panel}

此 **已分配渠道** 面板显示分配给此设备的渠道。


### “设备”面板 {#devices-panel}

此 **设备** 面板提供有关设备配置的信息。

单击(**...**)的右上角 **设备** 用于添加设备配置和更新设备的面板。

此外，单击设备配置可查看属性、指定设备或将其完全删除。

![chlimage_1-13](assets/chlimage_1-13.png)

#### 后续步骤 {#the-next-steps}

完成为位置创建显示后，需要为显示分配渠道。

参见 [分配渠道](channel-assignment.md) 了解更多详细信息。
