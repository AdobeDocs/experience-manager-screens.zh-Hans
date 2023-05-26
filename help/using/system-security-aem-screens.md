---
title: AEM Screens安全核对清单
seo-title: Security Checklist for AEM Screens
description: 本页介绍了AEM Screens的安全核对清单
seo-description: The page describes Security Checklist for AEM Screens
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 1%

---


# AEM Screens的系统安全注意事项 {#security-checklist}

>[!IMPORTANT]
>这是内部Git资源。

本页重点介绍了AEM Screens的系统安全注意事项。


## AEM Screens安全白皮书 {#white-paper}

本节介绍白皮书。 （待处理白皮书附件）


## AEM Screens安全性常见问题解答 {#faqs-screens}

以下常见问题解答采用经过身份验证的注册播放器架构，该架构使用HTTPS作为播放器和AEM Server之间的通信协议。

### 常见问题解答1 {#faq1}

播放器流量是否可以重新路由到恶意服务器，并指示下载和播放恶意媒体内容？

**答案**

这是不可能的，因为HTTPs连接标识连接的两端并对其加密。 如果您试图置身于中间并拦截它，则只会看到加密的内容，而如果您尝试模拟服务器，则播放器将拒绝您，因为您的证书不同。


### 常见问题解答2 {#faq2}

我应该使用HTTP还是HTTP？

**答案**

使用HTTP。 如果您担心安全问题，这是必须的。 利用HTTP协议，播放器与服务器之间的通信会被加密，拦截内容或修改内容几乎是不可能的。


### 常见问题解答3 {#faq3}

下载内容时，是否有任何内容或哈希的签名？

**答案**

每个资产都由服务器签名(SHA)，然后由播放器验证相同的哈希以确保完整性。
如果哈希不匹配，我们会尝试重新验证3次。 尝试3次后，我们认为下载命令无效。


### 常见问题解答4 {#faq4}

AEM Server是否安全？

**答案**

回答4。 假设您使用的是AMS，那么我们使用与Sites或Assets相同的功能来保护所有服务器安全性。


### 常见问题解答5 {#faq5}

设备是否安全？

**答案**

从理论上讲，物理上受损的播放器可以被操纵以播放任何内容。 您也可以直接将播放器插上USB/HDMI卡。

因此，建议最好将设备放在安全的容器中，并固定电缆。 同时禁用任何IR远程端口。

如果设备操作系统未定期更新，则操作系统可能会暴露在安全漏洞中，并允许通过网络进行远程攻击。

>[!NOTE]
>
>建议使用合适的远程更新和控制功能（远程桌面、MDM解决方案等）来检测设备。 此外，建议使用专用网络，例如，不要向公共WIFI公开。


### 常见问题解答6 {#faq6}

黑客如何尝试危害玩家？

**答案**

危害播放器设备的唯一方法是：

1. 危害DNS以模拟服务器的主机名，并且
1. 折中
   1. 用于模拟服务器的证书服务器端
   1. 设备和模拟证书客户端

>[!IMPORTANT]
>即使设备受到危害，您仍然可以轻松撤销其凭据，以便它无法再连接到AEM。





