---
title: AEM 平台配置
seo-title: AEM 平台配置
description: 本页介绍AEM Platform配置
seo-description: 本页介绍AEM Platform配置
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 21%

---

# AEM 平台配置  {#platform-configurations}

>[!NOTE]
>
>本活动的典型利益相关方是AEM实施者。

请按照以下部分设置AEM平台配置以开始使用AEM Screens。

## 服务器配置{#server-configurations}

要设置服务器配置，请参阅[服务器配置](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration)。

## 创作 — 发布{#author-publish}

要设置author-publish，请参阅[在AEM Screens中配置作者和发布](https://helpx.adobe.com/cn/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>如果只有一位作者和一个发布，您只需按照[在 AEM Screens 中配置作者和发布](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)页面中&#x200B;**设置作者复制代理**&#x200B;下的步骤操作即可。

## 调度程序配置{#dispatcher-configurations}

Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。使用 AEM 的 Dispatcher 还有助于保护 AEM 服务器免受攻击。因此，您可以通过将 Dispatcher 与企业级 Web 服务器结合使用来提高 AEM 实例的安全性。

请参阅&#x200B;**[AEM Screens的调度程序配置](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** ，其中重点介绍了为AEM Screens项目配置调度程序的准则。

## 安装FFMpeg和视频演绎版{#installing-ffmpeg}

按照相应操作系统（通常为RHEL）的步骤安装FFMpeg:

1. 如果通过启用EPEL和RPMFusion进行安装，则可以安装所有gstreamer编解码器以扩大对FFmpeg转换的支持
1. 如果AAC编解码器标记为实验性，则ffmpeg转换将失败。 为避免向视频配置文件(AEM 6.3中的/etc/dam/video)添加 — strict -2，并将其移至AEM 6.4中的/libs/settings/dam/video)
   >[!NOTE]
   >
   > 请注意，-strict -2必须是参数列表中的最后一个参数。 此外，在AEM 6.4中，您还需要将&#x200B;*/libs/settings/dam/video*&#x200B;下的节点复制到&#x200B;*/conf/global/settings/dam/video*，如[视频呈现](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html)中所述。
1. 验证视频转化是否正在进行以及是否正在创建演绎版。

## 密码限制{#password-restrictions}

需要在AMS实例上禁用AEM的密码策略。 可以使用Screens设备服务&#x200B;*com.adobe.cq.screens.device.impl.DeviceService*在Web控制台中交替配置此设置
请参阅[在AEM Screens中配置作者和发布](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)中的&#x200B;**密码限制**&#x200B;部分

## 设置环境{#setting-up-environments}

为您的Adobe Experience Manager(AEM)版本安装并运行以下最新版本的软件包：

* AEM Service Pack
* Screens功能包
* AEM 累积修补程序包

除了上述功能外，还需识别任何开发包(例如，WCM Core
组件)或第三方工具包（例如，SAP Hybris）。
在本地开发环境中安装相同的软件包。 指示您的客户端在其所有QA、暂存和生产服务器上采用相同的配置。 不匹配的服务器配置在部署和测试时会出现问题。

>[!NOTE]
>
>要安装最新的AEM Screens功能包，请参阅[发行说明](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js)。

## 设置ACL {#setting-up-acls}

设置ACL说明如何隔离项目，以便每个人或团队都能够处理自己的项目。

有关更多详细信息，请参阅[设置ACL](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) 。
