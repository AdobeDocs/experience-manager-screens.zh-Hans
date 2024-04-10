---
title: 在多区域布局中创建自定义模板
description: 了解如何在MultiZone布局中为AEM Screens创建自定义模板。
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: c142830a37461a36baae15f543bd43b0ae8a62a7
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 1%

---

# 为MultiZone布局创建自定义模板 {#creating-custom-templates-multizone}

本页展示如何为多区域布局创建自定义模板。

## 重要注意事项 {#considerations}

在多区域布局中创建自定义模板之前，必须注意两个重要注意事项：

1. **固定像素大小或百分比**：

   决定是为自定义布局的不同区域使用固定像素大小，还是要使用百分比创建自定义布局。

   >[!NOTE]
   >使用百分比为您的自定义布局设置区域的好处允许您在各种屏幕大小上重复使用该模板。

1. **命名约定**：

   在了解如何创建要在AEM Screens项目中使用的自定义多区域模板之前，请了解您要创建的模板的语言。

   | **布局名称** | **描述** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | 三区域横向布局允许您创建三个区域：<br>*区域1为水平屏幕和垂直屏幕左侧的20%<br>*区域2为水平屏幕的80%和垂直屏幕的20%右对齐<br>*区域3为水平屏幕100%，垂直屏幕80%，长宽比为16:9 |
   | `Upper20-PortraitHD2Zone` | 双区纵向模板，从上到下占屏面的20%，长宽比为16:9 |
   | `Right20-LandscapeSD3Zone` | 一个三区模板，从右侧覆盖20%的屏幕，长宽比为4:3 |

   >[!IMPORTANT]
   >在自定义布局中定义的区域可能与整个布局的整体纵横比不匹配。 本文档中遵循的命名惯例指定自定义布局整体的长宽比。

## 示例用例 `Left20-LandscapeHD3Zone` 布局 {#custom-template-one}

请按照以下部分创建自定义模板 *`Left20-LandscapeHD3Zone`* 配置：

* **`Left20`**  — 左侧的顶部区域占水平屏幕和垂直屏幕大小的20%。
* **`Landscape`**  — 屏幕方向。
* **`HD`**  — 长宽比为16:9。
* **`3Zone`**  — 三个显示区域。

## 多区域布局的可视化表示形式 {#multi-layout-visual-one}

此 `Left20-LandscapeHD3Zone` 布局允许您在项目中创建以下多区域布局：

![图像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## 创建 `Left20-LandscapeHD3Zone` 布局 {#landscape-layout-one}

请按照以下步骤创建 `Left20-LandscapeHD3Zone` AEM Screens项目布局。

1. AEM Screens创建标题为 **`customtemplate`**.

   ![图像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 导航到 **CRXDE Lite** 通过您的AEM实例>工具> **CRXDE Lite**.

1. 在下创建文件夹 **应用程序** 标题为 **`customtemplate`**. 同样，创建另一个名为 **模板** 下 **`customtemplate`**，如下图所示。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >选择 **全部保存** 创建、编辑内容或将内容复制到任意CRXDE Lite时，都会从节点中的操作栏中复制内容。 否则，您无法提交更新。

1. 从以下位置复制左栏模板 `/libs/screens/core/templates/splitscreenchannel/lbar-left` 到 `/apps/customtemplate/template`.

1. 重命名复制的 **左边栏** (`/apps/customtemplate/template`)到 **my-custom-layout**.
   ![图像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 导航到 `/apps/customtemplate/template/my-custom-layout` 并更新属性 **`jcr:description`** 到 *模板`Left20-LandscapeHD3Zone`* 和 **`jcr:title`** 到 *`Left20-LandscapeHD3Zone`*.

   ![图像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 导航至 **`offline-config`** 节点来源 `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` 并更新 **`jcr:title`** 到 *`Left20-LandscapeHD3Zone`*.

   ![图像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 导航至 *`jcr:content`* 属性 **my-custom-template** 从 `/apps/customtemplate/template/my-custom-layout/jcr:content` 并更新 **`cq:cssClass`** 属性，以便您使用 **aem-Layout my-custom-layout**.

   ![图像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 参照复制左侧lbar模板的步骤(4)，您可以在下面查看三个响应式网格 `my-custom-layout/jcr:content`. 将自定义css类添加到中的每个响应式网格 *`cq:cssClass`* 属性，例如， *my-custom-layout — 左上方* 对象 *r1c1* 节点。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同样，添加 *my-custom-layout — 右上方* 对象 *r1c2*  和， *my-custom-layout — 底部* 对象 *r2c1* 节点。

   >[!NOTE]
   >这些自定义类在css中用于设置这些响应式网格的宽度/高度。

   >[!NOTE]
   >您可以根据所需的网格总数添加或删除响应式网格。 在此示例中，第一行中的两个网格和第二行中的一个网格被显示，因此总共有三个响应式网格(r1c1、r1c2、r2c1)。

1. 复制 `/libs/settings/wcm/designs/screens` 到 `/apps/settings/wcm/designs/` 并将复制的设计重命名为 **custom-template-designs**.

1. 导航到 `/apps/settings/wcm/designs/custom-template-designs` 并更新属性 *`jcr:title`* 之 **custom-template-designs** 到 **customtemplate-design**.

1. 导航到 `/apps/settings/wcm/designs/custom-template-designs` 并创建文件static.css。

1. 将内容复制到 `static.css` 文件：

   ```shell
       /*my-custom-layout styles*/
      .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-left {
       width:20%;
       height: 36%;
      float: left !important;
      }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-right {
      width:80%;
      height: 36%;
     float: left !important;
     }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--bottom {
     width:100%;
     height: 64%;
     }
   ```

   >[!NOTE]
   >您可以更新百分比以符合自定义模板的要求。

1. 导航到 `/apps/<project>/templates/my-custom-layout/jcr:content` 并更新属性 *`cq:designPath`* 到 `/apps/settings/wcm/designs/customtemplate-designs` 以便加载在static.css中配置的样式。

   >[!NOTE]
   >键入所有样式，而不是复制或粘贴，因为这样可能会导致空格导致css样式问题。

## 查看结果 {#viewing-result}

请按照以下步骤在您的AEM Screens项目中使用上述自定义模板：

1. 导航到您在步骤(1)中创建的Screens项目，然后选择 **渠道** 文件夹。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 选择 **创建** 从操作栏中选择模板 **`Left20-LandscapeHD3Zone`** 从 **创建** 向导。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 使用自定义模板创建渠道后，可以从编辑器将资产添加到渠道。 以下预览显示自定义模板中的图像。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 插入图像作为背景图层  {#inserting-image}

您可以将图像作为背景图层插入到布局中：

您可以调整CSS规则以使用“data-uri”并直接内联图像(`Base64` (encoded)的任意位置，然后在所创建的CSS文件中（步骤13）， *static.css*.

具体操作如下：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您也可以执行以下步骤：

1. 确保以某种方式将该图像包含在渠道的脱机配置中。
1. 使用上述CSS中图像的直接链接，而不是“data-uri”变量。


## 更新背景颜色 {#updating-color}

要更改背景颜色，请将以下代码添加到xml文件中（步骤13）， *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
