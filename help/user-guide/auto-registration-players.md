---
title: 播放器自动注册
description: 按照此页面进行操作，以便了解使用AMS/内部部署屏幕自动注册播放器的相关信息。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 播放器自动注册 {#auto-registration}

手动批量注册数千个播放器可能会变得繁琐并增加时间和成本。 为简化此过程，批量注册功能允许您在AEM中指定预共享密钥，该密钥可通过配置文件或移动设备管理(MDM)解决方案配置到播放器中。

## 实施播放器自动注册 {#bulk-registering-implementation}

请按照以下步骤实施播放器的自动注册：

1. 登录到您的AEM实例，选择您的AEM Screens项目，然后单击 **属性** 从操作栏中。
1. 选择 **高级** 选项卡，以便您查看 **设备注册** 部分。

1. 在中指定自动注册代码 **批量注册代码** 字段和可选的默认显示 **默认显示分配** 以分配给自动注册的播放器。

   >[!NOTE]
   >输入您选择的代码，并根据需要选择默认显示。

   ![图像](/help/user-guide/assets/auto-registration/auto-register1.png)
1. 使用MDM或配置JSON文件为播放器配置相应的服务器URL和注册码。

   >[!NOTE]
   >有关更多详细信息，请参阅适用于您的操作系统(OS)的特定播放器的实施页面。 您还可以使用管理员UI输入注册码。

1. 如果 `registrationKey` 属性与AEM中配置的属性匹配，播放器会自动注册自身，如果配置了默认显示，则会下载并播放该内容。

   ![图像](/help/user-guide/assets/auto-registration/auto-register2.png)

## 安全最佳实践 {#security-best-practices}

请阅读以下章节，以考虑一些最佳安全实践：

* 确保注册代码不被破坏 — 在开始批量注册之前在AEM中配置代码，完成后，清除该字段并保存在AEM中。

* 您可以配置路径 `/bin/screens/registration` 仅在已知IP范围中可访问（如果可能）。

* 考虑使用MDM为播放器配置配置。

* 始终使用 `HTTPS` 而非 `HTTP` 用于与AEM进行播放器通信。

  >[!NOTE]
  >默认显示分配当前仅适用于批量注册，不适用于没有注册代码的手动注册。
