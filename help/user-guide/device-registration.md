---
title: 设备注册
description: 了解AEM Screens项目中的设备注册流程。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens, Device Registration
role: Admin
level: Intermediate
exl-id: b2d3a2cd-263f-4142-80da-29ce54cbf391
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# 设备注册 {#device-registration}

以下页面介绍了AEM Screens项目中的设备注册流程。

## 注册设备 {#registering-a-device}

设备注册过程在两个独立的计算机上完成：

* 要注册的实际设备，例如您的标牌显示器
* 用于注册设备的AEM服务器

>[!NOTE]
>
>下载最新的Windows Player后(*.exe*)，从 [AEM 6.4播放器下载](https://download.macromedia.com/screens/) 页面，按照播放器上的步骤完成临时安装：
>
>1. 长按左上角以打开管理面板。
>1. 导航到 **配置** 从左侧操作菜单中，输入AEM实例的位置地址 **服务器** 并选择 **保存**.
>1. 选择 **注册** 左侧操作菜单中的链接以及完成设备注册过程的以下步骤。
>

![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. 在设备上，启动AEM Screens Player。 将显示注册UI。

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. 在AEM中，导航到 **设备** 文件夹中的任意位置。

   >[!NOTE]
   >
   >要获取有关在AEM功能板中创建屏幕项目的更多信息，请参阅 [创建和管理Screens项目](creating-a-screens-project.md).

1. 选择 **设备管理器** 按钮进行更改。

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. 选择 **设备注册** 按钮。

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. 选择所需的设备（与步骤1相同），然后选择 **注册设备**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. 在AEM中，等待设备发送其注册码。

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. 在您的设备中，检查 **注册码**.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. 如果 **注册码** 两台计算机上相同，请选择 **验证** AEM按钮，如步骤(6)中所示。
1. 为设备设置所需的名称，然后选择 **注册**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. 选择 **完成** 以完成注册流程。

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >此 **新注册** 用于注册新设备。
   >
   >此 **分配显示区** 允许您将设备直接添加到显示区。

   如果您选择 **完成**，将设备分配给显示。

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >要了解有关为Screens项目创建和管理显示的更多信息，请参阅 [创建和管理显示区](managing-displays.md).

### 将设备分配给显示器 {#assigning-device-to-a-display}

如果尚未将设备分配给显示，请按照以下步骤将设备分配给AEM Screens项目中的显示：

1. 选择设备并选择 **指定设备** 从操作栏中。

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. 选择显示的路径 **显示器/设备配置路径**.

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. 选择 **分配** 选择路径时。

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. 选择 **完成** 成功分配设备后，如下图所示。

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   此外，您还可以在选择时查看显示仪表板 **完成**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## 从设备管理器中搜索设备 {#search-device}

当您将设备注册到播放器后，可以从设备管理器UI中查看所有设备。

1. 例如，从AEM Screens项目导航到设备管理器UI， **DemoScreens** > **设备**.

1. 选择 **设备** 文件夹并选择 **设备管理器** 从操作栏中。

   ![图像](/help/user-guide/assets/device-manager/device-manager-1.png)

1. 此时将显示已注册设备的列表。

1. 如果注册的设备列表很长，您现在可以使用操作栏中的搜索图标进行搜索

   ![图像](/help/user-guide/assets/device-manager/device-manager-2.png)

   或者，

   选择 `/` （正斜杠）以调用搜索功能。

   ![图像](/help/user-guide/assets/device-manager/device-manager-3.png)


### 搜索功能的限制 {#limitations}

* 用户能够搜索中存在的任何单词 *设备ID* 或 *设备名称*.

  >[!NOTE]
  >建议您用多个词创建设备名称，例如 *波士顿商店大厅* 而不是一个单身 *BostonStoreLobby*.

* 如果您创建设备名称，例如 *波士顿商店大厅*，它会搜索任意单词 *波士顿*， *存储*，或 *大厅*. 但是，如果设备名称为 *BostonStoreLobby*，然后搜索 *波士顿* 不显示任何结果。

* 通配符， `*` 支持搜索。 如果您希望查找所有名称以开头的设备， *波士顿*，您可以使用 *波士顿**.

* 如果设备名称为 *BostonStoreLobby* 并搜索 *波士顿* 不返回结果，则使用 *波士顿**会返回结果。

## Device Registration的限制 {#limitations-on-device-registration}

系统范围的用户密码限制可能会导致设备注册失败。 设备注册使用随机生成的密码来创建设备用户。

如果密码受 *AuthorizableActionProvider* 配置，创建设备用户可能会失败。

>[!NOTE]
>
>当前生成的随机密码由36个ASCII字符组成，范围在33到122之间（几乎包括所有特殊字符）。

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### 其他资源 {#additional-resources}

要了解AEM Screens Player，请参阅 [AEM Screens Player](working-with-screens-player.md).
