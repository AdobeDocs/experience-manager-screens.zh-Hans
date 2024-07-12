---
title: 在多区域布局中创建自定义模板
description: 了解如何在MultiZone布局中为AEM Screens创建自定义模板。
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '862'
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

   它有助于了解如何创建要在AEM Screens项目中使用的自定义多区域模板。 但首先，您必须了解要创建的模板的措辞。

   | **布局名称** | **描述** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | 三区域横向布局允许您创建三个区域： <br>*区域1为水平屏幕和垂直屏幕的20%<br>*区域2为水平屏幕的80%，垂直屏幕的20%向右对齐<br>*区域3为水平屏幕的100%和垂直屏幕的80%。 长宽比为16:9 |
   | `Upper20-PortraitHD2Zone` | 双区域纵向模板，从顶部覆盖20%的屏幕，长宽比为16:9 |
   | `Right20-LandscapeSD3Zone` | 一个三区模板，从右侧覆盖20%的屏幕，长宽比为4:3 |

   >[!IMPORTANT]
   >在自定义布局中定义的区域可能与整个布局的整体纵横比不匹配。 本文档中遵循的命名惯例指定自定义布局整体的长宽比。

## 示例用例`Left20-LandscapeHD3Zone`布局 {#custom-template-one}

按照以下部分创建具有以下配置的自定义模板&#x200B;*`Left20-LandscapeHD3Zone`*：

* **`Left20`** — 左侧的顶部区域占水平屏幕和垂直屏幕大小的20%。
* **`Landscape`** — 屏幕方向。
* **`HD`** — 长宽比为16:9。
* **`3Zone`** — 显示的三个区域。

## 多区域布局的可视化表示形式 {#multi-layout-visual-one}

`Left20-LandscapeHD3Zone`布局允许您在项目中创建以下多区域布局：

![图像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## 创建`Left20-LandscapeHD3Zone`布局 {#landscape-layout-one}

请按照以下步骤为AEM Screens项目创建`Left20-LandscapeHD3Zone`布局。

1. 创建标题为&#x200B;**`customtemplate`**&#x200B;的AEM Screens项目。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 从您的AEMCRXDE Lite> “工具”>“**CRXDE Lite”**&#x200B;导航到&#x200B;**工具**。

1. 在&#x200B;**apps**&#x200B;下创建标题为&#x200B;**`customtemplate`**&#x200B;的文件夹。 同样，在&#x200B;**`customtemplate`**&#x200B;下创建另一个名为&#x200B;**template**&#x200B;的文件夹，如下图所示。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >每次创建、编辑内容或将CRXDE Lite复制到任何节点时，在Node的操作栏中单击&#x200B;**全部保存**。 否则，您无法提交更新。

1. 将lbar-left模板从`/libs/screens/core/templates/splitscreenchannel/lbar-left`复制到`/apps/customtemplate/template`。

1. 将复制的&#x200B;**lbar-left** (`/apps/customtemplate/template`)重命名为&#x200B;**my-custom-layout**。
   ![图像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 导航到`/apps/customtemplate/template/my-custom-layout`并将属性&#x200B;**`jcr:description`**&#x200B;更新为&#x200B;`Left20-LandscapeHD3Zone`*的*&#x200B;模板，将&#x200B;**`jcr:title`**&#x200B;更新为&#x200B;*`Left20-LandscapeHD3Zone`*。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 从`/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config`导航到&#x200B;**`offline-config`**&#x200B;节点并将&#x200B;**`jcr:title`**&#x200B;更新为&#x200B;*`Left20-LandscapeHD3Zone`*。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 从`/apps/customtemplate/template/my-custom-layout/jcr:content`导航到&#x200B;**my-custom-template**&#x200B;的&#x200B;*`jcr:content`*&#x200B;属性并更新&#x200B;**`cq:cssClass`**&#x200B;属性，以便您可以使用&#x200B;**aem-Layout my-custom-layout**。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 参照复制左侧lbar模板的步骤(4)，您可以在`my-custom-layout/jcr:content`下查看三个响应式网格。 向&#x200B;*`cq:cssClass`*&#x200B;属性中的每个响应式网格添加自定义css类，例如&#x200B;*r1c1*&#x200B;节点的&#x200B;*my-custom-layout-top-left*。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同样，为&#x200B;*r1c2*&#x200B;添加&#x200B;*my-custom-layout-top-right*，为&#x200B;*r2c1*&#x200B;节点添加&#x200B;*my-custom-layout-bottom*。

   >[!NOTE]
   >这些自定义类在css中用于设置这些响应式网格的宽度/高度。

   >[!NOTE]
   >您可以根据所需的网格总数添加或删除响应式网格。 在此示例中，第一行中的两个网格和第二行中的一个网格被显示，因此总共有三个响应式网格(r1c1、r1c2、r2c1)。

1. 将`/libs/settings/wcm/designs/screens`复制到`/apps/settings/wcm/designs/`并将复制的设计重命名为&#x200B;**custom-template-designs**。

1. 导航到`/apps/settings/wcm/designs/custom-template-designs`并将&#x200B;**custom-template-designs**&#x200B;的属性&#x200B;*`jcr:title`*&#x200B;更新为&#x200B;**customtemplate-design**。

1. 导航到`/apps/settings/wcm/designs/custom-template-designs`并创建文件static.css。

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

1. 导航到`/apps/<project>/templates/my-custom-layout/jcr:content`并将属性&#x200B;*`cq:designPath`*&#x200B;更新为`/apps/settings/wcm/designs/customtemplate-designs`，以便加载在static.css中配置的样式。

   >[!NOTE]
   >键入所有样式而不是复制或粘贴，这可能会导致空格导致css样式问题。

## 查看结果 {#viewing-result}

请按照以下步骤在您的AEM Screens项目中使用上述自定义模板：

1. 导航到您在步骤(1)中创建的Screens项目，然后单击&#x200B;**渠道**&#x200B;文件夹。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 单击操作栏中的&#x200B;**创建**，然后单击&#x200B;**创建**&#x200B;向导中的模板&#x200B;**`Left20-LandscapeHD3Zone`**。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 使用自定义模板创建渠道后，可以从编辑器将资产添加到渠道。 以下预览显示自定义模板中的图像。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 插入图像作为背景图层 {#inserting-image}

您可以将图像作为背景图层插入到布局中：

您可以调整CSS规则以使用“data-uri”，并在您在第13步&#x200B;*static.css*&#x200B;中创建的CSS文件中直接内联图像（`Base64`编码）。

此安排如下：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您也可以执行以下步骤：

1. 确保以某种方式将该图像包含在渠道的脱机配置中。
1. 使用上述CSS中图像的直接链接，而不是“data-uri”变量。


## 更新背景颜色 {#updating-color}

若要更改背景颜色，请将以下代码添加到xml文件（步骤13） *static.css*。

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
