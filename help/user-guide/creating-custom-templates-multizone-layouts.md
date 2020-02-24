---
title: 在MultiZone布局中创建自定义模板
seo-title: 在MultiZone布局中创建自定义模板
description: 可查看本页以了解如何在MultiZone布局中创建自定义模板。
seo-description: 可查看本页以了解如何在MultiZone布局中创建自定义模板。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6a0967580d06e749db878d74aad2ffb1fec82f43

---


# 在MultiZone布局中创建自定义模板 {#creating-custom-templates-multizone}

此页面显示如何在多区域布局中创建自定义模板。

## 命名规范 {#name-terms}

在了解如何创建要在AEM Screens项目中使用的自定义多区域模板之前，建议您先了解要创建的模板的版本。

| **布局名称** | **描述** |
|---|---|
| Left20-LandscapeHD3Zone | 指3区横向布局，它允许您创建3个区域，其中区域1从左侧占水平和垂直屏幕的20%，区域2从水平屏幕的80%对齐，区域3从右侧垂直屏幕的20%对齐，区域3从水平屏幕的100%对齐，垂直屏幕的80%纵横比为16:9 |
| Upper20-PortraitHD2Zone | 指从顶部覆盖屏幕20%的2区纵向模板，长宽比为16:9 |
| Right20-LandscapeSD3Zone | 指从右侧覆盖屏幕20%的3区模板，长宽比为4:3 |

## 示例用例 {#example-use-cases}

## Left20-LandscapeHD3Zone布局 {#custom-template-one}

按照以下部分创建具有以下配置的 *自定义模板Left20-LandscapeHD3Zone* :

* **Left20** 指左侧的顶部区域，覆盖20%的水平和垂直屏幕大小。
* **横向** ：指屏幕方向
* **HD** 将宽高比称为16:9
* **3Zone** 是指显示器的三个区域

## 多区域布局的可视化表示 {#multi-layout-visual-one}

Left20-LandscapeHD3Zone布局允许您在项目中创建以下多区域布局：

![图像](/help/user-guide/assets/custom-multizone/custom-multizone1.png)

## 创建Left20-LandscapeHD3Zone布局 {#landscape-layout-one}

请按照以下步骤为AEM Screens项目创建Left20-LandscapeHD3Zone布局：

1. 创建标题为自定义模板的AEM Screens **项目**。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 从您的 **AEM实例** —>工具—> **CRXDE Lite**。

1. 在标题为“自定义模 **板** ”的应用程序下 **创建文件夹**。 同样，在customtemplate下创建另一个标 **题为** “ **template**”的文件夹，如下图所示。

   ![图像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   > [!NOTE]
   > 建议您每次创建、编辑内容或将内容复制到任何节点时，都单击CRXDE Lite中操作栏中的“保存全部 **** ”，否则将无法提交更新。

1. 将左栏模板从复制到 `/libs/screens/core/templates/splitscreenchannel/lbar-left` 中 `/apps/customtemplate/template`。

1. 将复制 **的lbar-left** (`/apps/customtemplate/template`)重命名 **为my-custom-layout**。

1. 导航到 `/apps/customtemplate/template/my-custom-layout` 属性 **jcr:** Left20-LandscapeHD3Zone的“模板”和 *jtitle*******:titleToLeft20-LandscapeHD3Zone的“模板”。

1. 导航到 **offline-config** node `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` from，并将 **jcr:title** 更新为 *Left20-LandscapeHD3Zone*。

1. 导航到 *my-custom-template* 的jcr:content **属性，并将** cq:css Class `/apps/customtemplate/template/my-custom-layout/jcr:content`******** Class属性更新为Aem-My-custom-layout的Custom-layout属性。

1. 在步骤(4)中，您复制了左栏模板，您将在下面查看3个响应式网格 `my-custom-layout/jcr:content`。 在 *cq:cssClass* 属性中为每个响应式网格添加自定义css类，例如， *my-custom-layout—top-left*, *my-custom-class—top-right*, ** my-custom-layout—bottomJayout。

   >[!NOTE]
   >这些自定义类将用在css中，以设置这些响应式网格的宽度／高度。

   >[!NOTE]
   > 您可以根据所需的网格总数添加或删除响应式网格。 在此示例中，我们展示第一行中的2个网格和第二行中的1个网格，因此总共有3个响应式网格(r1c1、r1c2、r2c1)。

1. 复制 `/libs/settings/wcm/designs/screens` 到 `/apps/settings/wcm/designs/` 自定义模 **板设计并重命名**

1. 导航到 `/apps/settings/wcm/designs/custom-template-designs` custom-template-designs的属 *性jcr:title* ，并将 **其更新为customtemplate-design****的属性**。

1. 更新内 `/apps/settings/wcm/designs/<project>-designs/static.css` 容以匹配以下内容

## 使用特定配置创建自定义模板 {#basic-flow-setting}

![图像](assets/custom-template1.png)

请按照以下步骤创建自定义模板。

1. 在 `/apps/<project>/templates/my-custom-layout`

   ```shell
    <?xml version="1.0" encoding="UTF-8"?>
    <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
    jcr:description="My Custom 3-zones layout "
    jcr:primaryType="cq:Template"
    jcr:title="3-zones layout"
    allowedParents="[/libs/screens/core/templates/channelfolder]"
    allowedPaths="[/content/screens(/.*)?]"
    ranking="{Long}20000">
    <jcr:content
        cq:cssClass="aem-Layout aem-Layout--3x1 my-CustomLayout"
        cq:designPath="/apps/settings/wcm/designs/<project>"
        cq:deviceGroups="[mobile/groups/responsive]"
        jcr:primaryType="cq:PageContent"
        sling:resourceSuperType="screens/core/components/channel"
        sling:resourceType="screens/core/components/multiscreenchannel">
        <r1c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-top"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r2c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-middle"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r3c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-bottom"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <cq:responsive jcr:primaryType="nt:unstructured">
            <breakpoints jcr:primaryType="nt:unstructured"/>
        </cq:responsive>
        <offline-config/>
    </jcr:content>
   </jcr:root>
   ```

1. 在中创建页面设计 `/apps/settings/wcm/designs/<project>`。

   >[!NOTE]
   >
   >确保上面 `cq:designPath` 的路径匹配。

1. 更新 **设计的offline-config** 节点，以同时指向新路径

1. 在文 **件夹中添加static.css**`/apps/settings/wcm/designs/<project>` 文件并将其内容设置为

   ```shell
   .cq-Screens-channel--multizone.my-CustomLayout {}
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-top { height: 150px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-middle { height: 1470px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-bottom { height: 300px; }
   ```

## 将图像作为背景图层插入 {#inserting-image}

您可以将图像作为背景图层插入布局：

您可以调整CSS规则，以使用“data-uri”，并直接在CSS文件中嵌入图像（Base64编码）。

具体操作如下：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您可以按照以下步骤操作：

1. 确保以某种方式将图像包含在渠道的脱机配置中
1. 使用指向上述CSS中图像的直接链接，而不是“data-uri”变体


## 更新背景颜色 {#updating-color}

要更改背景颜色，请向xml文件添加以下代码：

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



