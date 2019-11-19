---
title: 创建和管理显示屏
seo-title: 管理显示屏
description: 可查看本页以了解有关创建新显示屏和设备配置的信息。此外，还可了解显示功能板。
seo-description: 可查看本页以了解有关创建新显示屏和设备配置的信息。此外，还可了解显示功能板。
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 创建和管理显示屏 {#creating-and-managing-displays}

显示屏是通常彼此相邻放置的屏幕的虚拟分组。显示屏对于某个安装通常是永久性的。这将是作者要处理的对象内容，并且始终引用为逻辑显示而不是其实际计数部分。

创建位置后，您必须为该位置创建一个新显示屏。

本页显示了如何为 Screens 创建和管理显示屏。

**先决条件**：

* [配置和部署 Screens](configuring-screens-introduction.md)
* [创建和管理Screens项目](creating-a-screens-project.md)
* [创建和管理渠道](managing-channels.md)
* [创建和管理位置](managing-locations.md)

## 创建新显示屏 {#creating-a-new-display}

>[!NOTE]
>
>在创建显示屏之前，您需要先创建位置。To see how to create a location, see [Create and Manage Locations](managing-locations.md) for more information.

要在您的位置中创建新显示屏，请按照以下步骤操作：

1. Navigate to the appropriate location, for example `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Select your location folder and tap/click **Create** next to the plus icon in the action bar. 此时将打开一个向导。
1. Select **Display** from the **Create** wizard and click **Next**.

1. Enter **Name** and **Title** for your display location.

1. Under the **Display** tab, choose the details of the Layout. Choose the desired **Resolution** (example as, as **Full HD**). 此外，您还可以选择水平和垂直设备的数量。

1. 单击&#x200B;**创建**。

The display (*StoreDisplay*) is created and added to the location (*SanJose*).

![显示](assets/display.gif)

创建显示屏后，下一步是为该特定显示屏创建设备配置。请按照以下部分创建新设备配置。

>[!NOTE]
>
>**下一步**：
>
>为您的位置创建显示屏后，您需要为显示屏分配渠道以利用内容。
>
>See [Assign Channels](channel-assignment.md) section to learn how to assign a channel to the display.

## 创建新设备配置 {#creating-a-new-device-config}

设备配置充当尚未安装的实际数字标牌设备的占位符。

请按照以下步骤创建新设备配置：

1. 导航到相应的显示屏，例如 `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`。
1. Select your display folder and tap/click **View Dashboard** in the action bar.
1. Tap/click the **+ Add Device Config** on the top right of the **Devices** panel.

1. Select the **Device Config** as the required template as and tap/click **Next**.

1. Enter the properties as required and tap/click **Create**.

The device config is created and added to the current display (in the following demonstration, the new device config is *DeviceConfig*).

![设备配置](assets/deviceconfig.gif)

为位置中的显示屏设置设备配置后，下一步是将渠道分配到显示屏。

>[!NOTE]
>
>为位置中的显示屏设置设备配置后，下一步是将渠道分配到显示屏。
>
>As shown in the figure below, if the device config is displayed as unassigned in the **DEVICES** pannel, if no channel is assigned to that particular device config.
>
>您应当已事先了解如何创建和管理渠道。有关更 [多详细信息，请参阅创建](managing-channels.md) 和管理渠道。

![chlimage_1-9](assets/chlimage_1-9.png)

## 显示功能板 {#display-dashboard}

显示功能板为您提供了不同的面板，用于为您的设备管理显示设备和设备配置。

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>您可以选择功能板列表并对多个项目触发批量操作，而不是对每个项目单独执行操作。
>
>例如，下图显示了如何从显示功能板中选择多个渠道。

![cqdoc9456](assets/cqdoc9456.gif)

### “显示信息”面板{#display-information-panel}

**显示信息**&#x200B;面板提供了显示属性。

Click on the (**...**) in the top right corner in the **DISPLAY INFORMATION **panel to view the properties and preview the display.

![chlimage_1-10](assets/chlimage_1-10.png)

#### 查看属性 {#viewing-properties}

单击&#x200B;**属性**&#x200B;可查看或更改显示屏的属性。

Additionally, you can adjust the event timer value for your interactive channel in **Idle timeout **property under **Display** tab. 默认值设为 *300 秒*。

Use **CRXDE Lite**, to access the **idleTimeout** property, that is, `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .

![chlimage_1-1](assets/chlimage_1-1.gif)

### “已指定渠道”面板{#assigned-channels-panel}

**已指定渠道**&#x200B;面板显示了已分配到此设备的渠道。

![chlimage_1-11](assets/chlimage_1-11.png)

### “设备”面板{#devices-panel}

**设备**&#x200B;面板提供了有关设备配置的信息。

Click on the (**...**) in the top right corner in the **DEVICES **panel to add device configs and update devices.

![chlimage_1-12](assets/chlimage_1-12.png)

此外，单击设备配置可查看属性、分配设备或完全删除设备。

![chlimage_1-13](assets/chlimage_1-13.png)

#### 后续步骤 {#the-next-steps}

为您的位置创建完显示屏后，您需要为显示屏分配渠道。

See [Assign Channels](channel-assignment.md) for more details.
