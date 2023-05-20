---
cloud: experience-cloud
product: experience manager
audience: end-user
user-guide-title: Adobe Experience Manager Screens 帮助
breadcrumb-title: AEM Screens 指南
user-guide-description: 了解如何使用这款数字标牌解决方案，发布动态的交互式数字体验与交互内容。
feature-set: Experience Manager Screens
source-git-commit: 9d8b336c12d5e44beb831ba41f3df5031a6ca32d
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 14%

---


# AEM Screens 用户指南 {#user-guide}

+ [Screens簡介](aem-screens-introduction.md)
+ 概覽和Kickstart指南 {#overview}
   + [Kickstart指南](kickstart-for-aem-screens.md)
   + [Screens最佳作法指南](https://experienceleague.adobe.com/docs/experience-manager-screens/using/about-guide.html)
   + [重要條款](screens-glossary.md)
+ 數位看板網路基本需知 {#digital-signage-network}
   + [第1部分：專案角色與職責](project-roles-responsibilities.md)
   + [第2部分：設定範圍專案的考量事項](project-considerations.md)
   + [第3部分：測試、POC、試行方案和推出](testing-pocs-pilots-rollouts.md)
   + [第4部分：專案管理與部署](project-management-and-deployment.md)
   + [第5部分：支援考量事項](support-considerations.md)
+ 設定和管理 {#administering}
   + [Screens伺服器設定](configuring-screens-introduction.md)
   + [設定Dispatcher設定](dispatcher-configurations-aem-screens.md)
   + [安装 Screens 播放器](installing-screens-player.md)
   + [連線Screens播放器](working-with-screens-player.md)
   + [设备注册](device-registration.md)
   + [設定ACL](setting-up-acls.md)
   + [AEM Screens安全性檢查清單](security-checklist.md)
   + [從ContentSync轉換為SmartSync](smartsync.md)
   + [從檔案新增專案匯入工具](project-importer.md)
   + [將資料觸發程式複製到發佈伺服器](replicating-data-triggers.md)
   + [設定Screens復寫代理](configure-screens-replication.md)
   + 使用者端特定考量事項 {#installing-client}
      + [Chrome作業系統播放器](implementing-chrome-os-player.md)
      + [使用Chrome播放器作為疑難排解的擴充功能](using-chrome-player-as-an-extension.md)
      + [Android Player](implementing-android-player.md)
      + [Windows Player](implementing-windows-player.md)
      + [Tizen Player](tizen-player.md)
      + [自動註冊播放器](auto-registration-players.md)
      + [使用遠端控制項](implementing-remote-control.md)
   + 作者發佈 {#author-publish}
      + [Author-Publish架構概述](author-publish-architecture-overview.md)
      + [設定作者和發佈](author-and-publish.md)
   + Analytics與AEM Screens的整合 {#analytics-integration}
      + [Adobe Analytics 集成](adobe-analytics-integration-aem-screens.md)
      + [使用AEM Screens設定Adobe Analytics](configuring-adobe-analytics-aem-screens.md)
+ 製作和使用案例範例 {#authoring}
   + 設定畫面專案 {#setting-up-projects}
      + [建立和管理專案](creating-a-screens-project.md)
      + [建立和管理管道](managing-channels.md)
      + [建立和管理顯示區](managing-displays.md)
      + [建立和管理位置](managing-locations.md)
      + [建立和管理排程](managing-schedules.md)
      + [管理裝置](managing-devices.md)
      + 指派管道 {#assigning-channels}
         + [渠道分配](channel-assignment-latest-fp.md)
         + [管道指派：舊版AEM Screens Feature Pack](channel-assignment.md)
   + 使用核心产品功能{#product-features}
      + [文本覆盖](text-overlay.md)
      + [大量離線更新](bulk-offline-update.md)
      + [AEM Screens通知服務](screens-notifications-service.md)
      + [使用体验片段](experience-fragments-in-screens.md)
      + [資產層級啟用](asset-level-scheduling.md)
      + [頻道層級啟用](channel-level-activation.md)
      + [建立和管理即時副本](managing-livecopy.md)
      + [建立視訊邊框間距工作流程](creating-a-video-padding-workflow.md)
      + [新增元件至管道](adding-components-to-a-channel.md)
      + [內嵌順序](embedded-sequences.md)
      + [多區域配置](multi-zone-layout-aem-screens.md)
      + [視訊轉譯](generating-renditions.md)
      + [动态嵌入式序列](dynamic-embedded-sequences.md)
      + [頻道層級大量影像播放持續時間](channel-level-image-playback.md)
      + [命令同步](using-command-sync.md)
      + [使用資料觸發器製作](authoring-data-triggers.md)
      + [語音辨識](voice-recognition.md)
      + [内容分配报告](content-assignment-report.md)
      + [视频的缩略图支持](thumbnail-support.md)
      + [在AEM Screens中使用最適化轉譯](using-adaptive-renditions.md)
   + 管理內容更新 {#content-updates}
      + [隨選內容更新](on-demand-content.md)
      + [內容即服務更新](content-update-as-a-service.md)
      + [使用Screens啟動的內容更新](launches.md)
   + 使用案例範例 {#use-case-examples}
      + [緊急通道](emergency-channel.md)
      + [旅行中心溫度啟用](local-temperature-activation.md)
      + [Hospality Reservation Activation](hospitality-reservation-activation.md)
      + [零售詳細目錄目標啟動](retail-inventory-activation.md)
      + [套用轉變](applying-transitions.md)
      + [多區域到單一區域轉換](multizone-to-singlezone.md)
      + [單次使用接管管道](single-use-takeover-channel.md)
      + [永久使用接管管道](perpetual-takeover-channel.md)
+ 開發人員和API資源 {#developing}
   + [REST API](rest-api.md)
   + [為AEM Screens開發自訂元件](developing-custom-component-tutorial-develop.md)
   + [離線頻道](offline-channels.md)
   + [延伸AEM Screens元件](extending-component-tutorial-develop.md)
   + [创建组件](creating-components.md)
   + [使用AEM SPA編輯器內嵌REACT應用程式並與AEM Screens Analytics整合](embedding-react-app.md)
   + [在AEM Screens中設定ContextHub](configuring-context-hub.md)
   + [建立MultiZone配置圖的自訂範本](creating-custom-templates-multizone-layouts.md)
   + [套用文字覆蓋圖的自訂品牌和樣式](custom-branding-text-overlays.md)
   + [最適化轉譯：架構概觀和設定](/help/user-guide/adaptive-renditions.md)
+ 疑難排解和常見問答( FAQ) {#troubleshooting}
   + [AEM Screens常見問題集](aem-screens-faqs.md)
   + [疑難排解裝置控制中心](monitoring-screens.md)
   + [視訊播放設定](troubleshoot-videos.md)
+ 发行说明 {#release-notes}
   + [Feature Pack 202204發行說明](release-notes-fp-202204.md)
   + [Feature Pack 202203發行說明](release-notes-fp-202203.md)
   + [Feature Pack 202112發行說明](release-notes-fp-202112.md)
   + [Feature Pack 202109發行說明](release-notes-fp-202109.md)
   + [Feature Pack 202105發行說明](release-notes-fp-202105.md)
   + [Feature Pack 202103發行說明](release-notes-fp-202103.md)
   + [Feature Pack 202011發行說明](release-notes-fp-202011.md)
   + [Feature Pack 202008發行說明](release-notes-fp-202008.md)
   + [Feature Pack 202004發行說明](release-notes-fp-202004.md)
   + [Feature Pack 202001發行說明](release-notes-fp-202001.md)
   + [Feature Pack 201909發行說明](release-notes-fp-201909.md)
   + [Feature Pack 201907發行說明](release-notes-fp-201907.md)
   + [Feature Pack 201905發行說明](screens-release-notes-fp-201905.md)
   + [Feature Pack 201812發行說明](release-notes-fp-201812.md)
   + [Feature Pack 201809發行說明](screens-release-notes.md)
