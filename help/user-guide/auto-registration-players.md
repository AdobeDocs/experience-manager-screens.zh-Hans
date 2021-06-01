---
title: 播放器的自动注册
seo-title: 播放器的自动注册
description: 请阅读本页，了解使用AMS/On-Prem Screens自动注册播放器的信息。
feature: 管理屏幕、播放器
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# 播放器自动注册{#auto-registration}

手动批量注册数千个播放器可能会变得非常麻烦，并会增加时间和成本。 为简化此过程，批量注册功能允许您在AEM中指定预共享密钥，该密钥可通过配置文件或移动设备管理(MDM)解决方案配置到播放器中。

## 实施播放器自动注册{#bulk-registering-implementation}

请按照以下步骤实施播放器的自动注册：

1. 登录AEM实例并选择您的AEM screens项目，然后单击操作栏中的&#x200B;**属性**。
1. 选择&#x200B;**Advanced**&#x200B;选项卡以查看&#x200B;**Device registration**&#x200B;部分。

1. 在&#x200B;**批量注册代码**&#x200B;字段中指定自动注册代码，并在&#x200B;**默认显示分配**&#x200B;中指定一个可选的默认显示，以分配给自动注册的播放器。
   >[!NOTE]
   >输入您选择的代码，并根据需要选择默认显示。

   ![图像](/help/user-guide/assets/auto-registration/auto-register1.png)
1. 使用MDM或配置JSON文件为播放器配置相应的服务器URL和注册代码。

   >[!NOTE]
   >有关更多详细信息，请参阅适用于您的操作系统(OS)的特定播放器的实施页面。 您还可以使用管理员UI输入注册代码。

1. 如果`registrationKey`属性与AEM中配置的属性匹配，则播放器将自动注册自身，如果配置了默认显示，则将下载和播放该内容。

   ![图像](/help/user-guide/assets/auto-registration/auto-register2.png)

## 安全最佳实践{#security-best-practices}

请按照以下部分考虑一些安全最佳实践：

* 要确保注册代码不会受到破坏，请在开始批量注册之前在AEM中配置该代码，完成后，请清除该字段，并将其保存在AEM中。

* 您可以将路径`/bin/screens/registration`配置为只能从已知的IP范围访问（如果可能）。

* 考虑使用MDM为播放器配置配置。

* 与AEM进行播放器通信时，请始终使用`HTTPS`，而不使用`HTTP`。

   >[!NOTE]
   >默认显示分配当前仅适用于批量注册，而不适用于没有注册代码的手动注册。