---
title: 创建组件
seo-title: 创建组件
description: AEM组件用于保存、格式化和呈现网页上提供的内容。 可查看本页以了解有关创作渠道和渲染组件的信息。
seo-description: AEM组件用于保存、格式化和呈现网页上提供的内容。 可查看本页以了解有关创作渠道和渲染组件的信息。
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 创建组件 {#creating-components}

AEM组件用于保存、格式化和呈现网页上提供的内容。

>[!NOTE]
>
>要了解有关创建AEM组件的详细信息，请参阅开发AEM组件。

## 创作渠道 {#authoring-channels}

渠道是交付到一组显示屏的内容的中心对象。 因此，内容作者通常会在编辑器中打开渠道以添加或修改内容。 由于渠道是 ***cq:Page*** ，因此它将遵循相同的传统UX模式在渠道上添加和更改组件。

但是，由于渠道中的组件通常呈现为全屏，因此在尝试编辑单个组件或编写新订单时，创作体验会受到影响。 因此，该渠道将依赖选择器来呈现组件的不同视图。 创作环境将利用编辑选择器激活自定义渠道渲染。

For example, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

在编辑时，用户不必在URL中添加选择器。 客户端逻辑正在侦听层交换机事件，并在信道具有专用资源类型 *screens/core/components/channel时添加选择器。*

## 渲染组件 {#rendering-components}

要启用正确的创作，组件需要提供以下两个渲染：

| **组件** | **演绎版** |
|---|---|
| *my-component/my-component.html* | 生产渲染 |
| *my-component/edit.html* | 在较小的视图中编辑渲染 |

内置组件利用以下客户端库类别：

| **组件** | **客户端库** |
|---|---|
| *cq.screens.components.edit* | CSS和JS，必须在创作过程中加载 |
| *cq.screens.components.production* | CSS和JS，必须在渠道运行时加载 |
| *cq.screens.components* | 共享CSS和JS |

>[!NOTE]
>
>要开发自定义组件，请使用*** [AEM Screens示例组件模板](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***。
