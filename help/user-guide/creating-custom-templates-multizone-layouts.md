---
title: 在多区域布局中创建自定义模板
seo-title: Creating Custom Templates in MultiZone Layouts
description: 按照本页了解如何在MultiZone布局中创建自定义模板。
seo-description: Follow this page to learn about creating custom templates in MultiZone layouts.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 1%

---

# 为MultiZone布局创建自定义模板 {#creating-custom-templates-multizone}

本页展示如何为多区域布局创建自定义模板。

## 重要注意事项 {#considerations}

在多区域布局中创建自定义模板之前，必须注意两个重要注意事项：

1. **固定像素大小或百分比**：

   您必须决定是要将固定像素大小用于自定义布局的不同区域，还是要使用百分比创建自定义布局。

   >[!NOTE]
   >使用百分比为您的自定义布局设置区域的好处允许您在各种屏幕大小上重复使用该模板。

1. **命名约定**：

   在了解如何创建要在AEM Screens项目中使用的自定义多区域模板之前，建议了解要创建的模板的措辞。

   | **布局名称** | **描述** |
   |---|---|
   | Left20-LandscapeHD3Zone | 参考3个区域的横向布局，通过此布局，可创建3个区域，其中区域1的横向和垂直屏幕宽度分别从左侧的20%、区域2的横向屏幕宽度以及垂直屏幕宽度的80%和右侧对齐，区域3的横向屏幕宽度分别达到100%和80%，并且纵横比为16:9 |
   | Upper20-PortraitHD2Zone | 指由2个区域组成的纵向模板，从上到下覆盖了20%的屏幕，长宽比为16:9 |
   | Right20-LandscapeSD3Zone | 指由3个区域组成的模板，从右侧覆盖20%的屏幕，长宽比为4:3 |

   >[!IMPORTANT]
   >在自定义布局中定义的区域可能与整个布局的整体纵横比不匹配。 本文档中遵循的命名惯例指定自定义布局整体的长宽比。

## 示例用例Left20-LandscapeHD3Zone布局 {#custom-template-one}

请按照以下部分创建自定义模板 *Left20-LandscapeHD3Zone* 配置：

* **Left20** 指左上角区域占水平与垂直屏幕大小20%的区域。
* **横向** 是指屏幕方向
* **高清** 是指长宽比为16:9
* **3Zone** 是指显示的三个区域

## 多区域布局的可视化表示形式 {#multi-layout-visual-one}

Left20-LandscapeHD3Zone布局允许您在项目中创建以下多区域布局：

![图像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## 创建Left20-LandscapeHD3Zone布局 {#landscape-layout-one}

按照以下步骤为AEM Screens项目创建Left20-LandscapeHD3Zone布局：

1. AEM Screens创建标题为 **customtemplate**.

   ![图像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 导航到 **CRXDE Lite** 通过您的AEM实例>工具> **CRXDE Lite**.

1. 在下创建文件夹 **应用程序** 标题为 **customtemplate**. 同样，创建另一个名为 **模板** 下 **customtemplate**，如下图所示。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >建议您单击 **全部保存** 每次创建、编辑内容或将CRXDE Lite复制到任何节点时，都将从节点中的操作栏中提交，否则将无法提交更新。

1. 从以下位置复制左栏模板 `/libs/screens/core/templates/splitscreenchannel/lbar-left` 到 `/apps/customtemplate/template`.

1. 重命名复制的 **左边栏** (`/apps/customtemplate/template`)到 **my-custom-layout**.
   ![图像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 导航到 `/apps/customtemplate/template/my-custom-layout` 并更新属性 **jcr：description** 到 *Left20-LandscapeHD3Zone模板* 和 **jcr：title** 到 *Left20-LandscapeHD3Zone*.

   ![图像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 导航至 **offline-config** 节点来源 `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` 并更新 **jcr：title** 到 *Left20-LandscapeHD3Zone*.

   ![图像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 导航至 *jcr：content* 属性 **my-custom-template** 从 `/apps/customtemplate/template/my-custom-layout/jcr:content` 并更新 **cq：cssClass** 属性至 **aem-Layout my-custom-layout**.

   ![图像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 请参考步骤(4)，在该步骤中，您复制了lbar左侧模板，随后您将看到3个响应式网格 `my-custom-layout/jcr:content`. 将自定义css类添加到中的每个响应式网格 *cq：cssClass* 属性，例如， *my-custom-layout — 左上方* 对象 *r1c1* 节点。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同样，添加 *my-custom-layout — 右上方* 对象 *r1c2*  和， *my-custom-layout — 底部* 对象 *r2c1* 节点。

   >[!NOTE]
   >这些自定义类将用于在css中设置这些响应式网格的宽度/高度。

   >[!NOTE]
   >您可以根据所需的网格总数添加或删除响应式网格。 在此示例中，我们在第一行显示2个网格，在第二行显示1个网格，因此共有3个响应式网格(r1c1、r1c2、r2c1)。

1. 复制 `/libs/settings/wcm/designs/screens` 到 `/apps/settings/wcm/designs/` 并将复制的设计重命名为 **custom-template-designs**.

1. 导航到 `/apps/settings/wcm/designs/custom-template-designs` 并更新属性 *jcr：title* 之 **custom-template-designs** 到 **customtemplate-design**.

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

1. 导航到 `/apps/<project>/templates/my-custom-layout/jcr:content` 并更新属性 *cq：designPath* 到 `/apps/settings/wcm/designs/customtemplate-designs` 以加载在static.css中配置的样式

   >[!NOTE]
   >建议您键入所有样式，而不是复制或粘贴，因为这样可能会导致空格导致css样式问题。

## 查看结果 {#viewing-result}

请按照以下步骤在您的AEM Screens项目中使用上述自定义模板：

1. 导航到您在步骤(1)中创建的Screens项目，然后选择 **渠道** 文件夹。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 单击 **创建** 从操作栏中选择模板 **Left20-LandscapeHD3Zone** 从 **创建** 向导。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 使用自定义模板创建渠道后，即可从编辑器将资产添加到渠道。 以下预览显示自定义模板中的图像。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 插入图像作为背景图层  {#inserting-image}

您可以将图像作为背景图层插入到布局中：

您可以调整CSS规则以使用称为“data-uri”的内容，并直接将图像（Base64编码）内联到您在中创建的CSS文件中（步骤13）， *static.css*.

具体操作如下：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您也可以执行以下步骤：

1. 确保以某种方式将该图像包含在渠道的脱机配置中
1. 使用上述CSS中图像的直接链接，而不是“data-uri”变量


## 更新背景颜色 {#updating-color}

要更改背景颜色，请将以下代码添加到xml文件中（步骤13）， *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
