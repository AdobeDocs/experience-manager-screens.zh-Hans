---
title: 播放器的自动注册
seo-title: 播放器的自动注册
description: 可查看本页以了解有关使用AMS/On-Prem屏幕自动注册播放器的信息。
translation-type: tm+mt
source-git-commit: 793507b266b99051544b377e4a7effb92dc6feb6
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# 播放器的自动注册{#auto-registration}

手动批量注册数千个播放器可能会变得非常繁琐，并增加时间和成本。 为简化此过程，批量注册功能允许您在AEM中指定预先共享的密钥，该密钥可以通过配置文件或移动设备管理(MDM)解决方案设置到播放器中。

## 实现播放器的自动注册{#bulk-registering-implementation}

请按照以下步骤实现播放器的自动注册：

1. 登录AEM实例并选择AEM screens项目，然后单击操作栏中的&#x200B;**属性**。
1. 选择&#x200B;**高级**&#x200B;选项卡以视图&#x200B;**设备注册**&#x200B;部分。

1. 在&#x200B;**批量注册代码**&#x200B;字段中指定自动注册代码，在&#x200B;**默认显示分配**&#x200B;中指定可选的默认显示，以分配给自动注册的播放器。
   >[!NOTE]
   >输入您选择的代码，然后根据需要选择默认显示。

   ![图像](/help/user-guide/assets/auto-registration/auto-register1.png)
1. 使用MDM或配置JSON文件，为您的播放器提供适当的服务器URL和注册代码。

   >[!NOTE]
   >有关详细信息，请参阅操作系统(OS)的特定播放器的实施页。 您还可以使用管理员UI输入注册代码。

1. 如果`registrationKey`属性与AEM中配置的属性匹配，则播放器将自动注册自己，如果配置了默认显示，则该内容将下载并播放。

   ![图像](/help/user-guide/assets/auto-registration/auto-register2.png)

## 安全最佳实践{#security-best-practices}

请按照以下部分考虑安全方面的一些最佳实践：

* 要确保注册代码不会泄露，请在启动批量注册之前在AEM中配置该代码，完成后，请清除该字段并保存在AEM中。

* 可以将路径`/bin/screens/registration`配置为仅可从已知IP范围访问（如果可能）。

* 请考虑使用MDM为播放器配置配置。

* 始终使用`HTTPS`而不是`HTTP`与AEM进行播放器通信。

   >[!NOTE]
   >默认显示分配当前仅适用于批量注册，而不适用于没有注册代码的手动注册。