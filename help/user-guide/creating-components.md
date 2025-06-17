---
title: 创建组件
description: 了解如何使用AEM组件来保存、格式化和呈现您的网页上可用的内容。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 1%

---

# 创建组件 {#creating-components}

AEM组件用于保留、格式化和呈现网页上可用的内容。

>[!NOTE]
>
>要了解创建AEM组件的详细信息，请参阅开发AEM组件。

## 创作渠道 {#authoring-channels}

渠道是交付给一组显示器的内容的中心对象。 因此，内容作者通常会在编辑器中打开一个渠道来添加或修改内容。 由于该渠道是***`cq:Page`***，因此它遵循相同的传统UX模式在该渠道上添加和更改组件。

但是，由于渠道中的组件通常以全屏方式呈现，因此在尝试编辑单个组件或撰写新订单时，创作体验会受损。 因此，渠道依赖选择器来呈现组件的不同视图。 创作环境使用`edit`选择器激活自定义渠道渲染。

例如，`http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

编辑时，用户无需将选择器添加到URL。 客户端逻辑正在侦听层切换事件，如果通道具有专用资源类型&#x200B;*screens/core/components/channel*，则添加选择器。

## 渲染组件 {#rendering-components}

要启用正确创作，组件必须提供以下两种渲染：

| **Component** | **演绎版** |
|---|---|
| *my-component/my-component.html* | 生产渲染 |
| *my-component/edit.html* | 在较小的视图中编辑渲染 |

内置组件使用以下客户端库类别：

| **Component** | **客户端库** |
|---|---|
| *cq.screens.components.edit* | 创作期间必须加载的CSS和JS |
| *cq.screens.components.production* | 渠道运行时必须加载的CSS和JS |
| *cq.screens.components* | 共享的CSS和JS |

>[!NOTE]
>
>要开发自定义组件，请使用***[AEM Screens示例组件模板](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***。
