---
cloud: experience-cloud
product: experience manager
audience: end-user
user-guide-title: Adobe Experience Manager Screens 帮助
user-guide-description: 了解如何使用 AEM Screens 发布涉及不同屏幕类型的交互式数字体验。
translation-type: tm+mt
source-git-commit: 7ce10b467559b33c5d3ca61b315e50cb1ceade9d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 18%

---


# AEM Screens 用户指南 {#user-guide}

+ [屏幕简介](aem-screens-introduction.md)
+ 概述和引题入门指南 {#overview}
   + [踢球指南](kickstart-for-aem-screens.md)
   + [Screens最佳实践指南](https://docs.adobe.com/content/help/zh-Hans/experience-manager-screens/using/about-guide.html)
   + [主要条款](screens-glossary.md)
+ 数字标牌网络基础知识 {#digital-signage-network}
   + [第1部分：项目角色和责任](project-roles-responsibilities.md)
   + [第2部分：项目范围时的注意事项](project-considerations.md)
   + [第3部分：测试、POC、试点和推广](testing-pocs-pilots-rollouts.md)
   + [第4部分：项目管理和部署](project-management-and-deployment.md)
   + [第5部分：支持注意事项](support-considerations.md)
+ 配置和管理 {#administering}
   + [Screens服务器配置](configuring-screens-introduction.md)
   + [设置调度程序配置](dispatcher-configurations-aem-screens.md)
   + [安装Screens播放器](installing-screens-player.md)
   + [连接Screens播放器](working-with-screens-player.md)
   + [设备注册](device-registration.md)
   + [设置ACL](setting-up-acls.md)
   + [AEM Screens安全清单](security-checklist.md)
   + [从ContentSync过渡到SmartSync](smartsync.md)
   + [从文件新建项目导入程序](project-importer.md)
   + [将数据触发器复制到发布服务器](replicating-data-triggers.md)
   + 客户端特定注意事项 {#installing-client}
      + [Chrome OS Player](implementing-chrome-os-player.md)
      + [将Chrome Player用作故障诊断的扩展](using-chrome-player-as-an-extension.md)
      + [Android Player](implementing-android-player.md)
      + [Windows Player](implementing-windows-player.md)
   + Author Publish {#author-publish}
      + [作者——发布架构概述](author-publish-architecture-overview.md)
      + [配置作者和发布](author-and-publish.md)
   + Analytics与AEM Screens {#analytics-integration}
      + [Adobe Analytics集成](adobe-analytics-integration-aem-screens.md)
      + [配置Adobe Analytics与AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ 创作和用例示例 {#authoring}
   + 设置Screens项目 {#setting-up-projects}
      + [创建和管理项目](creating-a-screens-project.md)
      + [创建和管理渠道](managing-channels.md)
      + [创建和管理显示屏](managing-displays.md)
      + [创建和管理位置](managing-locations.md)
      + [创建和管理计划](managing-schedules.md)
      + [管理设备](managing-devices.md)
      + 分配渠道 {#assigning-channels}
         + [渠道分配](channel-assignment-latest-fp.md)
         + [渠道分配：旧AEM Screens功能包](channel-assignment.md)
   + 使用核心产品功能 {#product-features}
      + [文本覆盖](text-overlay.md)
      + [批量脱机更新](bulk-offline-update.md)
      + [AEM Screens通知服务](screens-notifications-service.md)
      + [使用体验片段](experience-fragments-in-screens.md)
      + [资产级别激活](asset-level-scheduling.md)
      + [渠道级别激活](channel-level-activation.md)
      + [创建和管理Live Copy](managing-livecopy.md)
      + [创建视频填充工作流](creating-a-video-padding-workflow.md)
      + [向渠道添加组件](adding-components-to-a-channel.md)
      + [嵌入式序列](embedded-sequences.md)
      + [多区域布局](multi-zone-layout-aem-screens.md)
      + [视频演绎版](generating-renditions.md)
      + [动态嵌入式序列](dynamic-embedded-sequences.md)
      + [渠道级批量图像播放持续时间](channel-level-image-playback.md)
      + [命令同步](using-command-sync.md)
      + [使用数据触发器进行创作](authoring-data-triggers.md)
      + [语音识别](voice-recognition.md)
   + 管理内容更新 {#content-updates}
      + [点播内容更新](on-demand-content.md)
      + [内容即服务更新](content-update-as-a-service.md)
      + [使用Screens启动进行内容更新](launches.md)
   + 用例示例 {#use-case-examples}
      + [紧急渠道](emergency-channel.md)
      + [旅行中心温度激活](local-temperature-activation.md)
      + [酒店预订激活](hospitality-reservation-activation.md)
      + [零售库存目标激活](retail-inventory-activation.md)
      + [应用过渡](applying-transitions.md)
      + [多区域到单区域过渡](multizone-to-singlezone.md)
      + [一次性使用接管渠道](single-use-takeover-channel.md)
      + [永久使用接管渠道](perpetual-takeover-channel.md)
+ 开发人员和API资源 {#developing}
   + [REST API](rest-api.md)
   + [为AEM Screens开发自定义组件](developing-custom-component-tutorial-develop.md)
   + [脱机渠道](offline-channels.md)
   + [扩展AEM Screens组件](extending-component-tutorial-develop.md)
   + [创建组件](creating-components.md)
   + [使用AEM SPA编辑器嵌入REACT应用程序并与AEM Screens分析集成](embedding-react-app.md)
   + [在AEM Screens配置ContextHub](configuring-context-hub.md)
   + [为多区域布局创建自定义模板](creating-custom-templates-multizone-layouts.md)
   + [对文本叠加应用自定义品牌和样式](custom-branding-text-overlays.md)
+ 疑难解答和常见问题解答 {#troubleshooting}
   + [AEM Screens常见问题解答](aem-screens-faqs.md)
   + [设备控制中心故障排除](monitoring-screens.md)
   + [视频播放配置](troubleshoot-videos.md)
+ 发行说明 {#release-notes}
   + [功能包202008发行说明](release-notes-fp-202008.md)
   + [功能包202004发行说明](release-notes-fp-202004.md)
   + [功能包202001发行说明](release-notes-fp-202001.md)
   + [功能包201909发行说明](release-notes-fp-201909.md)
   + [功能包201907发行说明](release-notes-fp-201907.md)
   + [功能包201905发行说明](screens-release-notes-fp-201905.md)
   + [功能包201812发行说明](release-notes-fp-201812.md)
   + [功能包201809发行说明](screens-release-notes.md)
