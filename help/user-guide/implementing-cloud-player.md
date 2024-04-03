---
title: 实施Cloud Player
seo-title: Implementing Cloud Player
description: 按照此页面了解如何实施Cloud Player。
seo-description: Follow  this page to learn about the implementation of the Cloud Player.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 5b64ab8eea274aa85c61311d34b1ce065a5ba601
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---

# 实施Cloud Player  {#implementing-cloud-player}

AEM Screens传统上为各种平台（包括ChromeOS、Windows、Android和Tizen）提供独特的本机播放器应用程序。 但是，为响应我们用户不断变化的需求，我们引入了一个创新解决方案 — AEM Screens Cloud Player。

Cloud Player与以前本机应用程序有重大不同。 它是一个渐进式Web应用程序(PWA)，托管在服务器上。 这种变革性的做法为客户提供了一个直接在Web浏览器中运行的独立于平台的播放器。

访问Cloud Player只需访问https://player.adobescreens.com即可。 用户可以将其安装在设备上，而不管平台如何，并享受无缝的数字标牌体验。 Cloud Player的兼容性取决于支持PWA的现代浏览器的存在，从而确保跨各种设备的一致性能。 告别手动更新，向自动提供修复和功能的播放器问好，确保您随时都能拥有最新功能。 向基于PWA的Cloud Player的转变标志着我们数字标牌产品的一个令人振奋的进步，使其比以往任何时候都更易于访问、更通用、更便于用户使用。

本节介绍如何实施云播放器。

>[!NOTE]
>
>为了兼容Cloud Player，需要配备支持PWA的现代浏览器，以确保各种设备之间的性能一致。

## 安装Cloud Player {#installing-cloud-player}

Cloud Player的安装可能因平台而异。 通常，任何具有现代化浏览器的平台都可以通过执行以下步骤来运行云播放器应用程序：

1. 打开浏览器并输入 [云播放器URL](https://player.adobescreens.com) 地址栏中。
1. 浏览器会检查云播放器是否可安装，然后在地址栏中显示安装图标。

   ![图像](/help/user-guide/assets/cloud-player-install.png)

1. 单击确认对话框上的安装图标和安装按钮。 Cloud Player将作为独立应用程序安装在您的设备上，并且可以使用图标启动。

>[!NOTE]
>
>### Cloud Player安装选项 {#cloud-player-install-option}
>
1. PWA的安装选项也称为“添加到主屏幕”或A2HS功能。  对从Web安装PWA的支持因浏览器和平台而异。
1. 每个浏览器都有不同的标准来检查PWA应用程序是否可安装。 通常，浏览器会检查这些内容（此处提供了更多详细信息）：
>
* 如果应用程序具有清单json文件，且其中包含在平台上安装应用程序所需的最小键，即名称、图标、start_url、显示
* 如果应用程序有一个带回迁事件侦听器的Service Worker文件。
* 应用程序必须通过https提供。
>
1. 安装选项可能显示在不同浏览器和设备类型中的不同位置。 某些浏览器可能会隐藏选项菜单栏中的安装图标。

## 批量配置Cloud Player {#bulk-provisioning}

要在多个设备上批量配置Cloud Player，请执行以下操作：

1. 选择支持在网亭模式下运行带有URL的浏览器的MDM解决方案。
1. 您可以按照以下步骤将相同的配置应用到所有设备：

   1. 将config.json托管在服务器上，使其可访问，例如：https://&lt;config_server_host>/config.json
   1. 要安装云播放器并应用托管配置，请使用如下云播放器URL： https://player.adobescreens.com?playerConfigAddress=https://&lt;config_server_host>
   1. Cloud Player应用程序在根目录中查找config.json &lt;config_server_host>，解析config.json以获取自定义配置并应用这些配置。
   1. 这些配置将在播放器的每次重新加载时应用。

## Chrome操作系统上的批量配置 {#bulk-provisioning-chrome}

要了解有关在Chrome操作系统上进行批量配置的更多信息，请参阅： [在Chrome操作系统上安装Cloud Player](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

## AEM实例上所需的配置 {#bulk-provisioning-config-aem}

根据AEM实例的类型，选择以下指南之一以启用CORS b/w AEM &amp; cloud player：
* [AEM On-Premises/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

>[!NOTE]
>
## Google弃用Chrome应用程序
>
1. Chrome操作系统硬件上的Chrome应用程序：
>
Google一直在积极弃用Chrome应用程序而支持PWA应用程序，计划在2025年1月之前进行迁移。 因此，Chrome操作系统上的AEM Screens Player应用程序将根据共享时间线停止运行。我们敦促当前在生产中使用Chrome Player的客户计划转换到Screens Cloud Player。
>
1. Mac、Windows和Linux上的Chrome扩展播放器：
>
由于Google的弃用过程，从Google Chrome版本114开始，不再支持Screens Chrome扩展播放器。 我们强烈建议转换到我们的Screens Cloud Player，以满足您的所有开发和测试要求。

## 对外部内容检索的脱机支持 {#offline-support}

在各种使用场景中，渠道可能要求从外部源（例如，天气构件或Commerce集成的单页面应用程序）检索内容，这些外部源本身无法提供离线支持。 为了为这些特定用例启用离线功能，Cloud Player提供对自定义标头的支持。

Cloud Player采用网络优先缓存策略，这意味着它尝试从网络获取内容（然后使用最新更新缓存），回退到缓存的内容（如果可用）。 要为此内容检索实施离线支持，请求中必须包含自定义标头。 随后，带有自定义标头的请求将在播放器上缓存，便于离线访问内容，同时保持网络优先缓存策略。

```
// Sample fetch request with the 'X-Cache-Strategy' header
fetch(externalUrl, {
  headers: {
    'X-Cache-Strategy': 'external-cache'
  }
})
  .then(response => {
    // Handle the response, which may be from the network or cache.
    // Your logic here.
  })
  .catch(error => {
    // Handle any errors that may occur during the fetch operation.
    // Your error handling logic here.
  }); 
```

## 反馈

我们重视您的反馈！ 请通过此分享您的想法 [表单](https://forms.office.com/r/MQXX9JsuEd).
