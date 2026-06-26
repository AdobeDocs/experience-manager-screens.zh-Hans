---
title: AEM平台配置
description: 本页介绍了AEM平台配置
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
TQID: https://experienceleague.adobe.com/qsJ-vj45WoTXXdBU5zsNQYoB7g4HnNTLwwfFSBL-wwI
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 592
ht-degree: 4%

---

# AEM平台配置 {#platform-configurations}

>[!IMPORTANT]
>此内容对AEM on-premise/AMS（AEM 6.5LTS和AEM 6.5）有效。 有关AEM as a Cloud Service Screens的内容，请参阅[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

>[!NOTE]
>
>此活动的典型利益相关者是AEM实施者。

按照以下部分设置AEM Screens平台配置，开始使用AEM

## 服务器配置 {#server-configurations}

要设置服务器配置，请参阅[服务器配置](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration)。

## Author-Publish {#author-publish}

请参阅[在AEM Screens中配置作者和发布](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)。

>[!NOTE]
>
>如果只有一个“创作”和“发布”，则只能按照[在AEM Screens中配置“创作和发布”页面](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)中的&#x200B;**在创作实例上设置复制代理**&#x200B;下的步骤操作。

## Dispatcher 配置 {#dispatcher-configurations}

Dispatcher是Adobe Experience Manager的缓存和负载平衡工具。 使用 AEM 的 Dispatcher 还有助于保护 AEM 服务器免受攻击。 因此，您可以通过将Dispatcher与企业级Web服务器结合使用来提高AEM实例的安全性。

请参阅针对AEM Screens的&#x200B;**[Dispatcher配置](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)**，其中重点说明了为AEM Screens项目配置Dispatcher的指南。

## 安装FFMpeg和视频呈现版本 {#installing-ffmpeg}

按照相应操作系统（通常是RHEL）的步骤安装FFMpeg：

1. 如果通过启用EPEL和RPMFusion进行安装，则可以安装所有gstreamer编解码器，以扩大对FFmpeg转换的支持
1. 如果AAC编解码器标记为试验性的，则ffmpeg转换会失败。 要避免此问题，请将`-strict -2`添加到视频配置文件（AEM 6.3中的`/etc/dam/video`并移至`/libs/settings/dam/video in AEM 6.4`）

   >[!NOTE]
   >
   >`-strict -2`必须是参数列表中的最后一个参数。 此外，在AEM 6.4中，将&#x200B;*/libs/settings/dam/video*&#x200B;下的节点复制到&#x200B;*/conf/global/settings/dam/video*，如[视频呈现](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions)中所述。
1. 验证是否正在进行视频转换以及是否正在创建演绎版。

## 密码限制 {#password-restrictions}

必须在AMS实例上禁用AEM的密码策略。 也可以使用Screens设备服务&#x200B;*com.adobe.cq.screens.device.impl.DeviceService在Web控制台中交替配置它*
请参阅[在AEM Screens中配置作者和发布](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)中的&#x200B;**密码限制**&#x200B;部分

## 设置环境 {#setting-up-environments}

为您的版本Adobe Experience Manager (AEM)安装并运行以下包的最新版本：

* AEM Service Pack
* Screens功能包
* AEM累积修补程序包

除上述内容外，请确定任何开发包(例如WCM Core
组件)或所需的第三方工具包（例如SAP Hybris）。在本地开发环境中安装相同的软件包。 指示您的客户端在其所有QA、暂存和生产服务器上采用相同的配置。 服务器配置不匹配会在部署和测试时造成问题。

>[!NOTE]
>
>要安装AEM Screens的最新功能包，请参阅[发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-screens/user-guide/aem-screens-introduction)。

## 设置ACL {#setting-up-acls}

设置ACL说明了如何分离项目，以便每个个人或团队处理自己的项目。

有关详细信息，请参阅[设置ACL](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/setting-up-acls)。

