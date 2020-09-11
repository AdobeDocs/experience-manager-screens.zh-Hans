---
title: AEM 平台配置
seo-title: AEM 平台配置
description: 本页介绍AEM平台配置
seo-description: 本页介绍AEM平台配置
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 21%

---

# AEM 平台配置  {#platform-configurations}

>[!NOTE]
>
>本活动的典型利益相关方是AEM实施者。

请按照以下各节设置AEM平台配置，以开始使用AEM Screens。

## 服务器配置 {#server-configurations}

要设置服务器配置，请参阅服 [务器配置](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration)。

## 作者发布 {#author-publish}

要设置作者发布，请参阅在AEM Screens [配置作者和发布](https://helpx.adobe.com/cn/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>如果只有一位作者和一个发布，您只需按照[在 AEM Screens 中配置作者和发布](https://helpx.adobe.com/cn/experience-manager/6-5/screens/using/author-and-publish.html)页面中&#x200B;**设置作者复制代理**&#x200B;下的步骤操作即可。

## 调度程序配置 {#dispatcher-configurations}

Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。使用 AEM 的 Dispatcher 还有助于保护 AEM 服务器免受攻击。因此，您可以通过将 Dispatcher 与企业级 Web 服务器结合使用来提高 AEM 实例的安全性。

请参阅AEM Screens **[调度程序配置](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** ，其中重点介绍了为AEM Screens项目配置调度程序的指南。

## 安装FFMpeg和视频演绎版 {#installing-ffmpeg}

按照相应操作系统（通常为RHEL）的步骤安装FFMpeg:

1. 如果通过启用EPEL和RPMFusion进行安装，则可以安装所有gstreamer编解码器以扩大对FFmpeg转换的支持
1. 如果将AAC编解码器标记为“实验”，则ffmpeg转换将失败。 要避免向视频用户档案添加-strict -2(AEM 6.3中的/etc/dam/video，并在AEM 6.4中移至/libs/settings/dam/video)
   >[!NOTE]
   >
   > 请注意，-strict -2必须是参数列表中的最后一个参数。 此外，在AEM 6.4中，您需要将/libs/settings/dam/video下的 *节点复制到* /conf/ *global/settings/dam/video，如视频演绎版中所* 述 [](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html)。
1. 验证视频转换是否正在进行以及是否正在创建再现。

## 密码限制 {#password-restrictions}

需要在AMS实例上禁用AEM的口令策略。 在Web控制台中，也可以使用Screens设备服务com.adobe.cq.screens.device.impl.DeviceService *在AEM Screens*&#x200B;配置作者和发布 **中参** 考“口令限[制”部分来进行此配置](https://helpx.adobe.com/cn/experience-manager/6-5/screens/using/author-and-publish.html)

## 设置环境 {#setting-up-environments}

为您的Adobe Experience Manager(AEM)版本安装并运行以下软件包的最新版本：

* AEM Service Pack
* 屏幕功能包
* AEM 累积修复程序包

除上述内容外，还需标识所需的任何开发包（例如，WCM Corecomponents）或第三方工具包（例如，SAP Hybris）。
在本地开发环境上安装相同的软件包。 指示客户端在其所有QA、Stage和Production服务器上采用相同的配置。 在部署和测试时，不匹配的服务器配置将产生问题。

>[!NOTE]
>
>要安装最新的AEM Screens功能包，请参阅 [发行说明](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js)。

## 设置ACL {#setting-up-acls}

设置ACL将说明如何隔离项目，使每个个人或团队都能处理自己的项目。

Refer  to [Setting up ACLs](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) for more details.
