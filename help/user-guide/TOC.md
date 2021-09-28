---
cloud: experience-cloud
product: experience manager
audience: end-user
user-guide-title: Adobe Experience Manager Screens 帮助
breadcrumb-title: AEM Screens 指南
user-guide-description: 了解如何使用这款数字标牌解决方案，发布动态的交互式数字体验与交互内容。
feature-set: Experience Manager Screens
source-git-commit: 8676b259304326ef3319ef40aa072b9d2a292a2e
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 18%

---


# AEM Screens 用户指南 {#user-guide}

+ [Screens简介](aem-screens-introduction.md)
+ 概述和Kickstart指南{#overview}
   + [Kickstart指南](kickstart-for-aem-screens.md)
   + [Screens最佳实践指南](https://docs.adobe.com/content/help/zh-Hans/experience-manager-screens/using/about-guide.html)
   + [关键术语](screens-glossary.md)
+ 数字标牌网络基础知识{#digital-signage-network}
   + [第一部分：项目角色和职责](project-roles-responsibilities.md)
   + [第2部分：关于项目适用范围的注意事项](project-considerations.md)
   + [第三部分：测试、POC、试点和推广](testing-pocs-pilots-rollouts.md)
   + [第4部分：项目管理和部署](project-management-and-deployment.md)
   + [第5部分：支持注意事项](support-considerations.md)
+ 配置和管理{#administering}
   + [Screens服务器配置](configuring-screens-introduction.md)
   + [设置调度程序配置](dispatcher-configurations-aem-screens.md)
   + [安装Screens播放器](installing-screens-player.md)
   + [连接Screens播放器](working-with-screens-player.md)
   + [设备注册](device-registration.md)
   + [设置ACL](setting-up-acls.md)
   + [AEM Screens安全检查列表](security-checklist.md)
   + [从ContentSync过渡到SmartSync](smartsync.md)
   + [从文件新建项目导入程序](project-importer.md)
   + [将数据触发器复制到发布服务器](replicating-data-triggers.md)
   + 客户端特定注意事项{#installing-client}
      + [Chrome OS Player](implementing-chrome-os-player.md)
      + [使用Chrome播放器作为扩展进行疑难解答](using-chrome-player-as-an-extension.md)
      + [Android Player](implementing-android-player.md)
      + [Windows Player](implementing-windows-player.md)
      + [蒂森球员](tizen-player.md)
      + [播放器的自动注册](auto-registration-players.md)
   + 作者发布{#author-publish}
      + [创作 — 发布架构概述](author-publish-architecture-overview.md)
      + [配置创作和发布](author-and-publish.md)
   + Analytics与AEM Screens的集成{#analytics-integration}
      + [Adobe Analytics 集成](adobe-analytics-integration-aem-screens.md)
      + [使用Adobe Analytics配置AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ 创作和用例示例{#authoring}
   + 设置Screens项目{#setting-up-projects}
      + [创建和管理项目](creating-a-screens-project.md)
      + [创建和管理渠道](managing-channels.md)
      + [创建和管理显示屏](managing-displays.md)
      + [创建和管理位置](managing-locations.md)
      + [创建和管理计划](managing-schedules.md)
      + [管理设备](managing-devices.md)
      + 分配渠道 {#assigning-channels}
         + [渠道分配](channel-assignment-latest-fp.md)
         + [渠道分配：旧版AEM Screens功能包](channel-assignment.md)
   + 使用核心产品功能{#product-features}
      + [文本覆盖](text-overlay.md)
      + [批量离线更新](bulk-offline-update.md)
      + [AEM Screens通知服务](screens-notifications-service.md)
      + [使用体验片段](experience-fragments-in-screens.md)
      + [资产级别激活](asset-level-scheduling.md)
      + [渠道级别激活](channel-level-activation.md)
      + [创建和管理Live Copy](managing-livecopy.md)
      + [创建视频内边距工作流](creating-a-video-padding-workflow.md)
      + [向渠道添加组件](adding-components-to-a-channel.md)
      + [嵌入式序列](embedded-sequences.md)
      + [多区域布局](multi-zone-layout-aem-screens.md)
      + [视频演绎版](generating-renditions.md)
      + [动态嵌入式序列](dynamic-embedded-sequences.md)
      + [通道级别批量图像播放持续时间](channel-level-image-playback.md)
      + [命令同步](using-command-sync.md)
      + [使用数据触发器进行创作](authoring-data-triggers.md)
      + [语音识别](voice-recognition.md)
      + [内容分配报告](content-assignment-report.md)
      + [视频的缩略图支持](thumbnail-support.md)
      + [在AEM Screens中使用自适应演绎版](using-adaptive-renditions.md)
   + 管理内容更新{#content-updates}
      + [按需内容更新](on-demand-content.md)
      + [内容即服务更新](content-update-as-a-service.md)
      + [使用Screens Launch更新内容](launches.md)
   + 用例示例{#use-case-examples}
      + [紧急渠道](emergency-channel.md)
      + [旅行中心温度激活](local-temperature-activation.md)
      + [酒店预订激活](hospitality-reservation-activation.md)
      + [零售库存目标激活](retail-inventory-activation.md)
      + [应用过渡](applying-transitions.md)
      + [多区域到单区域过渡](multizone-to-singlezone.md)
      + [单次使用TakeOver渠道](single-use-takeover-channel.md)
      + [永久使用TakeOver渠道](perpetual-takeover-channel.md)
+ 开发人员和API资源{#developing}
   + [REST API](rest-api.md)
   + [为AEM Screens开发自定义组件](developing-custom-component-tutorial-develop.md)
   + [离线渠道](offline-channels.md)
   + [扩展AEM Screens组件](extending-component-tutorial-develop.md)
   + [创建组件](creating-components.md)
   + [使用AEM SPA Editor嵌入REACT应用程序并与AEM Screens Analytics集成](embedding-react-app.md)
   + [在AEM Screens中配置ContextHub](configuring-context-hub.md)
   + [为多区域布局创建自定义模板](creating-custom-templates-multizone-layouts.md)
   + [为文本叠加图应用自定义品牌和样式](custom-branding-text-overlays.md)
   + [自适应演绎版：体系结构概述和配置](/help/user-guide/adaptive-renditions.md)
+ {#troubleshooting}疑难解答和常见问题解答
   + [AEM Screens常见问题解答](aem-screens-faqs.md)
   + [设备控制中心故障排除](monitoring-screens.md)
   + [视频播放配置](troubleshoot-videos.md)
+ 发行说明 {#release-notes}
   + [功能包202109的发行说明](release-notes-fp-202109.md)
   + [功能包202105的发行说明](release-notes-fp-202105.md)
   + [功能包202103的发行说明](release-notes-fp-202103.md)
   + [功能包202011的发行说明](release-notes-fp-202011.md)
   + [功能包202008的发行说明](release-notes-fp-202008.md)
   + [功能包202004的发行说明](release-notes-fp-202004.md)
   + [功能包202001的发行说明](release-notes-fp-202001.md)
   + [功能包201909的发行说明](release-notes-fp-201909.md)
   + [功能包201907的发行说明](release-notes-fp-201907.md)
   + [功能包201905的发行说明](screens-release-notes-fp-201905.md)
   + [功能包201812的发行说明](release-notes-fp-201812.md)
   + [功能包201809的发行说明](screens-release-notes.md)
