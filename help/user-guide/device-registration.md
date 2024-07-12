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
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '722'
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
>从[AEM 6.4 Player下载](https://download.macromedia.com/screens/)页面下载最新的Windows Player (*.exe*)后，请按照播放器上的步骤完成临时安装：
>
>1. 长按左上角以打开管理面板。
>1. 从左侧操作菜单中导航到&#x200B;**配置**，输入&#x200B;**服务器**&#x200B;中AEM实例的位置地址，然后单击&#x200B;**保存**。
>1. 单击左侧操作菜单中的&#x200B;**注册**&#x200B;链接及以下步骤以完成设备注册过程。
>

![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. 在设备上，启动AEM Screens Player。 将显示注册UI。

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. 在AEM中，导航到项目的&#x200B;**设备**&#x200B;文件夹。

   >[!NOTE]
   >
   >要获取有关在AEM功能板中为Screens创建项目的更多信息，请参阅[创建和管理Screens项目](creating-a-screens-project.md)。

1. 单击操作栏中的&#x200B;**设备管理器**&#x200B;按钮。

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. 单击右上方的&#x200B;**设备注册**&#x200B;按钮。

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. 单击所需的设备（与步骤1相同），然后单击&#x200B;**注册设备**。

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. 在AEM中，等待设备发送其注册码。

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. 在您的设备中，检查&#x200B;**注册码**。

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. 如果两台计算机上的&#x200B;**注册码**&#x200B;相同，请单击AEM中的&#x200B;**验证**&#x200B;按钮，如步骤(6)所示。
1. 为设备设置所需的名称，然后单击&#x200B;**注册**。

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. 单击&#x200B;**完成**&#x200B;以完成注册过程。

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >通过&#x200B;**注册新设备**，您可以注册新设备。
   >
   >通过&#x200B;**分配显示区**，您可以直接将设备添加到显示区。

   如果单击&#x200B;**完成**，请将设备分配给显示设备。

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >要了解有关为您的Screens项目创建和管理显示的详细信息，请参阅[创建和管理显示](managing-displays.md)。

### 将设备分配给显示器 {#assigning-device-to-a-display}

如果尚未将设备分配给显示，请按照以下步骤将设备分配给AEM Screens项目中的显示：

1. 单击设备，然后单击操作栏中的&#x200B;**指定设备**。

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. 单击&#x200B;**显示/设备配置路径**&#x200B;中显示的路径。

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. 单击路径时，单击&#x200B;**分配**。

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. 成功分配设备后，单击&#x200B;**完成**，如下图所示。

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   此外，您还可以通过选择&#x200B;**完成**&#x200B;来查看显示仪表板。

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## 从设备管理器中搜索设备 {#search-device}

当您将设备注册到播放器后，可以从设备管理器UI中查看所有设备。

1. 从AEM Screens项目导航到设备管理器UI，例如&#x200B;**DemoScreens** > **设备**。

1. 单击&#x200B;**设备**&#x200B;文件夹，然后单击操作栏中的&#x200B;**设备管理器**。

   ![图像](/help/user-guide/assets/device-manager/device-manager-1.png)

1. 此时将显示已注册设备的列表。

1. 如果注册的设备列表很长，您现在可以使用操作栏中的搜索图标进行搜索

   ![图像](/help/user-guide/assets/device-manager/device-manager-2.png)

   或者，

   选择`/`（正斜杠）以调用搜索功能。

   ![图像](/help/user-guide/assets/device-manager/device-manager-3.png)


### 搜索功能的限制 {#limitations}

* 用户可以搜索&#x200B;*设备ID*&#x200B;或&#x200B;*设备名称*&#x200B;中存在的任何单词。

  >[!NOTE]
  >建议您用多个单词（如&#x200B;*`Boston Store Lobby`*）创建设备名称，而不是用一个&#x200B;*`BostonStoreLobby`*&#x200B;创建。

* 如果您创建了设备名称，如&#x200B;*`Boston Store Lobby`*，它将搜索任意单词&#x200B;*`boston`*、*`store`*&#x200B;或&#x200B;*`lobby`*。 但是，如果设备名称为&#x200B;*`BostonStoreLobby`*，则搜索&#x200B;*`boston`*&#x200B;不会显示任何结果。

* 支持使用通配符`*`进行搜索。 如果要查找名称以&#x200B;*`boston`*&#x200B;开头的所有设备，可以使用*`boston`**。

* 如果设备名称为&#x200B;*`BostonStoreLobby`*&#x200B;且搜索&#x200B;*`boston`*&#x200B;未返回结果，则在搜索条件中使用&#x200B;*`boston`**将返回结果。

## Device Registration的限制 {#limitations-on-device-registration}

系统范围的用户密码限制可能会导致设备注册失败。 设备注册使用随机生成的密码来创建设备用户。

如果&#x200B;*AuthorizableActionProvider*&#x200B;配置限制密码，则创建设备用户可能会失败。

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

要了解有关AEM Screens Player的更多信息，请参阅[AEM Screens Player](working-with-screens-player.md)。
