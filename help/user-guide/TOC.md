---
cloud: Experience Cloud
product: experience manager
audience: end-user
user-guide-title: Adobe Experience Manager Screens 帮助
breadcrumb-title: AEM Screens 指南
user-guide-description: 了解如何使用数字标牌解决方案，让您发布动态的交互式数字体验与交互内容。
feature-set: Experience Manager Screens
feature: Content
role: User
source-git-commit: d8392b015c65e6bba35ba4c923d4f663e1121e0c
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 11%

---


# AEM Screens用户指南 {#user-guide}

+ [Screens简介](aem-screens-introduction.md)
+ 概述和Kickstart指南{#overview}
   + [Kickstart指南](kickstart-for-aem-screens.md)
   + [Screens最佳实践指南](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-screens/using/about-guide)
   + [关键术语](screens-glossary.md)
   + [Screens术语和概念](screens-concepts-feature-video-understand.md)
+ 数字标牌网络基础知识{#digital-signage-network}
   + [第1部分：项目角色和职责](project-roles-responsibilities.md)
   + [第2部分：关于项目适用范围的注意事项](project-considerations.md)
   + [第3部分：测试、概念验证、试点和推广](testing-pocs-pilots-rollouts.md)
   + [第4部分：项目管理和部署](project-management-and-deployment.md)
   + [第5部分：支持注意事项](support-considerations.md)
+ 配置和管理{#administering}
   + [配置Screens服务器](configuring-screens-introduction.md)
   + [设置Dispatcher配置](dispatcher-configurations-aem-screens.md)
   + [安装 Screens 播放器](installing-screens-player.md)
   + [连接Screens Player](working-with-screens-player.md)
   + [设备注册](device-registration.md)
   + [设置ACL](setting-up-acls.md)
   + [AEM Screens安全核对清单](security-checklist.md)
   + [从ContentSync转换为SmartSync](smartsync.md)
   + [从文件新建项目导入程序](project-importer.md)
   + [将数据触发器复制到发布服务器](replicating-data-triggers.md)
   + [在Screens上配置复制代理](configure-screens-replication.md)
   + 特定于客户端的注意事项{#installing-client}
      + [Chrome操作系统播放器](implementing-chrome-os-player.md)
      + [使用Chrome Player作为扩展进行故障排除](using-chrome-player-as-an-extension.md)
      + [Android](implementing-android-player.md)
      + [Windows Player](implementing-windows-player.md)
      + [Tizen Player](tizen-player.md)
      + [云播放器](implementing-cloud-player.md)
      + [播放器自动注册](auto-registration-players.md)
      + [使用遥控器](implementing-remote-control.md)
   + 作者发布{#author-publish}
      + [Author-Publish架构概述](author-publish-architecture-overview.md)
      + [配置作者和发布](author-and-publish.md)
   + Analytics与AEM Screens的集成{#analytics-integration}
      + [Adobe Analytics 集成](adobe-analytics-integration-aem-screens.md)
      + [使用AEM Screens配置Adobe Analytics](configuring-adobe-analytics-aem-screens.md)
+ 创作和使用案例示例{#authoring}
   + 设置Screens项目{#setting-up-projects}
      + [创建和管理项目](creating-a-screens-project.md)
      + [创建和管理渠道](managing-channels.md)
      + [创建和管理显示区](managing-displays.md)
      + [创建和管理位置](managing-locations.md)
      + [创建和管理时间表](managing-schedules.md)
      + [管理设备](managing-devices.md)
      + 正在分配渠道{#assigning-channels}
         + [渠道分配](channel-assignment-latest-fp.md)
         + [渠道分配：旧版AEM Screens功能包](channel-assignment.md)
   + 使用核心产品功能{#product-features}
      + [文本覆盖](text-overlay.md)
      + [批量脱机更新](bulk-offline-update.md)
      + [AEM Screens通知服务](screens-notifications-service.md)
      + [使用体验片段](experience-fragments-in-screens.md)
      + [资产级别激活](asset-level-scheduling.md)
      + [渠道级别激活](channel-level-activation.md)
      + [创建和管理Live Copy](managing-livecopy.md)
      + [创建视频填充工作流](creating-a-video-padding-workflow.md)
      + [将组件添加到渠道](adding-components-to-a-channel.md)
      + [嵌入式序列](embedded-sequences.md)
      + [多区域布局](multi-zone-layout-aem-screens.md)
      + [视频演绎版](generating-renditions.md)
      + [动态嵌入式序列](dynamic-embedded-sequences.md)
      + [渠道级别的批量图像播放持续时间](channel-level-image-playback.md)
      + [命令同步](using-command-sync.md)
      + [使用Data Triggers创作](authoring-data-triggers.md)
      + [使用标记](tagging.md)
      + [语音识别](voice-recognition.md)
      + [内容分配报告](content-assignment-report.md)
      + [视频支持缩略图](thumbnail-support.md)
      + [在AEM Screens中使用自适应演绎版](using-adaptive-renditions.md)
   + 管理内容更新{#content-updates}
      + [按需内容更新](on-demand-content.md)
      + [内容即服务更新](content-update-as-a-service.md)
      + [使用Screens Launch更新内容](launches.md)
   + 用例示例{#use-case-examples}
      + [紧急渠道](emergency-channel.md)
      + [行程中心温度激活](local-temperature-activation.md)
      + [Hospitality Reservation Activation](hospitality-reservation-activation.md)
      + [零售库存目标激活](retail-inventory-activation.md)
      + [应用过渡](applying-transitions.md)
      + [多区域到单区域转换](multizone-to-singlezone.md)
      + [一次性接管渠道](single-use-takeover-channel.md)
      + [永久使用接管渠道](perpetual-takeover-channel.md)
+ 开发人员和API资源{#developing}
   + [REST API](rest-api.md)
   + [为AEM Screens开发自定义组件](developing-custom-component-tutorial-develop.md)
   + [脱机渠道](offline-channels.md)
   + [扩展AEM Screens组件](extending-component-tutorial-develop.md)
   + [创建组件](creating-components.md)
   + [使用AEM SPA Editor嵌入REACT应用程序并与AEM Screens Analytics集成](embedding-react-app.md)
   + [在AEM Screens中配置ContextHub](configuring-context-hub.md)
   + [为MultiZone布局创建自定义模板](creating-custom-templates-multizone-layouts.md)
   + [为文本叠加应用自定义品牌和样式](custom-branding-text-overlays.md)
   + [自适应演绎版：架构概述和配置](/help/user-guide/adaptive-renditions.md)
+ 疑难解答和常见问题解答{#troubleshooting}
   + [AEM Screens常见问题解答](aem-screens-faqs.md)
   + [设备控制中心故障排除](monitoring-screens.md)
   + [视频播放配置](troubleshoot-videos.md)
+ 发行说明 {#release-notes}
   + [功能包20250327发行说明](release-notes-fp-20250327.md)
   + [功能包20250224发行说明](release-notes-fp-20250224.md)
   + [功能包20240715发行说明](release-notes-fp-20240715.md)
   + [功能包202401发行说明](release-notes-fp-20250215.md)
   + [功能包202401发行说明](release-notes-fp-202401.md)
   + [功能包20240116发行说明](release-notes-fp-20240116.md)
   + [功能包20240215发行说明](release-notes-fp-20240215.md)
   + [功能包202204发行说明](release-notes-fp-202204.md)
   + [功能包202203发行说明](release-notes-fp-202203.md)
   + [功能包202112发行说明](release-notes-fp-202112.md)
   + [功能包202109的发行说明](release-notes-fp-202109.md)
   + [功能包202105发行说明](release-notes-fp-202105.md)
   + [功能包202103发行说明](release-notes-fp-202103.md)
   + [功能包202011发行说明](release-notes-fp-202011.md)
   + [功能包202008发行说明](release-notes-fp-202008.md)
   + [功能包202004发行说明](release-notes-fp-202004.md)
   + [功能包202001发行说明](release-notes-fp-202001.md)
   + [功能包201909发行说明](release-notes-fp-201909.md)
   + [功能包201907发行说明](release-notes-fp-201907.md)
   + [功能包201905发行说明](screens-release-notes-fp-201905.md)
   + [功能包201812发行说明](release-notes-fp-201812.md)
   + [功能包201809发行说明](screens-release-notes.md)
