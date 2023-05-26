---
title: AEM 平台配置
seo-title: AEM Platform Configurations
description: 本页介绍了AEM平台配置
seo-description: The page describes AEM Platform Configurations
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 21%

---

# AEM 平台配置  {#platform-configurations}

>[!NOTE]
>
>此活动的典型利益相关者是AEM实施者。

请按照以下部分设置AEM平台配置以开始使用AEM Screens。

## 服务器配置 {#server-configurations}

要设置服务器配置，请参阅 [服务器配置](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration).

## Author-Publish {#author-publish}

要设置作者发布，请参阅 [在AEM Screens中配置“创作”和“发布”](https://helpx.adobe.com/cn/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>如果只有一位作者和一个发布，您只需按照[在 AEM Screens 中配置作者和发布](https://helpx.adobe.com/cn/experience-manager/6-5/screens/using/author-and-publish.html)页面中&#x200B;**设置作者复制代理**&#x200B;下的步骤操作即可。

## Dispatcher 配置 {#dispatcher-configurations}

Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。使用 AEM 的 Dispatcher 还有助于保护 AEM 服务器免受攻击。因此，您可以通过将 Dispatcher 与企业级 Web 服务器结合使用来提高 AEM 实例的安全性。

请参阅 **[适用于AEM Screens的Dispatcher配置](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** 其中重点介绍了为AEM Screens项目配置Dispatcher的准则。

## 安装FFMpeg和视频呈现版本 {#installing-ffmpeg}

按照相应操作系统（通常为RHEL）的步骤安装FFMpeg：

1. 如果通过启用EPEL和RPMFusion进行安装，则可以安装所有gstreamer编解码器，以扩大对FFmpeg转换的支持
1. 如果AAC编解码器标记为实验性，则ffmpeg转换将失败。 要避免出现这种情况，请在视频配置文件中添加 — strict -2(在AEM 6.3中为/etc/dam/video，在AEM 6.4中为/libs/settings/dam/video)
   >[!NOTE]
   >
   > 请注意，-strict -2必须是参数列表中的最后一个参数。 此外，在AEM 6.4中，您需要复制 */libs/settings/dam/video* 到 */conf/global/settings/dam/video* 如中所述 [视频演绎版](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html).
1. 验证是否正在进行视频转换以及是否正在创建演绎版。

## 密码限制 {#password-restrictions}

需要在AMS实例上禁用AEM的密码策略。 这可以使用Screens设备服务在Web控制台中交替配置 *com.adobe.cq.screens.device.impl.DeviceService*
请参阅 **密码限制** 中的部分[在AEM Screens中配置“创作”和“发布”](https://helpx.adobe.com/cn/experience-manager/6-5/screens/using/author-and-publish.html)

## 设置环境 {#setting-up-environments}

为您的Adobe Experience Manager (AEM)版本安装并运行以下包的最新版本：

* AEM 服务包
* Screens功能包
* AEM 累积修订包

除上述内容外，请确定所需的任何开发包（例如WCM核心组件）或第三方工具包（例如SAP Hybris）。
在本地开发环境中安装相同的软件包。 指示您的客户端在其所有QA、暂存和生产服务器上采用相同的配置。 服务器配置不匹配将在部署和测试时造成问题。

>[!NOTE]
>
>要安装AEM Screens的最新功能包，请参阅 [发行说明](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js).

## 设置ACL {#setting-up-acls}

设置ACL说明了如何分隔项目，以便每个个人或团队处理自己的项目。

请参阅 [设置ACL](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) 了解更多详细信息。
