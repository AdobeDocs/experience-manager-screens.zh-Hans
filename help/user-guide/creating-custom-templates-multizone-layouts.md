---
title: 在MultiZone布局中创建自定义模板
seo-title: 在MultiZone布局中创建自定义模板
description: 可查看本页以了解如何在MultiZone布局中创建自定义模板。
seo-description: 可查看本页以了解如何在MultiZone布局中创建自定义模板。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 8492bdd071ae029a68ec4a4983c79ce326cac38b
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 1%

---


# 为多区域布局创建自定义模板 {#creating-custom-templates-multizone}

此页将展示如何为多区域布局创建自定义模板。

## 重要注意事项 {#considerations}

在多区域布局中创建自定义模板之前，必须注意以下两个重要注意事项：

1. **固定像素大小或百分比**:

   您必须决定是对自定义布局的不同区域使用固定像素大小，还是要使用百分比创建自定义布局。

   >[!NOTE]
   >使用百分比设置自定义布局的区域的益处允许您在各种屏幕大小上重复使用模板。

1. **命名约定**:

   在了解如何创建要在AEM Screens项目中使用的自定义多区域模板之前，建议您先了解要创建的模板的版本。

   | **布局名称** | **描述** |
   |---|---|
   | Left20-LandscapeHD3Zone | 指3区横向布局，它允许您创建3个区域，区域1为左侧水平和垂直屏幕的20%，区域2为水平屏幕的80%，右侧垂直屏幕的20%，区域3为水平屏幕的100%，长宽比为16:9的垂直屏幕的80% |
   | Upper20-PortraitHD2Zone | 指从顶部覆盖屏幕20%的2区纵向模板，长宽比为16:9 |
   | Right20-LandscapeSD3Zone | 指从右侧覆盖屏幕20%的3区模板，长宽比为4:3 |

   >[!IMPORTANT]
   >自定义布局中定义的区域可能与整个布局的整体长宽比不匹配。 此文档中遵循的命名约定将自定义布局的宽高比指定为整体。

## 示例用例Left20-LandscapeHD3Zone布局 {#custom-template-one}

按照以下部分创建具有以 *下配置的自定义模板* Left20-LandscapeHD3Zone:

* **Left20** 指左侧的顶部区域，覆盖20%的水平和垂直屏幕大小。
* **横向** ：指屏幕方向
* **HD** 将宽高比指16:9
* **3Zone** (3Zone)是显示器的三个区域

## 多区域布局的可视化表示 {#multi-layout-visual-one}

Left20-LandscapeHD3Zone布局允许您在项目中创建以下多区域布局：

![图像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## 创建Left20-LandscapeHD3Zone布局 {#landscape-layout-one}

按照以下步骤为AEM Screens项目创建Left20-LandscapeHD3Zone布局：

1. 创建标题为customtemplate的AEM Screens **项目**。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 导航到 **CRXDE Lite** ，从AEM实例—>工具—> **CRXDE Lite**。

1. 在标题为“customtemplate”的 **应用程** 序下创 **建文件夹**。 同样，在customtemplate下创 **建另一个标** 题为 **template的**&#x200B;文件夹，如下图所示。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >建议您每次创建、 **编辑内容** ，或将内容复制到任何节点时，都在CRXDE Lite中单击操作栏中的“全部保存”，否则将无法提交更新。

1. 将左栏模板从复制到 `/libs/screens/core/templates/splitscreenchannel/lbar-left` 以下 `/apps/customtemplate/template`。

1. 将复制 **的左栏** (`/apps/customtemplate/template`)重命 **名为my-custom-layout**。
   ![图像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 导航 `/apps/customtemplate/template/my-custom-layout` 至并更新Left20- **LandscapeHD3Zone和jcr:** title *至Left20-LandscapeHD3Zone的属性jcr:******* description和Template。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 导航至 **脱机配置节点** , `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` 并将jcr:title更 **新为Left20** - *LandscapeHD3Zone*。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 导航到 *my-custom-template的jcr* :content属性 **，并将cq** :cssClassClass属 `/apps/customtemplate/template/my-custom-layout/jcr:content` 性更新为 **aem-Layout我的自定义布局******。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 参考步骤(4)，在该步骤中，您复制了左侧模板，您将在下面视图3个响应式网格 `my-custom-layout/jcr:content`。 在cq:cssClass属性中将自定义css类 *添加到每个响应式网格* ，例如， *my-custom-layout—r1c1节点的**左上角* 。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同样， *为r1c2添加my-custom-layout* ( *右上)和* my-custom-layout( *r2c1节点)* 添加bottom *(* bottom)。

   >[!NOTE]
   >这些自定义类将用在css中以设置这些响应式网格的宽度／高度。

   >[!NOTE]
   >您可以根据所需的网格总数添加或删除响应式网格。 在此示例中，我们展示第一行中的2个网格和第二行中的1个网格，因此总共有3个响应式网格(r1c1、r1c2、r2c1)。

1. 复制 `/libs/settings/wcm/designs/screens` 到复 `/apps/settings/wcm/designs/` 制的设计并将其重命名 **为custom-template-designs**。

1. 导航 `/apps/settings/wcm/designs/custom-template-designs` 到custom-template-designs的 *属性jcr* :title **** 并将其更新为customtemplate-design ****。

1. 导航到 `/apps/settings/wcm/designs/custom-template-designs` 并创建一个static.css文件。

1. 将内容复制到static.css文件：

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

1. 导航到 `/apps/<project>/templates/my-custom-layout/jcr:content` 并更新属 *性cq:designPath* ，以 `/apps/settings/wcm/designs/customtemplate-designs` 加载static.css中配置的样式

   >[!NOTE]
   >建议您键入所有样式，而不是复制或粘贴，这会导致空格导致css样式问题。

## 查看结果 {#viewing-result}

请按照以下步骤在您的AEM Screens项目中使用上述自定义模板：

1. 导航到您在步骤(1)中创建的Screens项目，然后选择 **渠道** 文件夹。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 单 **击操作** 栏中的“创建”，然后从“创 **建”向导中选择模板Left20-LandscapeHD** 3 **Zone** 。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 使用自定义模板创建渠道后，您可以从编辑器将资产添加到渠道。 以下预览显示自定义模板中的图像。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 将图像插入为背景层  {#inserting-image}

您可以将图像作为背景图层插入布局：

您可以调整CSS规则，以使用称为“data-uri”的内容，并直接在CSS文件(在（第13步）static.css中创建)中嵌入图 *像（Base64编码）*。

具体操作如下：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您可以按照以下步骤操作：

1. 确保图像以某种方式包含在渠道的脱机配置中
1. 使用指向上述CSS中图像的直接链接，而不是“data-uri”变体


## 更新背景颜色 {#updating-color}

要更改背景颜色，请向xml文件（第13步） *static.css添加以下代码*。

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



