---
title: 设备注册
seo-title: 设备注册
description: 本页介绍AEM Screens项目中的设备注册过程。
seo-description: 本页介绍AEM Screens项目中的设备注册过程。
uuid: 5365e506-1641-4a0c-b34d-c39da02f700b
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 523084f6-bd71-4daf-95b7-fc4c481f76dc
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 1%

---


# 设备注册 {#device-registration}

下页介绍了AEM Screens项目中的设备注册过程。

## 注册设备 {#registering-a-device}

设备注册过程在两台单独的计算机上完成：

* 要注册的实际设备，例如标牌展示广告
* 用于注册设备的AEM服务器

>[!NOTE]
>
>从AEM 6.4 Player下载页&#x200B;*面下载最新的Windows* Player( [.exe)后](https://download.macromedia.com/screens/) ，请按照播放器上的步骤完成临时安装：
>
>1. 长按左上角以打开管理面板。
>1. 从左侧 **操作** 菜单导航到配置，在服务器中输入AEM实例的位置地 **址** ，然后单 **击保存**。
>1. 单击左侧操 **作菜单** 中的“注册”链接和以下步骤以完成设备注册过程。

>



![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. 在您的设备上开始AEM Screens播放器。 将显示注册UI。

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. 在AEM中，导航到 **项目** 的“设备”文件夹。

   >[!NOTE]
   >
   >要获取有关在AEM仪表板中为Screens创建新项目的更多信息，请参 [阅创建和管理Screens项目](creating-a-screens-project.md)。

1. 点按／单击操 **作栏中** 的设备管理器按钮。

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. 点按／单击右 **上方的** “设备注册”按钮。

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. 选择所需的设备（与步骤1相同），然后点按／单击注 **册设备**。

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. 在AEM中，等待设备发送其注册代码。

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. 在您的设备中，检查注 **册代码**。

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. 如果注 **册代码** （在两台计算机上）相同 **，请点按／单击AEM中的验** 证(如步骤(6)所示)。
1. 为设备设置所需的名称，然后单击“注 **册”**。

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Tap/click **Finish** to complete the registration process.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >通过 **新注册** ，您可以注册新设备。
   >
   >通过 **“指定显** 示屏”，您可以直接将设备添加到显示屏。

   如果单击“ **完成**”，则需要将设备分配到显示屏。

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >要进一步了解如何为Screens项目创建和管理显示屏，请参阅创 [建和管理显示屏](managing-displays.md)。

### 将设备分配给显示屏 {#assigning-device-to-a-display}

如果尚未将设备分配给显示屏，请按照以下步骤将设备分配给您的AEM Screens项目中的显示屏：

1. 选择设备，然后单 **击操作栏** 中的指定设备。

   ![screen_shot_2018-11-26at11026am](assets/screen_shot_2018-11-26at111026am.png)

1. 在显示／设备配置路 **径中选择显示路径**。

   ![screen_shot_2018-11-26at11252am](assets/screen_shot_2018-11-26at111252am.png)

1. 选择 **路径** 时，单击“分配”。

   ![screen_shot_2018-11-26at11722am](assets/screen_shot_2018-11-26at111722am.png)

1. 成功 **分配设** 备后，单击“完成”，如下图所示。

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   此外，单击“完成”后，可视图显 **示仪表板**。

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## 设备注册限制 {#limitations-on-device-registration}

系统范围的用户密码限制可能导致设备注册失败。 设备注册使用随机生成的口令来创建设备用户。

如果密码受AuthorizableActionProvider配 *置限制* ，则创建设备用户可能失败。

>[!NOTE]
>
>当前生成的随机密码由36个ASCII字符组成，范围从33到122（包括几乎所有特殊字符）。

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### 其他资源 {#additional-resources}

要了解AEM Screens播放器，请参阅 [AEM Screens播放器](working-with-screens-player.md)。
