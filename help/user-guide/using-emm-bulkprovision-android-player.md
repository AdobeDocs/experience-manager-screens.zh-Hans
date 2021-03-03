---
title: 使用MDM或EMM批量配置Android Player
seo-title: 使用EMM或MDM批量设置Android Player
description: 可查看本页以了解有关使用EMM或MDM批量设置Android Player的信息
translation-type: tm+mt
source-git-commit: 793507b266b99051544b377e4a7effb92dc6feb6
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---


# 使用企业移动管理{#bulk-provisioning}批量配置Android Player

批量部署Android播放器时，使用AEM手动注册每个播放器会变得很繁琐。 强烈建议使用VMWare Airwatch、MobileIron或Samsung Knox等EMM（企业移动管理）解决方案来远程配置和管理您的部署。 AEM Screens Android player支持行业标准EMM AppConfig，以允许远程设置。

## 使用企业移动管理{#implementation}实现Android Player的批量配置

请按照以下步骤允许在Android Player中进行批量配置：

1. 确保您的Android设备支持Google Play服务。
1. 使用您喜爱的支持AppConfig的EMM解决方案注册您的Android播放器设备。
1. 登录您的EMM控制台，然后从Google Play中拉取AEM Screens Player应用程序。
1. 选择受管配置（或相关选项）。
1. 您现在应该会看到可配置的播放器选项列表（如服务器和批量注册代码）。
1. 配置这些参数，保存策略并将其部署到设备。

   >[!NOTE]
   >设备应接收应用程序及配置，并指向正确的AEM服务器并选择配置。 如果您选择配置批量注册代码并将其保持与AEM中配置的相同，则播放器应能够自动注册自己。 如果您已配置默认显示，则还可以下载并显示某些默认内容（以后可以根据您的方便而更改）。

此外，您应与EMM供应商确认AppConfig支持。 最流行的产品，如[VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、[Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)、[SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)、[Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)、[IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)和[Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)等支持此行业标准。


