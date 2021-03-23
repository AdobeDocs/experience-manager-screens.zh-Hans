---
title: 在多区域布局中创建自定义模板
seo-title: 在多区域布局中创建自定义模板
description: 可查看本页以了解如何在MultiZone布局中创建自定义模板。
seo-description: 可查看本页以了解如何在MultiZone布局中创建自定义模板。
contentOwner: Jyotika Syal
feature: 开发屏幕
role: 开发人员
level: 中间
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 1%

---


# 为多区域布局创建自定义模板{#creating-custom-templates-multizone}

此页面展示如何为多区域布局创建自定义模板。

## 重要注意事项{#considerations}

在多区域布局中创建自定义模板之前，必须注意以下两个重要注意事项：

1. **固定像素大小或百分比**:

   您必须决定是对自定义布局的不同区域使用固定像素大小，还是要使用百分比创建自定义布局。

   >[!NOTE]
   >使用百分比设置自定义布局的区域的好处是可以在各种屏幕大小上重复使用模板。

1. **命名约定**:

   在您了解如何创建要在AEM Screens项目中使用的自定义多区域模板之前，建议您了解要创建的模板的版本。

   | **布局名称** | **描述** |
   |---|---|
   | Left20-LandscapeHD3Zone | 指3区横向布局，它允许您创建3个区域，区域1为左侧水平和垂直屏幕的20%，区域2为水平屏幕的80%，右侧垂直屏幕的20%，区域3为水平屏幕的100%，长宽比为16:9的垂直屏幕的80% |
   | Upper20-PortraitHD2Zone | 指从顶部覆盖屏幕20%的2区纵向模板，长宽比为16:9 |
   | Right20-LandscapeSD3Zone | 指从右侧覆盖屏幕20%的3区模板，长宽比为4:3 |

   >[!IMPORTANT]
   >自定义布局中定义的区域可能与整个布局的整体长宽比不匹配。 此文档中遵循的命名约定将自定义布局的宽高比指定为整体。

## 示例用例Left20-LandscapeHD3Zone布局{#custom-template-one}

请按照以下部分创建具有以下配置的自定义模板&#x200B;*Left20-LandscapeHD3Zone*:

* **Left20** 指左侧的顶部区域，覆盖20%的水平和垂直屏幕大小。
* **** 横向是指屏幕方向
* **HD** 将宽高比称为16:9
* **3** Zone是显示器的三个区域

## 多区域布局的可视表示{#multi-layout-visual-one}

Left20-LandscapeHD3Zone布局允许您在项目中创建以下多区域布局：

![图像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## 创建Left20-LandscapeHD3Zone布局{#landscape-layout-one}

请按照以下步骤为AEM Screens项目创建Left20-LandscapeHD3Zone布局：

1. 创建标题为&#x200B;**customtemplate**&#x200B;的AEM Screens项目。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 从AEM实例 — >工具 — > **CRXDE Lite**&#x200B;导航到&#x200B;**CRXDE Lite**。

1. 在&#x200B;**apps**&#x200B;下创建一个名为&#x200B;**customtemplate**&#x200B;的文件夹。 同样，在&#x200B;**customtemplate**&#x200B;下创建另一个标题为&#x200B;**template**&#x200B;的文件夹，如下图所示。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >建议您每次创建、编辑内容或将内容复制到任何节点时，都单击CRXDE Lite中操作栏中的&#x200B;**保存所有**，否则将无法提交更新。

1. 将左栏模板从`/libs/screens/core/templates/splitscreenchannel/lbar-left`复制到`/apps/customtemplate/template`。

1. 将复制的&#x200B;**lbar-left**(`/apps/customtemplate/template`)重命名为&#x200B;**my-custom-layout**。
   ![图像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 导航到`/apps/customtemplate/template/my-custom-layout`并将属性&#x200B;**jcr:description**&#x200B;更新为&#x200B;*Template for Left20-LandscapeHD3Zone*&#x200B;和&#x200B;**jcr:title**&#x200B;更新为&#x200B;*Left20-LandscapeHD3Zone*。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 导航到`/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config`的&#x200B;**offline-config**&#x200B;节点，将&#x200B;**jcr:title**&#x200B;更新为&#x200B;*Left20-LandscapeHD3Zone*。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 导航到`/apps/customtemplate/template/my-custom-layout/jcr:content`中&#x200B;**my-custom-template**&#x200B;的&#x200B;*jcr:content*&#x200B;属性，并将&#x200B;**cq:cssClass**&#x200B;属性更新为&#x200B;**aem-Layout my-custom-layout**。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 参照步骤(4)，在该步骤中，您复制了左侧模板，您将在`my-custom-layout/jcr:content`下视图3个响应式网格。 在&#x200B;*cq:cssClass*&#x200B;属性中，将自定义css类添加到每个响应式网格，例如，*my-custom-layout—top-left* for *r1c1*&#x200B;节点。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同样，为&#x200B;*my-custom-layout—top-right*（对于&#x200B;*r1c2*）和&#x200B;*my-custom-layout—bottom*（对于&#x200B;*r2c1*）节点)添加。

   >[!NOTE]
   >这些自定义类将用在css中，以设置这些响应式网格的宽度/高度。

   >[!NOTE]
   >您可以根据所需的总网格数添加或删除响应式网格。 在此示例中，我们展示第一行中的2个网格和第二行中的1个网格，因此总共有3个响应式网格(r1c1、r1c2、r2c1)。

1. 将`/libs/settings/wcm/designs/screens`复制到`/apps/settings/wcm/designs/`，并将复制的设计重命名为&#x200B;**custom-template-designs**。

1. 导航到`/apps/settings/wcm/designs/custom-template-designs`并将&#x200B;**custom-template-designs**&#x200B;的属性&#x200B;*jcr:title*&#x200B;更新为&#x200B;**customtemplate-design**。

1. 导航到`/apps/settings/wcm/designs/custom-template-designs`并创建一个static.css文件。

1. 将内容复制到`static.css`文件：

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

1. 导航到`/apps/<project>/templates/my-custom-layout/jcr:content`并将属性&#x200B;*cq:designPath*&#x200B;更新到`/apps/settings/wcm/designs/customtemplate-designs`以加载static.css中配置的样式

   >[!NOTE]
   >建议您键入所有样式，而不是复制或粘贴，这会导致出现空格，从而导致css样式问题。

## 查看结果{#viewing-result}

请按照以下步骤在您的AEM Screens项目中使用上述自定义模板：

1. 导航到您在步骤(1)中创建的Screens项目，然后选择&#x200B;**渠道**&#x200B;文件夹。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 单击操作栏中的&#x200B;**创建**，然后从&#x200B;**创建**&#x200B;向导中选择模板&#x200B;**Left20-LandscapeHD3Zone**。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 使用自定义模板创建渠道后，您可以从编辑器将资产添加到渠道。 以下预览显示自定义模板中的图像。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 插入图像作为背景图层{#inserting-image}

可以将图像作为背景图层插入布局：

您可以调整CSS规则以使用称为“data-uri”的内容，并直接在CSS文件（步骤13）*static.css*&#x200B;中创建的Base64编码)中嵌入图像。

具体操作如下：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您可以按照以下步骤操作：

1. 确保图像以某种方式包含在渠道的脱机配置中
1. 使用指向上述CSS中图像的直接链接，而不是“data-uri”变体


## 更新背景颜色{#updating-color}

要更改背景颜色，请向xml文件（步骤13）*static.css*&#x200B;添加以下代码。

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



