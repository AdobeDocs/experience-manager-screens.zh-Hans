---
title: 创建组件
seo-title: Creating Components
description: AEM组件用于保留、格式化和渲染网页上可用的内容。 请按照本页面了解如何创作渠道和渲染组件。
seo-description: AEM components are used to hold, format, and render the content made available on your webpages. Follow this page to learn about authoring channels and rendering components.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 3%

---

# 创建组件 {#creating-components}

AEM组件用于保留、格式化和渲染网页上可用的内容。

>[!NOTE]
>
>要了解创建AEM组件的详细信息，请参阅开发AEM组件。

## 创作渠道 {#authoring-channels}

渠道是交付给一组显示器的内容的中心对象。 因此，内容作者通常会在编辑器中打开一个渠道来添加或修改内容。 由于渠道是 ***cq：Page*** 它将遵循与传统UX相同的模式，在渠道中添加和更改组件。

但是，由于渠道中的组件通常会在全屏模式下呈现，因此，在尝试编辑单个组件或撰写新订单时，创作体验会受到影响。 因此，渠道将依赖选择器呈现组件的不同视图。 创作环境将利用编辑选择器激活自定义渠道渲染。

例如，`http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

编辑时，用户无需将选择器添加到URL。 客户端逻辑正在侦听层切换事件，并在通道具有专用资源类型时添加选择器 *screens/core/components/channel.*

## 渲染组件 {#rendering-components}

要启用正确创作，组件需要提供以下两种渲染：

| **Component** | **演绎版** |
|---|---|
| *my-component/my-component.html* | 生产渲染 |
| *my-component/edit.html* | 在较小的视图中编辑渲染 |

内置组件利用以下客户端库类别：

| **Component** | **客户端库** |
|---|---|
| *cq.screens.components.edit* | 创作期间必须加载的CSS和JS |
| *cq.screens.components.production* | 渠道运行时必须加载的CSS和JS |
| *cq.screens.components* | 共享CSS和JS |

>[!NOTE]
>
>要开发自定义组件，请使用***[AEM Screens示例组件模板](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***。
