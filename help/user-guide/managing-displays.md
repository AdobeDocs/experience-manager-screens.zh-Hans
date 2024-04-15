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
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# 创建和管理显示区 {#creating-and-managing-displays}

显示器是彼此相邻放置的屏幕的虚拟分组。 该显示相对于安装是永久性的。 这是内容作者使用的对象，并始终引用为逻辑显示，而不是其物理计数器部分。

在创建位置时，必须创建位置的显示。

此页显示如何创建和管理屏幕显示。

**先决条件**：

* [配置和部署Screens](configuring-screens-introduction.md)
* [创建和管理Screens项目](creating-a-screens-project.md)
* [创建和管理渠道](managing-channels.md)
* [创建和管理位置](managing-locations.md)

## 创建新显示 {#creating-a-new-display}

>[!NOTE]
>
>在创建显示之前创建位置。 请参阅 [创建和管理位置](managing-locations.md) 以了解更多信息。

1. 导航到相应的位置，例如 `http://localhost:4502/screens.html/content/screens/TestProject`.
1. 选择您的位置文件夹，然后选择 **创建** 位于操作栏中的加号图标旁边。
1. 选择 **显示** 从 **创建** 向导，然后选择 **下一个**.
1. 输入 **名称** 和 **标题** 显示位置的信息。
1. 在 **显示** 选项卡，选择布局的详细信息。 选择所需的 **分辨率**，例如 **全高清**. 选择水平和垂直设备数量。
1. 选择&#x200B;**创建**。

显示区(*StoreDisplay*)创建并添加到位置(*圣何塞*)。

![显示](assets/display.gif)

当显示处于适当位置时，下一步是为该特定显示创建设备配置。

>[!NOTE]
>
>**下一步**：
>
>在为您的位置创建显示区时，请为显示区分配一个渠道以使用内容。
>
>请参阅 [分配渠道](channel-assignment.md) 部分，以了解如何将渠道分配给显示。

## 创建新设备配置 {#creating-a-new-device-config}

设备配置充当尚未安装的实际数字标牌设备的占位符。

1. 导航到相应的显示区，例如， `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. 选择您的显示文件夹，然后选择 **查看功能板** 在操作栏中。
1. 选择 **+添加设备配置** 右上角的 **设备** 面板。

1. 选择 **设备配置** 作为所需的模板，然后点按/单击 **下一个**.

1. 根据需要输入属性，然后点按/单击 **创建**.

设备配置已创建并添加到当前显示中(在以下演示中，新的设备配置为 *设备配置*)。

![设备配置](assets/deviceconfig.gif)

>[!NOTE]
>
>当设备配置设置为您在该位置的显示时，下一步是为您的显示分配一个渠道。
>
>如下图所示，如果设备配置在 **设备** 面板（如果未将渠道分配给该特定设备配置）。
>
>您应该事先了解如何创建和管理渠道。 请参阅 [创建和管理渠道](managing-channels.md) 以了解更多详细信息。

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

### 显示信息面板 {#display-information-panel}

此 **显示区信息** 面板提供显示属性。

单击(**...**)的右上角 **显示区信息** 面板，以便查看属性并预览显示。


#### 查看属性 {#viewing-properties}

单击 **属性** 以便查看或更改显示的属性。

此外，您还可以在中调整交互式渠道的事件计时器值 **空闲超时** 下的属性 **显示** 选项卡。 默认值设置为 *300秒*.

使用 **CRXDE Lite**，以访问 **idleTimeout** 属性，也就是说， `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .


### 已分配渠道面板 {#assigned-channels-panel}

此 **已分配渠道** 面板会显示分配给此设备的渠道。


### “设备”面板 {#devices-panel}

此 **设备** 面板提供有关设备配置的信息。

选择(**...**)的右上角 **设备** 面板，以便添加设备配置和更新设备。

另外，单击设备配置可查看属性、指定设备或将其完全删除。

![chlimage_1-13](assets/chlimage_1-13.png)

#### 后续步骤 {#the-next-steps}

在为您的位置创建显示区后，请为您的显示区分配一个渠道。

请参阅 [分配渠道](channel-assignment.md) 以了解更多详细信息。
