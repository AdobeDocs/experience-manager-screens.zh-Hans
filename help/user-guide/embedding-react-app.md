---
title: 使用AEM SPA编辑器嵌入REACT应用程序并与AEM Screens分析集成
seo-title: 使用AEM SPA编辑器嵌入REACT应用程序并与AEM Screens分析集成
description: 可查看本页以了解如何使用AEM SPA编辑器（可由AEM中的商业人士配置）嵌入使用REACT（或Angular）的交互式单页应用程序，以及如何将交互式应用程序与脱机Adobe Analytics集成。
seo-description: 可查看本页以了解如何使用AEM SPA编辑器（可由AEM中的商业人士配置）嵌入使用REACT（或Angular）的交互式单页应用程序，以及如何将交互式应用程序与脱机Adobe Analytics集成。
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 使用AEM SPA编辑器嵌入REACT应用程序并与AEM Screens分析集成 {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

本节介绍如何使用AEM SPA编辑器嵌入使用REACT（或Angular）的交互式单页应用程序，该编辑器可由商业人士在AEM中配置，以及如何将交互式应用程序与脱机Adobe Analytics集成。

## 使用AEM SPA Editor {#using-the-aem-spa-editor}

请按照以下步骤使用AEM SPA编辑器：

1. 克隆位于https://github.com/adobe/aem-spa-project-archetype的AEM SPA Editor回 [购库。](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >此原型创建了最小的Adobe Experience manager项目，作为您自己的SPA项目的起点。 使用此原型时必须提供的属性允许根据需要命名此项目的所有部分。

1. 按照自述文件说明创建AEM SPA编辑器原型项目：

   ```
   mvn clean install archetype:update-local-catalog
   mvn archetype:crawl
   
   mvn archetype:generate \
   -DarchetypeCatalog=internal \
   -DarchetypeGroupId=com.adobe.cq.spa.archetypes \
   -DarchetypeArtifactId=aem-spa-project-archetype \
   -DarchetypeVersion=1.0.3-SNAPSHOT \
   ```

   >[!NOTE]
   >
   >我们将 **GroupId用作** com.adobe.aem.screens ***，将*** GroupId用作 **My Martifact(默认值为******** Artifact)范例。 您可以根据需要选择自己的。

1. 创建项目后，请使用您选择的IDE或编辑器并导入生成的Maven项目。
1. 使用命令mvn clean install -PautoInstallPackage部署 ***到本地AEM实例***。

### 在REACT应用程序中编辑内容 {#editing-content-in-the-react-app}

要编辑REACT应用程序中的内容，请执行以下操作：

1. 导航到 `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` （如果适用，请替换主机名、端口和项目名称）。
1. 您应该能够编辑在Hello world应用程序中显示的文本。

### 将交互式REACT应用程序添加到AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

请按照以下步骤将交互式REACT应用程序添加到AEM Screens:

1. 创建新的AEM Screens项目。 有关更多 [详细信息，请参阅创建和管理项](creating-a-screens-project.md) 目。

   >[!NOTE]
   >
   >在Screens项 **目的Channels文件夹中创建渠道时，** 创建序列渠 **道** 。
   >
   >
   >有关更多 [详细信息，请参阅创建和管理渠道](managing-channels.md) 。

   ![screen_shot_2019-02-15at100330am](assets/screen_shot_2019-02-15at100330am.png)

1. 编辑任何序列渠道并拖放嵌入的页面组件。

   有关更多 [详细信息，请参阅将组件添加到渠道](adding-components-to-a-channel.md) 。

   >[!NOTE]
   >
   >确保在将渠道分配给显示屏时添加用户交互事件。

1. 单 **击操作栏** 中的编辑以编辑序列渠道的属性。

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. 拖放嵌入式 **页面组件** ，然后选择mysamplespa应用程序下的主页，例如 ***/content/mysamplespa/en/home***。

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. 针对此项目注册播放器，您现在应能看到交互式应用程序在AEM Screens上运行。

   请参阅 [设备注册](device-registration.md) ，详细了解设备注册。

## 通过AEM Screens将SPA与Adobe Analytics与脱机功能集成 {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

按照以下步骤，通过AEM Screens将SPA与Adobe Analytics集成，并具备脱机功能：

1. 在AEM Screens中配置Adobe Analytics。

   请参阅[使用AEM Screens配置Adobe Analytics(configuring-adobe-analytics-aem-screens.md))，了解如何在Adobe Analytics中使用AEM Screens执行排序，以及使用脱机Adobe Analytics发送自定义事件。

1. 在您选择的IDE/编辑器中编辑您的反应应用程序（尤其是文本组件或要开始发出事件的其他组件）。
1. 在要为组件捕获的单击事件或其他事件上，使用标准数据模型添加分析信息。

   有关更多 [详细信息，请参](configuring-adobe-analytics-aem-screens.md)阅配置Adobe Analytics与AEM屏幕。

1. 调用AEM Screens Analytics API以脱机保存活动并将其连发发送到Adobe Analytics。

   例如，

   ```
   handleClick() {
       if ((window.parent) && (window.parent.CQ) && (window.parent.CQ.screens) && (window.parent.CQ.screens.analytics))
       {
           var analyticsEvent = {};
           analyticsEvent['event.type'] = 'play'; // Type of event
    analyticsEvent['event.coll_dts'] = new Date().toISOString(); // Start of collecting the event
    analyticsEvent['event.dts_start'] = new Date().toISOString(); // Event start
    analyticsEvent['content.type'] = 'Washing machine'; // Mime Type or product category
    analyticsEvent['content.action'] = 'Path to the washing machine asset in AEM'; // Path in AEM to relevant asset
    analyticsEvent['trn.product'] = 'Washing machine Model number'; // Product being explored
    analyticsEvent['trn.amount'] = 1000; // Product pricing or other numeric value or weight
    analyticsEvent['event.dts_end'] = new Date().toISOString(); // Event end
    analyticsEvent['event.count'] = 100; // Numeric value that may count a number of clicks or keystrokes or wait time in seconds for example
    analyticsEvent['event.value'] = 'My favorite analytics event';
           analyticsEvent['trn.quantity'] = 10; // Quantity of product selection
    analyticsEvent['event.subtype'] = 'end'; // Event subtype if applicable
    window.parent.CQ.screens.analytics.sendTrackingEvent(analyticsEvent);
       }
   }
   ```

   >[!NOTE]
   >
   >播放器固件会自动向您发送的自定义分析数据中添加有关播放器及其运行时环境的更多详细信息。 因此，除非绝对必要，否则您可能无需捕获低级操作系统／设备详细信息。 您只需关注业务分析数据。

