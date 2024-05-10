---
title: AEM平台配置
description: 本页介绍了AEM平台配置
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 3%

---

# AEM平台配置 {#platform-configurations}

>[!NOTE]
>
>此活动的典型利益相关者是AEM实施者。

按照以下部分设置AEM平台配置，开始使用AEM Screens

## 服务器配置 {#server-configurations}

要设置服务器配置，请参见 [服务器配置](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration).

## Author-Publish {#author-publish}

请参阅 [在AEM Screens中配置创作和发布](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

>[!NOTE]
>
>如果只有一个“作者”和一个“发布”，则您只能执行下的步骤 **设置创作实例上的复制代理** 在 [在AEM Screens中配置创作和发布](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish) 页面。

## Dispatcher 配置 {#dispatcher-configurations}

Dispatcher是Adobe Experience Manager的缓存和负载平衡工具。 使用 AEM 的 Dispatcher 还有助于保护 AEM 服务器免受攻击。因此，您可以通过将Dispatcher与企业级Web服务器结合使用来提高AEM实例的安全性。

请参阅 **[适用于AEM Screens的Dispatcher配置](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)** 其中重点介绍了为AEM Screens项目配置Dispatcher的准则。

## 安装FFMpeg和视频呈现版本 {#installing-ffmpeg}

按照相应操作系统（通常是RHEL）的步骤安装FFMpeg：

1. 如果通过启用EPEL和RPMFusion进行安装，则可以安装所有gstreamer编解码器，以扩大对FFmpeg转换的支持
1. 如果AAC编解码器标记为试验性的，则ffmpeg转换会失败。 要避免此添加，请执行以下操作 `-strict -2` 到视频配置文件(AEM 6.3中的/etc/dam/video并移至AEM 6.4中的/libs/settings/dam/video)

   >[!NOTE]
   >
   >此 `-strict -2` 必须是参数列表中的最后一个参数。 此外，在AEM 6.4中，复制 */libs/settings/dam/video* 到 */conf/global/settings/dam/video* 如中所述 [视频演绎版](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions).
1. 验证是否正在进行视频转换以及是否正在创建演绎版。

## 密码限制 {#password-restrictions}

必须在AMS实例上禁用AEM的密码策略。 也可以使用Screens设备服务在Web控制台中交替配置它 *com.adobe.cq.screens.device.impl.DeviceService*
请参阅 **密码限制** 中的部分[在AEM Screens中配置创作和发布](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)

## 设置环境 {#setting-up-environments}

为您的版本Adobe Experience Manager (AEM)安装并运行以下包的最新版本：

* AEM Service Pack
* 屏幕功能包
* AEM累积修补程序包

除上述内容外，请确定所需的任何开发包（例如WCM核心组件）或第三方工具包（例如SAP Hybris）。
在本地开发环境中安装相同的软件包。 指示您的客户端在其所有QA、暂存和生产服务器上采用相同的配置。 服务器配置不匹配会在部署和测试时造成问题。

>[!NOTE]
>
>要安装AEM Screens的最新功能包，请参阅 [发行说明](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/aem-screens-introduction).

## 设置ACL {#setting-up-acls}

设置ACL说明了如何分离项目，以便每个个人或团队处理自己的项目。

请参阅 [设置ACL](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/setting-up-acls) 以了解更多详细信息。
